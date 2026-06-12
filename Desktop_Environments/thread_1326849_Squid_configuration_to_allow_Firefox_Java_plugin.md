---
title: "Squid configuration to allow Firefox Java plugin"
date: 2009-11-14
forum: Desktop Environments
---

### Post by cengelbrecht on 2009-11-14
I am running Karmic with Squid installed, which I use as a proxy. 

If I enable the Squid proxy (on 10.1.1.4, which is the same as my machine IP), then Firefox works perfectly, I can access any web page, so everything is good. So Squid is running on the same machine as Firefox, just in case that was unclear.

What doesn't work, however, are Java applets. The firefox-bin process does spawn the jvm process, which makes a socket in /tmp, but firefox never gets any data from the jvm process and it times out.

If I disable the use of a proxy in Firefox, then Java applets work perfectly.

What do I need to configure in Squid (or maybe in Firefox) to make this work?

Your help will be appreciated.

---

### Post by cengelbrecht on 2009-11-18
Update:

Excluding 10.1.1.4 (my desktop's IP) from proxy requests in Firefox doesn't help. Java applets still don't work.

Switching to a Squid proxy on another machine in my LAN results in Java applets working.

There are messages in ~/.xession-errors like:
Exception in thread "main" netscape.javascript.JSException: Plugin instance for applet ID 2 was already released
    at sun.plugin2.main.server.LiveConnectSupport.getInfo(LiveConnectSupport.java:380)
    at sun.plugin2.main.server.LiveConnectSupport.shutdown(LiveConnectSupport.java:41)
    at sun.plugin2.main.server.JVMInstance.unregisterApplet(JVMInstance.java:1296)
    at sun.plugin2.main.server.JVMInstance.recycleAppletID(JVMInstance.java:381)
    at sun.plugin2.main.server.JVMManager.recycleAppletID(JVMManager.java:316)
    at sun.plugin2.main.server.MozillaPlugin.stopApplet(MozillaPlugin.java:312)
    at sun.plugin2.main.server.MozillaPlugin.destroy(MozillaPlugin.java:225)


Why does communication between Firefox and the JVM fail when Firefox is configured to use a proxy on the local machine? Why does this named pipe even go through the proxy at all?

My Squid is a standard install, with all of the files exactly as they are made by installing using apt-get. One line in /etc/squid/squid.conf was changed, and that is the one to allow http_access acl localnet

---

### Post by cengelbrecht on 2009-11-18
SOLVED:

Accessing the proxy as 127.0.0.1 results in Java applets working perfectly.

You can bind Squid to *.*.*.* or to specific interfaces, making it available for use by the rest of the LAN, but you have to access it locally on 127.0.0.1

Everything I wrote in this whole thread also goes for Privoxy.

I used Squid 2.7.STABLE6-2ubuntu2 and Privoxy 3.0.13-1 Ubuntu packages for all tests and results mentioned here.

PS: I must say I'm disappointed in this forum because no-one even tried to help me.

---

