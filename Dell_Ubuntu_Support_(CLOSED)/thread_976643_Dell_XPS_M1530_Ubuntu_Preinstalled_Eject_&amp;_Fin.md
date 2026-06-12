---
title: "Dell XPS M1530 Ubuntu Preinstalled Eject &amp; Fingerprint Reader"
date: 2008-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oceanfirehawk on 2008-11-09
Hello all,

I'm having a problem with my new xps m1530 ubuntu preinstalled. 

1) The sleek eject button is not working. I can eject it within the gui but not with the button on top of the keyboard.

2) Does anyone know how to configure the fingerprint reader.

---

### Post by Clockswork on 2008-11-09
Just go into "System-Preferences-Keyboard shortvuts" And bind the Eject button to the eject command.

And the fingerprint reader should work with this..
[Taken from this site]("http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530")
> Fingerprint reader

 

Install thinkfinger-tools and libpam-thinkfinger:

 

```
sudo apt-get install thinkfinger-tools libpam-thinkfinger
```

 

Test it and edit /etc/pam.d/common-auth as described in the Ubuntu wiki and reboot.

 

Unfortunately I have some problems after logging in by swiping my finger. It looks like not all software understands that I've logged in and asks for me to type in my password - which ofcourse defeats the purpose of the fingerprint reader... See bug #221900.



---

### Post by oceanfirehawk on 2008-11-09
> **Clockswork said:**
> Just go into "System-Preferences-Keyboard shortvuts" And bind the Eject button to the eject command.

And the fingerprint reader should work with this..
[Taken from this site]("http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530")

I went to system-preferences-keyboard shortcuts.

I highlited the eject, and pressed the eject button. nothing happened.

---

### Post by Darrell Lawrence on 2008-11-09
> **oceanfirehawk said:**
> Hello all,

I'm having a problem with my new xps m1530 ubuntu preinstalled. 

1) The sleek eject button is not working. I can eject it within the gui but not with the button on top of the keyboard.

2) Does anyone know how to configure the fingerprint reader.

I have an XPS M1530 preloaded with Ubuntu 8.04 and my eject button is working. You might want to post your problem over on the Dell Linux site to let them know. Item 2: There is a Dell shortcut on the desktop that contains a pdf document for setting up the fingerprint reader. If you no longer have that shortcut on your desk top, you can access the Dell documents in /usr/share/dell/DELL. Dell already has the fingerprint reader software preloaded for you.

Darrell

---

### Post by aw4lly on 2008-11-18
This problem has been solved here

[http://ubuntuforums.org//showthread.php?t=115499](http://ubuntuforums.org//showthread.php?t=115499)

This happens because the eject button is hardwired in and wont unmount the CD unless told to otherwise.

Hope it helps,
Aw4lly

---

### Post by Unlearned on 2009-02-09
i used the method gandalf suggested and it works mostly for my m1530, but sometimes when it ejects a disc the comp still thinks it is there and will not let me open a new disc

any ideas?

---

### Post by Zachs Kappler on 2009-06-27
Try this:

[IMG]http://i159.photobucket.com/albums/t130/MechaManiac/Screenshot-EjectDiscProperties.png[/IMG]

It is still done through the Gnome GUI, but it will eject and unmount the disc drive as well. plus I got a PW joke out of it too!

I have it on my desktop at a somewhat large size for ease of use.

---

