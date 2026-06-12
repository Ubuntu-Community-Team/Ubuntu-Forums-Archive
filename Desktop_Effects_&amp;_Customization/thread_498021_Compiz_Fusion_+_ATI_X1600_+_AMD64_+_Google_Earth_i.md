---
title: "Compiz Fusion + ATI X1600 + AMD64 + Google Earth issue"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by firmwire on 2007-07-10
Decided to post this in more than one forum section to maximize possibilities of response:

I have been all over the forums and have found some very good info for possibly solving my issue. I am not sure if it will work or not since I am not at home at the moment. I wanted to run some things by you all to make it easier when I do get home.

Issue: 
Running Compiz Fusion ( perfectly) in xgl w/ gnome. I have fglrx as the driver I am using. I have Composite set to "0" and have even changed it to "false".
When I run glxinfo I get direct rendering is NO. 
glxgears works fine in any session I do.
From what I can find, in order for compiz fusion to run it has to be in xgl mode. But google earth NEEDS direct rendering ( I think).
I think if I just go into a non xgl session the same glxinfo gives me YES for direct rendering. I don't remember though at the moment.
Even so...when I run google earth in any session I get 100% CPU usage from it. It just hangs at the initialization splash screen. I can still kill the process, so it doesn't lock my system up completely. 
I have read that people have been able to get it to work with Beryl and ATI cards running together. I am just trying to figure out how to get it to run with my setup.

In case the question comes up, I have installed it two different ways. I had installed it through Automatix. Then uninstalled it. Then I installed it from the download from the google earth linux download site. Both installs went fine. Both hang and produce 100% cpu usage when activated and hangs on the splash screen.

I found this post [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636). Do you think this will solve my problem?

Also I have seen posts about libGL.so.1.bz2 and libGL.so.1.tar.bz2, and I do you think this may fix my issue?

Oh yeah... and I even tried this earlier today: DISPLAY=:0 /usr/local/google-earth/googleearth. It just loads the splash screen and hangs.

I know people have had the issue with 100% cpu usage, but I couldn't find anything saying what they did to fix it or if they were even able to.
I have seen in one place that one person actually installed an extra stick of RAM and that helped. But I don't think I should have to. Everything else works great. I only have 1GB on this system currently.

I am running Feisty 64 and it runs completely stable. I love it!

Any suggestions/solutions are greatly appreciated. Thanks in advance.

---

### Post by firmwire on 2007-07-11
/bump

---

### Post by DarwinsTheory on 2008-06-23
I'm using a nvidia card and it still effects me...

Using the FusionIcon and just switching off Compiz is the work around.. pitty...

Matt

---

