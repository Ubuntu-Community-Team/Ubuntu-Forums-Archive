---
title: "New Openoffice version?"
date: 2005-01-24
forum: Desktop Environments
---

### Post by mirtux on 2005-01-24
Hi everybody,
   i have one question regarding new versions of OpenOffice. I've seen on their website that version [COLOR=Red]1.1.4[/COLOR] is available for download [HTML]http://download.openoffice.org/index.html[/HTML] . Who we might ask for add a compiled version to the ubuntu repositories so that we can upgrade without breaking the system? 

Of course i can download the new version and install it separately but it would be better to upgrade using apt-get.....

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=mirtux]Hi everybody,
   i have one question regarding new versions of OpenOffice. I've seen on their website that version [COLOR=Red]1.1.4[/COLOR] is available for download [HTML]http://download.openoffice.org/index.html[/HTML] . Who we might ask for add a compiled version to the ubuntu repositories so that we can upgrade without breaking the system? 

Of course i can download the new version and install it separately but it would be better to upgrade using apt-get.....[/QUOTE]


Well......the is no way to add new software to Warty's repositories. Only bug fixes are added.

All the work now is being done on Hoary. You want Firefox 1.0, Openoffice.org 1.14? You have to upgrade to Hoary. I use Hoary on my desktop. Its is buggier than Warty, I would say use caution with it. 

On this thread there is talk of a way to get it from Debian:

[http://ubuntuforums.org/showthread.php?t=8578&page=1&pp=10&highlight=openoffice+backport](http://ubuntuforums.org/showthread.php?t=8578&page=1&pp=10&highlight=openoffice+backport)

but that is risky to.

Ubuntu is set up to have 6 month releases. That means for new programs, you either use the unstable version or just upgrade every six months.

The choice for me was easy. I love new stuff!

---

### Post by Perfect Storm on 2005-01-24
You could add hoary repo. to your warty and get some of the newest stuff. But it's risky too, and I wouldn't advise it.


.:=The AI Dude=:.

---

### Post by Viro on 2005-01-24
Is there anything in OO 1.1.4 that's worth upgrading for?

---

### Post by mirtux on 2005-01-24
[QUOTE=Viro]Is there anything in OO 1.1.4 that's worth upgrading for?[/QUOTE]
Well, thanks you all for your replies.

I've got one problem that has been resolved in OO 1.1.4. Have a look here [http://www.openoffice.org/issues/show_bug.cgi?id=28715](http://www.openoffice.org/issues/show_bug.cgi?id=28715). 
In my case the problem doesn't present so often, but it is still annoying... However upgrading was also a shield against some bugs that i didn't have discovered yet!

Regards,
MC

---

### Post by Viro on 2005-01-24
Don't know if you've tried, but give Gnumeric a shot. It opens the document in the bug id without problems (apart from 2 work sheets that don't have data because I think the original deleted them. Same error occurs in OO). I've tried scrolling lots and haven't had a crash for the last 2 minutes of continuous scrolling and switching work sheets. OO crashed not long after I tried scrolling (3rd worksheet).

Give gnumeric a try.

---

### Post by jdong on 2005-01-24
[QUOTE=mirtux]Well, thanks you all for your replies.

I've got one problem that has been resolved in OO 1.1.4. Have a look here [http://www.openoffice.org/issues/show_bug.cgi?id=28715](http://www.openoffice.org/issues/show_bug.cgi?id=28715). 
In my case the problem doesn't present so often, but it is still annoying... However upgrading was also a shield against some bugs that i didn't have discovered yet!

Regards,
MC[/QUOTE]

Debian patches their OO.o heavily, with stuff like GNOME/KDE file associations, Ximian's desktop integration (i.e. GNOME-style file->open dialogs), etc. It takes a LOT of effort to repatch an upstream version of Openoffice.org.

Hoary has a heavily patched 1.1.3. See if it has the fix. If not, file a bug with Debian, so they'd include the patch.

---

### Post by gheorghe_pop on 2005-01-24
Look at this it's OpenOffice 2 BETA:
[OpenOffice -with gtk file chooser](http://www.pvv.org/~jorgensa/slackware/ooo-ximian-1.9.66-i686-1hyb.png) 
[OpenOffice no gtk file chooser](http://www.pvv.org/~jorgensa/slackware/ooo-1.9.65-i586-1hyb.png) 
They look very nice.Too bad that i got only slackware packages for them...but i think i'll try a alien.:)

---

### Post by andy_sp1ke on 2005-01-24
Firefox is easy, just download it form their website and install it, its very easy. Openoffice you can download but its in rpm format, not deb. I havent worked out how to install those!

andy

---

### Post by Perfect Storm on 2005-01-24
sudo alien <name of the file>.rpm

---

### Post by buldir on 2005-01-24
[QUOTE=andy_sp1ke]Firefox is easy, just download it form their website and install it, its very easy. Openoffice you can download but its in rpm format, not deb. I havent worked out how to install those!

andy[/QUOTE]

Can you just install OO 1.1.4 using the tarball?

---

### Post by mirtux on 2005-01-25
[QUOTE=Artificial Intelligence]sudo alien <name of the file>.rpm[/QUOTE]

Hi,
  regarding the OpenOffice 2 rpm, we can just do the command you suggest, for all of them?

Regards,
MC

---

