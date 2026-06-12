---
title: "How do I load dependencies for Opera 9.0b2: Specifically xlib6g| xlibs?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by RAV TUX on 2006-06-03
I am trying to load Opera 9.0b2 on Ubuntu 6.06 and have the dependency prompt come up xlib6g|xlibs not satisfied. How do I overcome this and load Opera?







.

---

### Post by Colonel Kilkenny on 2006-06-03
You can fetch that xlibs-package from Breezy repositories.

edit.
wget [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb)
sudo dpkg -i xlibs_6.8.2-77.1_all.deb

---

### Post by RAV TUX on 2006-06-03
[quote=Colonel Kilkenny]You can fetch that xlibs-package from Breezy repositories.[/quote]

Is this in the Synaptic Package Manager?







.

---

### Post by Colonel Kilkenny on 2006-06-03
Just making sure that you noticed that I edited previous post.
Those commands to console should do the trick. Then you can remove the .deb file.

---

### Post by RAV TUX on 2006-06-03
[quote=Colonel Kilkenny]Just making sure that you noticed that I edited previous post.
Those commands to console should do the trick. Then you can remove the .deb file.[/quote]

ok this is what I got:

jozef@ubuntujozef:~$ sudo dpkg -i xlibs_6.8.2-77.1_all.deb
Password:
dpkg: error processing xlibs_6.8.2-77.1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xlibs_6.8.2-77.1_all.deb
jozef@ubuntujozef:~$

---

### Post by RAV TUX on 2006-06-03
I do seem to getting somewhere, when I grab, drag and drop the deb file into the terminal I get this:

[[IMG]http://img60.imageshack.us/img60/7241/screenshot26jj.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshot26jj.png)

---

### Post by RAV TUX on 2006-06-03
[quote=yozef]I do seem to getting somewhere, when I grab, drag and drop the deb file into the terminal I get this:

[[IMG]http://img60.imageshack.us/img60/7241/screenshot26jj.th.png[/IMG]]("http://img60.imageshack.us/my.php?image=screenshot26jj.png")[/quote]

This is my progression thus far:

[[IMG]http://img119.imageshack.us/img119/5710/screenshot33eb.th.png[/IMG]](http://img119.imageshack.us/my.php?image=screenshot33eb.png)

[[IMG]http://img109.imageshack.us/img109/390/screenshot40py.th.png[/IMG]](http://img109.imageshack.us/my.php?image=screenshot40py.png)

[[IMG]http://img119.imageshack.us/img119/9031/screenshot51om.th.png[/IMG]](http://img119.imageshack.us/my.php?image=screenshot51om.png)

[[IMG]http://img109.imageshack.us/img109/3937/screenshot69bu.th.png[/IMG]](http://img109.imageshack.us/my.php?image=screenshot69bu.png)

OK the last screenshot had a discouraging message...

---

### Post by RAV TUX on 2006-06-03
[quote=yozef]This is my progression thus far:

[[IMG]http://img119.imageshack.us/img119/5710/screenshot33eb.th.png[/IMG]]("http://img119.imageshack.us/my.php?image=screenshot33eb.png")

[[IMG]http://img109.imageshack.us/img109/390/screenshot40py.th.png[/IMG]]("http://img109.imageshack.us/my.php?image=screenshot40py.png")

[[IMG]http://img119.imageshack.us/img119/9031/screenshot51om.th.png[/IMG]]("http://img119.imageshack.us/my.php?image=screenshot51om.png")

[[IMG]http://img109.imageshack.us/img109/3937/screenshot69bu.th.png[/IMG]]("http://img109.imageshack.us/my.php?image=screenshot69bu.png")

OK the last screenshot had a discouraging message...[/quote]

but I clicked applications: internet: and what do you know there is an Icon for Opera!

so I give it a go:

and this is what I got:

[[IMG]http://img111.imageshack.us/img111/5593/screenshot70ll.th.png[/IMG]](http://img111.imageshack.us/my.php?image=screenshot70ll.png)

& then

[[IMG]http://img111.imageshack.us/img111/9671/screenshot81gc.th.png[/IMG]](http://img111.imageshack.us/my.php?image=screenshot81gc.png)

WOW! how exciting success !...I now am a proud user of Opera 9.0b2 on Ubuntu 6.06!!!



Thanks for all your help !

---

### Post by RAV TUX on 2006-06-03
[quote=Colonel Kilkenny]You can fetch that xlibs-package from Breezy repositories.

edit.
wget [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb")
sudo dpkg -i xlibs_6.8.2-77.1_all.deb[/quote]

**Colonel Kilkenny** really thank you very much for you quick replies and assistance! this has made my day ! 

...and a Thank You to all the Devs. who worked on this incredible OS Ubuntu 6.06 !




.

---

### Post by ffi on 2006-06-03
[QUOTE=yozef]**Colonel Kilkenny** really thank you very much for you quick replies and assistance! this has made my day ! 

...and a Thank You to all the Devs. who worked on this incredible OS Ubuntu 6.06 !




.[/QUOTE]

The latest release (build 315) from Opera doesn´t need those packages anymore as they are linked to proper Dapper libs. Ypu can also repackage the opera.deb [http://my.opera.com/community/forums/findpost.pl?id=1447916](http://my.opera.com/community/forums/findpost.pl?id=1447916) and delete the depency (it´s not needed anyway by Opera)

---

### Post by RAV TUX on 2006-06-04
[quote=ffi]The latest release (build 315) from Opera doesn´t need those packages anymore as they are linked to proper Dapper libs. Ypu can also repackage the opera.deb [http://my.opera.com/community/forums/findpost.pl?id=1447916]("http://my.opera.com/community/forums/findpost.pl?id=1447916") and delete the depency (it´s not needed anyway by Opera)[/quote]

we're not talking about the latest Opera but Instead Opera 9.0 beta 2.

---

### Post by ffi on 2006-06-04
[QUOTE=yozef]we're not talking about the latest Opera but Instead Opera 9.0 beta 2.[/QUOTE]


Me too, build 315 is a newer (post 9 beta 2) build.

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by blackpaw on 2006-06-15
I just got myself a build from named snapshot-directory and it's called:
"opera-static_9.0-20060612.1-qt_en_**dapper**_i386.deb"
:D

the (pletty nice) installer says "all dependencies are satisfied"

and it's all good :)

2 clicks with the mouse.. and the root password. 
I love it :)


'paw

---

### Post by RAV TUX on 2006-06-21
[QUOTE=blackpaw]I just got myself a build from named snapshot-directory and it's called:
"opera-static_9.0-20060612.1-qt_en_**dapper**_i386.deb"
:D

the (pletty nice) installer says "all dependencies are satisfied"

and it's all good :)

2 clicks with the mouse.. and the root password. 
I love it :)


'paw[/QUOTE]

from where do you have a link I just updated to Opera 9 and I am trying to get Java plugin enabled

---

