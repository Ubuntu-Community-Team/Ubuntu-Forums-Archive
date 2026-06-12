---
title: "why do I have an unknown tcp connection to Canonical?"
date: 2014-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Andres Gonzalez on 2014-03-17
I have a XPS Developers Edition that I purchased over a year ago. I was having some network issues so I used netstat to see what was going on. Turns out that I have a tcp connection to 91.189.89.144 which apparently is to Canonical. The only thing running at the time was a terminal.

So, what is connecting to Canonical that I did not initiate?

I have already put the following in my /etc/hosts file to prevent an automatic connection to some kind of Amazon search stuff:

127.0.0.1 productsearch.ubuntu.com

What else do I have to do to get my privacy back from Canonical?

-Andres

---

### Post by tgalati4 on 2014-03-17
Are you running any Landscape monitoring services?

tgalati4@Mint14-Extensa ~ $ apt-cache search landscape
landscape-client - The Landscape administration system client
landscape-client-ui - The Landscape administration system client - UI configuration
landscape-client-ui-install - The Landscape administration system client - UI installer
landscape-common - The Landscape administration system client - Common files

Also, error reporting (*apport*) may open connections.  Do you have it installed?

tgalati4@Mint14-Extensa ~ $ apt-cache policy apport
apport:
  Installed: (none)
  Candidate: 2.6.1-0ubuntu13
  Version table:
     2.6.1-0ubuntu13 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
     2.6.1-0ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

---

### Post by ian-weisser on 2014-03-18
It could be your NTP client syncing time from ntp.pool.ubuntu.com
It could be your Geolocation client testing your IP at geoip.ubuntu.com
It could be your apt doing it's daily package database update
It could be whoopsie sending an error report to daisy.ubuntu.com
It could be any of several other services.

Canonical runs a lot of free *services* to make your Ubuntu system more convenient to use, and a couple services to improve future Ubuntu releases.
They are not secret, the data collection policies (on the few services where *any* data is retained) is public, and you can change or turn them off at any time (it's *your* system).

For example, you can see the results whoopsie/daisy services at [http://errors.ubuntu.com](http://errors.ubuntu.com)

Set your own NTP servers, and figure out your own location, and upload your own crash reports to Launchpad if you're worried about it. Or put a tinfoil hat on your router.

---

