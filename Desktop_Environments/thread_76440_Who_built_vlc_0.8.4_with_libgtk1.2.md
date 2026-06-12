---
title: "Who built vlc 0.8.4 with libgtk1.2???"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Envel on 2005-10-15
The 0.8.2 version was built with libgtk2. What happened?

---

### Post by GTvulse on 2005-10-15
It is related to a problem with the previous buld in Breezy's repo. I don't know if the fix was recompiling with wxWidgets 2.4 instead of wxWidgets 2.6 though. I've filed a [bug report]("https://launchpad.net/distros/ubuntu/+sources/vlc/+bug/3191").

---

### Post by shidai.liu on 2005-10-15
[QUOTE=dradul]It is related to a problem with the previous buld in Breezy's repo. I don't know if the fix was recompiling with wxWidgets 2.4 instead of wxWidgets 2.6 though. I've filed a [bug report]("http://https://launchpad.net/distros/ubuntu/+sources/vlc/+bug/3191")report.[/QUOTE]

The link redirect to [http://www.paypal.com/](http://www.paypal.com/)

> The 0.8.2 version was built with libgtk2. What happened?

This puts me off using vlc. Basically I don't use any gtk1 programs.

---

### Post by lithorus on 2005-10-15
The correct link is [https://launchpad.net/distros/ubuntu/+sources/vlc/+bug/3191]("https://launchpad.net/distros/ubuntu/+sources/vlc/+bug/3191")

I've also had some problems with wxWidgets2.6 since there is no non-unicode build, but only the unicode version, which requires somewhat different code and doesn't include odbc support.

---

### Post by Kimm on 2005-10-16
I just set off re-compiling vlc agains wxwidgets 2.6.2 and with gtk2... gtk1 just wount do.

---

### Post by GTvulse on 2005-10-16
OK. The bug is closed and the reason is this: [http://lists.ubuntulinux.org/archives/breezy-changes/2005-October/012774.html](http://lists.ubuntulinux.org/archives/breezy-changes/2005-October/012774.html)

---

### Post by Kimm on 2005-10-16
well... if anyone wants it, this is my build of vlc

[http://i.domaindlx.com/MrKimm/vlc-0.8.4_0.8.4-svn20050920-1_i386.deb](http://i.domaindlx.com/MrKimm/vlc-0.8.4_0.8.4-svn20050920-1_i386.deb)

Its just a Checkinstall package, so it doesnt tell dpkg what dependencies it has, and it install as vlc-0.8.4, not wxvlc or vlc.

If you use it and get problems with it, tell me and I can give you my build of wxGTK and ffmpeg

---

### Post by crimsun on 2005-10-16
[QUOTE=Envel]The 0.8.2 version was built with libgtk2. What happened?[/QUOTE]
I did. The changelog has been referenced.

---

### Post by Frankk on 2005-10-17
[QUOTE=Kimm]well... if anyone wants it, this is my build of vlc

[http://i.domaindlx.com/MrKimm/vlc-0.8.4_0.8.4-svn20050920-1_i386.deb](http://i.domaindlx.com/MrKimm/vlc-0.8.4_0.8.4-svn20050920-1_i386.deb)

Its just a Checkinstall package, so it doesnt tell dpkg what dependencies it has, and it install as vlc-0.8.4, not wxvlc or vlc.

If you use it and get problems with it, tell me and I can give you my build of wxGTK and ffmpeg[/QUOTE]

Can you please upload it somewhere else? it says that the bandwidth quota has been exceeded.

If you pm me I can give you my ftp and you can put it there and I could give passwd to people tham need it and pm me.

Thanks

---

### Post by angrykeyboarder on 2005-10-26
[quote=shidai.liu]This puts me off using vlc. Basically I don't use any gtk1 programs.[/quote]

Kudos to you sir! ;-)  I thought I was the only one with this "policy".

---

### Post by vassie on 2005-10-26
Fixed :D

[http://www.ubuntuforums.org/showthread.php?p=445422](http://www.ubuntuforums.org/showthread.php?p=445422)

Ben

---

### Post by angrykeyboarder on 2005-10-26
[quote=crimsun]I did. The changelog has been referenced.[/quote]\


So in other words, we're stuck with dated, old, ugly, stanky GTK1 unless we fend for ourselves...?

---

