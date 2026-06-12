---
title: "Different themes for gtk apps depending on how started"
date: 2005-08-18
forum: Desktop Environments
---

### Post by Watter on 2005-08-18
I have installed a few of the the gtk2-engine-whatever gtk themes so that my GTK apps look decent enough to use. I set the gth theme I want to use with "Control-Center > Appearance & Themes > GTK Styles and Fonts". This all works perfectly as long as I start the gtk apps from a console window. When I start the same gtk apps from the KDE menu, they come up with the ugly and nearly unusable default blocky GTK look and feel. 

This isn't a killer problem as I can just start my gtk apps from console, but it is a little annoying. Any ideas?

---

### Post by Watter on 2005-08-18
Ha! Not 30 seconds after posting this I think I figured out what the issue might be. It turns out that only those GTK apps that have to be run with sudo (i.e. synaptic and a few others) have this problem. I am guessing that the GTK Theme preferences are user specific so when I'm running it with sudo, KDE is using the root user's preferences (which haven't been set). 

This still doesn't explain why starting the same application from the console with something like "sudo synaptic" doesn't cause the same issue. The correct theme comes up when I do it that way. 

Should I create a password for the root user and log in with him to set the GTK preferences or is there a better way to get what I'm looking for?

---

