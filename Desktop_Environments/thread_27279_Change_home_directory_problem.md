---
title: "Change home directory problem?"
date: 2005-04-15
forum: Desktop Environments
---

### Post by juliocesargarcia on 2005-04-15
I have done very little customization to my GNOME desktop. For some work requirements, I had to change my home directory from /home/julio to /labshome/julio.

When I restarted the desktop, things did not go well. In the past, I simply removed every file and directory that I could guess belonged to GNOME/KDE/etc and just restarted. This fixed things and I re-did my minor configuration preferences. No big deal, but one of the more anoying issues that I have had with upgrades or changes of this nature.

This time, I am not able to get panels at all, no matter what I do or delete. It almost appears as if /home is somehow hardcoded somewhere and will not work properly elsewhere. What do I need to do to get a new, "out of the box" home desktop?

I hope I have not missed something obvious. Thanks for any help. I will also try upgrading to 5.04 soon.

Julio

---

### Post by nad on 2005-04-15
Did you try ' mv /home/julio /labshome/julio ', then creating a symlink ' ln -s /labshome/julio /home/julio '? This will maintain permissions. The system and applications expect to find your files in the /home directory unless you have done some serious environment reconfiguring.

Dan M

---

### Post by juliocesargarcia on 2005-04-15
[QUOTE=nad]Did you try ' mv /home/julio /labshome/julio ', then creating a symlink ' ln -s /labshome/julio /home/julio '? This will maintain permissions. The system and applications expect to find your files in the /home directory unless you have done some serious environment reconfiguring.

Dan M[/QUOTE]

I did try that and it did not work either. So, I should not expect things to work outside of /home without lots of work?

---

### Post by nad on 2005-04-15
How about just setting up a new user ' labshome ', then copying stuff over?

Or a hard link ' ln /labshome/julio /home/julio ' ?

I've had similar problems setting up home directories over nfs. I haven't got my head completely around ubuntu yet.

Dan M

---

### Post by juliocesargarcia on 2005-04-15
I'll keep trying and see how far I get. Thanks for the pointers. Let you know how far I get.

--
julio

---

### Post by nad on 2005-04-15
Something else I just thought of. Modify your /etc/gdm/gdm.conf file to point to your new home.

This ought to configure your applets and panel correctly.

Dan M

---

### Post by juliocesargarcia on 2005-04-15
[QUOTE=nad]Something else I just thought of. Modify your /etc/gdm/gdm.conf file to point to your new home.

This ought to configure your applets and panel correctly.

Dan M[/QUOTE]
 I'm pretty GNOME illiterate. I did not see and obvious seting for home directories. There are some referenese to the cookies files, but not home directories. Hope I'm not being dense.

Julio

---

### Post by nad on 2005-04-15
"I'm pretty GNOME illiterate". Me to. I've always used xdm before with much lighter desktops. These new fangled 'desktop environments' take some getting used to. Gnome is wonderful for the point and click generation. Customizing by one user for one's own login is one thing. Configuring for a certain environment is something else.

I've been waiting for someone who knows to chime in. In the meantime I will continue to learn with you.

Dan M

---

### Post by juliocesargarcia on 2005-04-18
[QUOTE=nad]"I'm pretty GNOME illiterate". Me to. I've always used xdm before with much lighter desktops. These new fangled 'desktop environments' take some getting used to. Gnome is wonderful for the point and click generation. Customizing by one user for one's own login is one thing. Configuring for a certain environment is something else.

I've been waiting for someone who knows to chime in. In the meantime I will continue to learn with you.

Dan M[/QUOTE]
 Well, I give up. I upgraded to 5.04 and  I still have problems. I now get a the error dialog box with "failed to initialize HAL". I thik I will do some more experimentation with symbolic links. What a pain. It seems like it should not be this hard.

---

### Post by juliocesargarcia on 2005-04-18
I did a little more investigation and found this link:
[http://www.ubuntuforums.org/showthread.php?t=24146](http://www.ubuntuforums.org/showthread.php?t=24146)

I reinstalled HAL and  I still have the problem. I also noticed that at boot time, the init.d/dbus-1 script errors out with a segmentation violation.

---

### Post by nad on 2005-04-18
Good catch with the HAL problem. I suspected, while working on another project, that HAL, GVM, pmount and udev are not ready for the real world. Unfortunately this does not answer your immediate problem, linking your non-standard home directory.

We have to keep in mind that the devs do their best at making certain that there are no errors in code and packages. We are the front line when setting up systems for the real world and can only hope that a dev will chime in with his/her thoughts, suggestions and advice.

Dan M

---

### Post by nad on 2005-04-18
Ummm... Have you read the help guides, Desktop -> User Guide and System Administration Guide? These explain the gconf system using gconfd. The Holy Grail of gnome. A virtual database of configuration options using xml files.

Time for some serious reading.

Dan M

---

### Post by juliocesargarcia on 2005-04-19
Thanks for the pointer. I think my problems are related to HAL and dbus-1. I am pursuing that here now:

[http://ubuntuforums.org/showthread.php?t=28049](http://ubuntuforums.org/showthread.php?t=28049)

---

