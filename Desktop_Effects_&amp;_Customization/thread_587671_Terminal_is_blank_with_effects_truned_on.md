---
title: "Terminal is blank with effects truned on"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by monos98 on 2007-10-22
When I turn the desktop effects on, I am unable to get my windows boarders back and my terminal comes up as a blank white square.  When I turn the desktop effects back to normal, everything works fine.  What am I doing wrong or missing?

7.10 AMD64, NVidia GeForce 7300GS

[[IMG]http://img152.imageshack.us/img152/1268/screenshotzv7.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshotzv7.png)

---

### Post by mseeba on 2007-10-25
I have a Dell XPS M1210 with exactly the same problem and I have it fixed until I reboot. The effects are great. Give this link a try:

[http://linuxevangelist.blogspot.com/2007/06/ubuntu-7-no-window-borders-on-desktop.html]("http://linuxevangelist.blogspot.com/2007/06/ubuntu-7-no-window-borders-on-desktop.html")

This guy knows what he is talking about here. A couple of things to keep in mind:

1. In Scenario #2, the author is referring to modifying your xorg.conf file (found in /etc/X11) although he or she is not clear about that fact.
2. If you are using 7.10 some of the changes will already be present, but making the rest of them did fix my problem.
3. Once I reboot the system has problems with my files and I have to restore them from backups. Be sure to back your files up before changing.
4. Let me know if you have any luck with these settings. I will continue to play with them one at a time to see if I can get it fixed.

Good luck with it.

-Mark.

---

### Post by mseeba on 2007-10-29
I got it! What I needed to do is only one step of the listed steps on the Linux Evangalist link above. Hopefully it is all you need. FYI, this is for Gutsy, 7.10
Here it is:
Make a backup copy of /etc/X11/xorg.conf (in case you need to restore it).
Edit the file adding this line: 
Option "AddARGBGLXVisuals" "True"
Put the above line in the Section "Screen" as the last line in the section just above the EndSubSection tag.
Save the file and reboot.
With any luck your desktop effects will be working.
Good luck with it!
-Mark.

---

### Post by monos98 on 2007-11-06
Wow.  That worked great.  Took me a minute to look up editing xorg.confg, but that did the trick.

Thanks!!

---

