---
title: "Will it break ?"
date: 2006-04-18
forum: Desktop Environments
---

### Post by Storm Rider on 2006-04-18
Running Kubuntu 5.1 with most of the Automatix apps added.  

If I change my sources list and dist-upgrade to Dapper Flight 6, will I break my system?

---

### Post by aysiu on 2006-04-18
Possibly.

---

### Post by yager on 2006-04-19
[QUOTE=aysiu]Possibly.[/QUOTE]

Oh I confirmed that it definitely breaks.  You don't know til you try so I took one for the team.  There seems to be some problem getting some dependencies which leads to problems later.  The screen is going by so fast that you can't see what it is saying.  It is as if it can not find all of the required repositories.
Is it possible that not every instance of Breezy should be replaced with Dapper in the repository list?

What finally reports out is that xwindows wont start.  I reviewed the log file as it indicated and found these 4 error messages.  They are:

```
(EE) Failed to load /usr/xorg/modules/extensions/libGLcore.so
(EE) Failed to load "GLcore"
(EE) Failed to load module "nvidia" (moduled does not exist,0)
(EE) no drivers available
```

There were also several warning messages but they were mostly about missing fonts.

Basically, I was left with just a shell and no way to start X.  Any ideas before I wipe the drive and reload Breezy with automatix?

---

### Post by Jason_25 on 2006-04-19
I have an idea.  

```

sudo nano /etc/X11/xorg.conf

```
Change driver from nvidia to vesa.  Also you may want to comment (#) glcore.  Then ctrl-o, enter, ctrl-z.
```

sudo /etc/init.d/gdm restart

```

And next time don't use automatix.  The minimal time it saves isn't worth the breakages, especially if you are unprepared to fix them.

---

### Post by Storm Rider on 2006-04-19
Yager,
Mine broke as well.  Oh well, half the fun is trying something new.

A reinstall was pretty quick, for me , probably much faster than trying to fix it.:D

---

### Post by yager on 2006-04-19
I tried and was unsuccessful.

I change the driver to VESA and looked an old config file and used the original nv driver as well.  Both cases came back with the same error that the driver could not be found.

The config file indicates that you can edit it using the "man" tool.  I tried this but was not successful in editing the file.

Also, xorg.conf indicates that it was created from a tool called dexconf.  Anyone know how to run that?  Maybe that will have better luck.

Update:  I continued the search for the answer on the forums and thought I had found pay dirt.  The thread suggested using aptitude to update the files using the dapper revised sources.list.  Started it up and.......

It removed 137 packages from my system leaving me with nothing but the kernel and the tty screen.  Wow, that was a mistake..  Reinstalling from DVD of Breezy and may try again based on some of the other threads that I found.

I will get back to let everyone know if I was successful.

---

