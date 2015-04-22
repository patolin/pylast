The project has moved to: https://github.com/pylast/pylast

# pyLast #

## Features ##

  * Simple public interface.
  * Access to all the data exposed by the Last.fm webservices.
  * Scrobbling support.
  * Full object-oriented design.
  * Proxy support.
  * Internal caching support for some webservices calls (disabled by default).
  * No extra dependencies but python itself.
  * Support for other API-compatible networks like Libre.fm
  * Python3-friendly (Starting from 0.5).
  * _...errr, what else?!_

&lt;wiki:gadget url="http://www.ohloh.net/p/22752/widgets/project\_users\_logo.xml" height="43"  border="0" /&gt;

# Getting Started #
Here's a very simple code example to get you started.
In order to create any object from pylast, you need a Network object which represents a social music network that is Last.fm or any other API-compatible one. You can obtain a preconfigured one for Last.fm and use it as follows:

```
import pylast

# You have to have your own unique two values for API_KEY and API_SECRET
# Obtain yours from http://www.last.fm/api/account for Last.fm
API_KEY = "b25b959554ed76058ac220b7b2e0a026" # this is a sample key
API_SECRET = "425b55975eed76058ac220b7b4e8a054"

# In order to perform a write operation you need to authenticate yourself
username = "your_user_name"
password_hash = pylast.md5("your_password")

network = pylast.LastFMNetwork(api_key = API_KEY, api_secret = 
    API_SECRET, username = username, password_hash = password_hash)

# now you can use that object every where
artist = network.get_artist("System of a Down")
artist.shout("<3")


track = network.get_track("Iron Maiden", "The Nomad")
track.love()
track.add_tags(("awesome", "favorite"))

# type help(pylast.LastFMNetwork) or help(pylast) in a python interpreter to get more help
# about anything and see examples of how it works
```

_Please do not email me asking for code examples or about issues, the above code is a perfectly good starter example, and there's an issue tracker up top._

# News #

## Scrobbling 2.0 ##
The new [Scrobbling 2.0](http://www.last.fm/api/scrobbling#scrobbling-2-0-documentation) protocol is now implemented directly in the pylast.Network class through the methods scrobble(...), scrobble\_many(...), and update\_now\_playing(...). The older <=1.2.1 spec for scrobbling is now deprecated.

## Now plays nice with Python 3 ##
I can now (hopefully) declare pylast to be both compatible with Python>=2.7 and Python>=3.1 in the same module. Please report any regressions to the issues section.

## A more permissive license ##
Due to popular demand, pylast is now available in the more permissive Apache 2.0 license starting from version 0.4.30; So help yourself to some non-copyleft code from the trunk or from PyPi. Happy coding.

## 0.4 ##
Hey guys, I've just commited 0.4 to svn and pypi a few moments ago.
I've been working on it for the last couple of days and I think it's
in good shape now.
What's totally new in 0.4 is total abstraction of the network you're
dealing with, so that pylast can be used with other API compatible
websites like Libre.fm and I don't have to maintain two separate
libraries like I previously intended to...
([see the whole message](http://groups.google.com/group/pylast/browse_thread/thread/c3a5188274adf448))

## Scrobble this! ##
Just for fun, I added scrobbling support to pylast this afternoon. It's pretty simple. Everything is contained in the class pylast.Scrobbler.
Python is just that much fun ;)

## Now with a lot more zen ##
0.3 is in the trunk now. After three days of constant work, I think it's done.
I've strived in this release to adhere to the python style guides to introduce more zen into pylast, so as you see, I had to break most of the API (sorry). But I'm sure that porting code to 0.3 won't be much of a hassle since that it's mostly semantics.

New features in this release as well are the ability to cache request as easily as calling pylast.enable\_caching(), and proxy support that is also just as easy.

Other than all that, most of the module has been rewritten, or has been given a really tight facelift. Plus, I've taken more time to work on better docstrings complete with examples and usage remarks.

You can check out the latest revision from the trunk now, test it out and report problems if any to the issue tracker.

_**svn checkout http://pylast.googlecode.com/svn/trunk/ pylast**_

P.S. We have a [pylast](http://identi.ca/group/pylast) group on [identi.ca](http://identi.ca) now. yaay.