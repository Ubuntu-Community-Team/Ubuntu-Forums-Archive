---
title: "B3 Server Plugin Uninstall Script"
date: 2011-03-09
forum: Gaming &amp; Leisure
---

### Post by Twitch04 on 2011-03-09
Hey guys, it's been awhile--

My friends and I run an Urban Terror server through an Ubuntu 10.10 Server Edition Virtual Machine. We have B3 (for those who don't know, Big Brother Bot, it's an administration bot with commands and such) and a few plugins installed for it.

When we download and extract the plugin, there are 3 things we have to do. Let's say the plugin is called... Plugin. 

There's a Plugin.py file we have to put in ~b3/b3/extplugins

There's a Plugin.xml file we have to put in ~b3/b3/extplugins/conf

And there's a line of code, similar for all plugins, that has to be put into a b3 configuration file, but I'm not going to worry about that for this. 

I was thinking it wouldn't be too hard to write a script that would look something like:

./uninstall.sh Plugin

That would check in ~b3/b3/extplugins for Plugin.py and in ~b3/b3/extplugins/conf for Plugin.xml and do something to the effect of change the extention for the files to something like .bak or .backup, so that the files are still there, unchanged, but for all B3 knows they are gone and uninstalled. 

Also, conversely, to make a script to check the same folders for Plugin.bak and change it back to Plugin.py and Plugin.xml.

Assuming that doing those two things would successfully uninstall the plugin, that'd be sweet, instead of having to manually do both of those things.

So does that sound like a feasible idea? And how would it generally be set up? I don't know how it'd work with taking that first argument "./uninstall.sh **Plugin**" and making it search for **Plugin**.py and **Plugin**.xml.

Thanks for any help, and I'll gladly answer any questions if I didn't give enough info!

---

