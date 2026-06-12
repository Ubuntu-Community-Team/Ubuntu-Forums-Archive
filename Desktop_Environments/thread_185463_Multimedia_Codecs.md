---
title: "Multimedia Codecs"
date: 2006-05-31
forum: Desktop Environments
---

### Post by rrsarge on 2006-05-31
I keep seeing different methods and different ideas in a thousand different posts on how to get codecs for Totem...and I'm confused as hell!

Can any one, definitively, tell me, a struggling Linux noob trying to get off Windows crack, how to listen to .mp3's and be able to watch vids (mpg, avi, wmv) in Totem?  How do I install these elusive codecs?  Should I use another program besides Totem?

Thank you!!!!!!!!!!!!!!!!!!](*,)

---

### Post by Metro on 2006-05-31
[QUOTE=rrsarge]I keep seeing different methods and different ideas in a thousand different posts on how to get codecs for Totem...and I'm confused as hell!

Can any one, definitively, tell me, a struggling Linux noob trying to get off Windows crack, how to listen to .mp3's and be able to watch vids (mpg, avi, wmv) in Totem?  How do I install these elusive codecs?  Should I use another program besides Totem?

Thank you!!!!!!!!!!!!!!!!!!](*,)[/QUOTE]

To 5.10?

Here: [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by rrsarge on 2006-05-31
Sorry, I should have said I'm using 6.06.  Will it still work?

---

### Post by detgar on 2006-05-31
This works for me:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)

---

### Post by Metro on 2006-05-31
[QUOTE=rrsarge]Sorry, I should have said I'm using 6.06.  Will it still work?[/QUOTE]

Dapper?
Ok :D 

[http://ubuntuforums.org/showthread.php?t=177646](http://ubuntuforums.org/showthread.php?t=177646)

It is beta but I have use it and everything went ok:)

Read carefully the instructions

---

### Post by az on 2006-05-31
[QUOTE=rrsarge]I keep seeing different methods and different ideas in a thousand different posts on how to get codecs for Totem...and I'm confused as hell!

Can any one, definitively, tell me, a struggling Linux noob trying to get off Windows crack, how to listen to .mp3's and be able to watch vids (mpg, avi, wmv) in Totem?  How do I install these elusive codecs?  [/QUOTE]
The deffinitive place for those answers is:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by rrsarge on 2006-05-31
[QUOTE=Metro]Dapper?
Ok :D 

[http://ubuntuforums.org/showthread.php?t=177646](http://ubuntuforums.org/showthread.php?t=177646)

It is beta but I have use it and everything went ok:)

Read carefully the instructions[/QUOTE]


Well this one didn't work.

---

### Post by Metro on 2006-05-31
[QUOTE=rrsarge]Well this one didn't work.[/QUOTE]


Have you done this?

> Debconf bug in packages with proprietary licenses:

If you want packages with proprietary licenses (like java, flashplugin etc) and you used espresso to install Dapper, you will still have to reconfigure debconf first. To do this open a terminal and type this first?

sudo dpkg-reconfigure debconf


You can use BUMPS: [http://ubuntuforums.org/showthread.php?t=181248](http://ubuntuforums.org/showthread.php?t=181248)

Or you can follow detgar sugestion.

---

### Post by rrsarge on 2006-05-31
[QUOTE=detgar]This works for me:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)[/QUOTE]

This didn't work either...getting errors during install.

example:

rrsarge@bravoubuntu:~$ sudo apt-get install gstreamer0.10-ffmpeg
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate

---

### Post by rrsarge on 2006-05-31
[QUOTE=Metro]Have you done this?



You can use BUMPS: [http://ubuntuforums.org/showthread.php?t=181248](http://ubuntuforums.org/showthread.php?t=181248)

Or you can follow detgar sugestion.[/QUOTE]

Yeah, I did that first.  Do I have to run the deb from terminal..I double-clicked and it ran in gui.

---

### Post by Metro on 2006-05-31
[QUOTE=rrsarge]Yeah, I did that first.  Do I have to run the deb from terminal..I double-clicked and it ran in gui.[/QUOTE]

Have you used automatix and it fail.
Have you follow the instructions to change the sources.list to follow detgar sugestion?

BUMPS ran in GUI.

---

### Post by rrsarge on 2006-05-31
How do I update the sources.list?

---

### Post by Metro on 2006-05-31
[QUOTE=rrsarge]How do I update the sources.list?[/QUOTE]

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

That is not necessary to Automatix or BUMPS

It is to follow this instructions: [http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)

---

### Post by Fornie on 2006-06-07
i have the same predicament...i'll try this later thanks thanks

---

