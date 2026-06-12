---
title: "s3 driver help!"
date: 2004-12-29
forum: Desktop Environments
---

### Post by veedubdesign.com on 2004-12-29
Hi, with much discussion with a friend, I've installed ubuntu from using mandrake 10. I've gotten the install done, now my video card s3Trio3D 86c366 was using the vesa driver which only allowed a 640x480 resolution. After poking around I found the s3virge driver to be a better mate to my video hardware. But, I'm still limited to 800x600. I really can't enjoy the OS because it looks stupid. Is there anywhere that I can manually configure to get the 1024x768 resolution.

thanks

ra

---

### Post by feneks on 2004-12-30
How did you change the resolution to 800x600?

To configure resolution Ubuntu has the comand
*sudo dpkg-reconfigure xserver-xfree86*

There you may change the resolution. If it doesn't work perhaps activating the framebuffer could help. - Is questioned during the mentioned configuration too.

--edit---
Jubilation!
Just got a star! "Ubuntu Inspiring Guru" sounds cool   8)

---

### Post by ellingtn on 2004-12-30
[QUOTE=veedubdesign.com]Hi, with much discussion with a friend, I've installed ubuntu from using mandrake 10. I've gotten the install done, now my video card s3Trio3D 86c366 was using the vesa driver which only allowed a 640x480 resolution. After poking around I found the s3virge driver to be a better mate to my video hardware. But, I'm still limited to 800x600. I really can't enjoy the OS because it looks stupid. Is there anywhere that I can manually configure to get the 1024x768 resolution.

thanks

ra[/QUOTE]
 I had this same problem when I first isntaled Ubuntu. I have an ATI Radeon 9500 card, that I know could handle better than 800x600 and 640x480, but that was all that it was configured for. 

I searched this forum and found my answer.  I canot find the thread just now, however, I  manually added to XF86Config-4 config file, the resolution I wanted.  The DefaultDepth was OK for me, but in **all** sections of Modes, I added the additional resolution(s) I wanted, 1024x768. Restarted the Xserver, I think, I may ave just logged out and back in, but when I went to the control panel app to change my resolutions, 1024 x768 was there and I enabled it no errors

 -begin cut

 DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection

- end cut

---

### Post by feneks on 2004-12-30
[QUOTE=ellingtn] I  manually added to XF86Config-4 config file, the resolution I wanted. [/QUOTE]

In my opinion this would be the next step after trying to use debconf. But I think it's  okay to do this without trying my proposal first.  :D

---

### Post by veedubdesign.com on 2005-01-03
I'm pissed, I did the reconfig command, I also had nothing but my desired resolution in my config file.  I managed to get it from 600x400 to about 864 or something of the sort.  I'm not a whiz, I sure am not stupid.  I know the config file is what needed to be edited and I did so many times with many combinations of refresh and different drivers.  

In the urgency of needing a machine, I'm using xandros the bootleg windows knock-off.  oh how pretty it is, but that's it. 

Can i use the same lines in xandros to config ubuntu?

---

### Post by feneks on 2005-01-04
If you talk about XF86Config-4 - well give it a try.
Don't forget to backup the original config file first!

Which driver uses Xandros?

---

