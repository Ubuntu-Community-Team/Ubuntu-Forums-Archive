---
title: "gnome-panel goes crazy"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Ytrecq on 2006-06-02
A minut of 15 ago I was running Synaptic, Firefox, Terraform and the gnome-panel-applets adder. Then it's running fixed(I don't know the English word, in Dutch it is vastlopen) and I have to restart my computer. But if my computer is restarted, the pannels aren't full loaden. I can only see the backgrounds, and I've started firefox with the start terminal option 'in' the RMB in Natautilus and then firefox [www.ubuntu.com](www.ubuntu.com).
What is the solution?(I can't ask it on ubuntu-nl because it's changing from server.)Thank you.

(Yes, my English isn't very good, but I had only 3 years English what one of the two years was seriously good.)

EDIT: The notification messages, such as them from gmail-notify and the zeroconf discover applet, are shown.

---

### Post by doobit on 2006-06-02
I'm having a similar problem of Gnome not loading properly at each boot up. Sometimes the keyboard doesn't work, sometimes I get an error telling me there was a  problem with the applets loading and sometimes the whole machine locks up right after the background starts to load, and I have to shut off the power to restart. I didn't have these problems with Xfce4. 
It may be related to the Nvidia drivers issues. Do you have an Nvidia card?

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

---

### Post by Ytrecq on 2006-06-02
Yes, I do have a nVidia card. A while ago when I was updating(I was using Dapper alpha) two versions of nVidia drivers parts hadn't the same version, so I couldn't start X. With a dist-upgrade the following day I thought the problem was solved, but now maybe it isn't :( .

---

### Post by doobit on 2006-06-02
Mine does not allow me to exit the desktop or restart from X, or enter the terminal, so I'm not sure how I will be able to impliment the fixes that are in this thread:
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

---

### Post by Ytrecq on 2006-06-02
I don't want to use XGL, I want only to repair gnome-panel(if that the problem is). My graphic card is a GeForce 4000 MX, I don't know if its even has Pixel Shader 0.5!

---

### Post by doobit on 2006-06-02
I think that's the same card I have.

---

### Post by RavenOfOdin on 2006-06-05
Certain KDE themes, if you run KDE at the same time as GNOME, can do this.

I used "Berlin Subway" from KDE-Look.org and while it was on my box I couldn't get into GNOME through "Session Type" . . .The only thing that would load was Metacity, and the panels kept going on and off like crazy.

It had something to do with the theme's splash screen.

This even applies to splash screens that are included with KDE by default, if they're in the wrong folders for a GNOME install. Moodin-KDE does the same thing.

---

### Post by Ytrecq on 2006-06-05
I've solved the problem by myself. I copied the files from /etc/gconf/gconf.xml.default/apps/panel/default_setup to ~/.gconf/apps/panel and it works again!
Thank you for your help.

---

