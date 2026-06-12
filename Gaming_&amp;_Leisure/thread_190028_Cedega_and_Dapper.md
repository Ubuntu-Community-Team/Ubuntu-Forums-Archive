---
title: "Cedega and Dapper"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by R3linquish3r on 2006-06-05
Well I tried installing Cedega on Dapper today and it looks like Dapper as an updated library so I cant install Cedega! Fun!

Heres the info I'm getting:

```
ed@ubuntu:~$ sudo dpkg -i cedega_5.1_i386.deb 
Selecting previously deselected package cedega.
(Reading database ... 122929 files and directories currently installed.)
Unpacking cedega (from cedega_5.1_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega
ed@ubuntu:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate
```

I tried installing the new suggested ones but Cedega wasn't very happy :(. Does anyone have a workaround or another way to get this running?

---

### Post by R3linquish3r on 2006-06-05
Actually never mind I found what I was looking for in the UGA :D

---

### Post by rslo on 2006-06-09
Where is the answer? and what is UGA?

---

### Post by Sukarn on 2006-06-09
yeah, what is UGA? I'm curious now...

---

### Post by Spif on 2006-06-09
I have the same problem. There is only a dev version of Xlibs in the reposetories.

---

### Post by deathbyswiftwind on 2006-06-09
You can get xlibs from the breezy repo. Also there is a post in the forums somewhere how you can remove xlibs from being a dependency of cedega

---

### Post by deathbyswiftwind on 2006-06-09
Here is the link I was speaking of [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)

Or here is xlibs from breezy
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb)

I did install xlibs from breezy onto my dapper system. Didnt seem to have any problems but I would suggest the other method. (I got the link from Artifical Intelligence so thank him for finding it) I suggest doing it this way for a few reasons. 

1. Dapper already has the files needed they were just renamed.
2. The xlibs package of breezy wont be being updated for security reasons
3. Why waste the space :mrgreen: 

Anyways best of luck to you either way you go

---

### Post by Spif on 2006-06-09
Thanks mate :)

Guild Wars, here I come...

---

### Post by PsYsK8eR on 2006-06-17
[QUOTE=deathbyswiftwind]Here is the link I was speaking of [http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)

Or here is xlibs from breezy
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb)

I did install xlibs from breezy onto my dapper system. Didnt seem to have any problems but I would suggest the other method. (I got the link from Artifical Intelligence so thank him for finding it) I suggest doing it this way for a few reasons. 

1. Dapper already has the files needed they were just renamed.
2. The xlibs package of breezy wont be being updated for security reasons
3. Why waste the space :mrgreen: 

Anyways best of luck to you either way you go[/QUOTE]


The problem with the first workaround is that is time consuming, because everytime a ".deb" package is missing "xlibs" you'll have to edit the package. 

The second workaround sucks, because of the 3 reasons you mentioned.

The solution to all of this is installing a "dummy package", which i have attached to this reply.

good luck! =)

---

### Post by eqisow on 2006-06-17
Err, I just installed Cedega 5.2 on a clean Dapper install. No errors.

---

### Post by handy on 2006-06-18
5.2 has fixed the xlibs problem.

---

### Post by Liz on 2006-11-03
meh@here:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
meh@here:~$

when i first installed cedega, both openGL and 3D accelerator tests failed ....now 3D accelerator wont work at all. 

no idea where im going wrong with this. 
any help would be appreciated. 

i have an nvidia geforce2 
old i know, but it still works.

---

### Post by Liz on 2006-11-06
well i got glxgears working. 
dont ask me how. 
but the frame rates are very very slow. 
im halfway there at least. 

now to get 3d accelerator working.

---

### Post by handy on 2006-11-06
Have you looked at the stickies in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") sub-forums?

[This one looks helpful for your card too!]("http://ubuntuforums.org/showthread.php?t=233241")

---

