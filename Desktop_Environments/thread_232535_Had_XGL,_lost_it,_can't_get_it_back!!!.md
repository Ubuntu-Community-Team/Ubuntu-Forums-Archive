---
title: "Had XGL, lost it, can't get it back!!!"
date: 2006-08-08
forum: Desktop Environments
---

### Post by n00buntu NJ on 2006-08-08
Ok, I was about ready to give up until I saw [THIS]("http://www.youtube.com/watch?v=DUSn-jBA3CE").

When I first installed the new Ubuntu 6.06, the very first thing I did was setup XGL.  It was the easiest yet (I've done it with 5.10 and with the latest OpenSuSE).  Then last week I was screwing around with my computer and I can't get the XGL effects back.  I've done everything except wipe the drive and start over again.  I have even removed everything related to XGL and reinstalled it all following the same instructions that worked the first time.  

Lately when I try to call compiz it complains about "No manageable screens found on display 0:0"  and something about pixmaps.  Any help?  Or should I just start over?

---

### Post by computergroove on 2006-08-08
can you post your /etc/X11/xorg.conf

---

### Post by n00buntu NJ on 2006-08-09
> **computergroove said:**
> can you post your /etc/X11/xorg.conf

Sure...  and while I'm at it I'll put my gdm.conf file here too...

EDIT:  Also, this is what happens when I try to call compiz ([these]("http://www.ubuntuforums.org/showthread.php?t=222034&highlight=nvidia+xgl") are the instructions I followed to set it all up):

> chailey@CHubuntu:~$ startcompiz
chailey@CHubuntu:~$ compiz.real: No XKB extension
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

chailey@CHubuntu:~$ gedit
chailey@CHubuntu:~$ sudo startcompiz
chailey@CHubuntu:~$ cgwd: Connection Error (No reply within specified time)
5845: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
5845: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
compiz.real: No XKB extension
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

...And again, I'm using an nVidia GeForce 6200 which has worked like a charm for XGL through 4 or 5 different times of setting it up.  Now all the sudden I can't get it running again.

Thanks in advance for the help!

---

### Post by n00buntu NJ on 2006-08-10
Nobody can help me?  

I'm now to the point where I am just ready to reinstall the whole thing, Ubuntu and all.  ](*,) 

I know it will work on a fresh install.  I've just screwed something up and I'm too frustrated to figure it out.  

It's the thing I love and hate about Linux vs. Windows so far.  I know I don't need to reinstall the OS to recover, like I would in Windows.  But I just can't figure out what I did wrong to even have a chance at fixing it.  :-({|=

---

### Post by HondaDirtBiker on 2006-08-10
I'm experiencing the exact same problem, except I started using a fresh install. I was running xgl on this computer before and it was working fine.

Edit: I got it working I just needed to update ubuntu with the compiz repos.

---

### Post by maniacmusician on 2006-08-10
have you tried that n00buntu? updating the compiz repos?

---

### Post by n00buntu NJ on 2006-08-11
Yup.  It's ok.  I went with the fresh installation.  I now have a brand spankin new Ubuntu on my machine.  And XGL is back.  It only took about 3 minutes to get it up and running (first try).  I don't know what was wrong before, but it's working now.

---

### Post by maniacmusician on 2006-08-11
awesome, congratulations.

---

