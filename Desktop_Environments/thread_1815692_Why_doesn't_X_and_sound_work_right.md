---
title: "Why doesn't X and sound work right?"
date: 2011-07-31
forum: Desktop Environments
---

### Post by dapfy on 2011-07-31
I remove /etc/init/gdm.conf, log in on text console and run startx.  My xinitrc starts a few things and then runs sawfish window manager.

Since 11.4 this has been weird: no sound and some windows not refreshing, e.g. as I type or scroll.  At times I have somehow managed to get sound working, exactly while I switch to the text console from which I ran startx.

Now I have a new laptop with a fresh install.  Still the same pain, actually seems like more windows sometimes don't refresh. ](*,)

To exclude my many settings from being incompatible, I've created a new user.  For some reason startx gives him the fallback gnome2 like desktop.  Nm-applet doesn't manage to connect to wifi, after choosing it in the menu: nothing.  No sound, i.e. nothing under hardware in the settings dialog.  I didn't notice window redrawing problems, but maybe didn't use it long enough...

So I reactivated gdm, just to see.  My account contains something that prevents it.  No error message, just goes back to the login window :(

But the same new account that caused problems above, suddenly runs unity, nm-applet works, as does sound.  There is a shocking number of daemons running.  I tried to start some of them manually in my sawfish environment to no avail.

What is all this bogus magic:confused:  What is the secret to just getting a minimalist working environment???

---

### Post by dapfy on 2011-08-04
Ok, I discovered /etc/gdm.  Xsession has a bug, in that it tries to source my .profile into a Bourne Shell.  Of course the syntax fails and my session crashes &#8212; how dumb!  If Ubuntu hacks into a user's environment like that, they should at least look up the right Shell!  Mine has grown over many years, and I keep it portable across bash and ksh on various flavours of Unix.

Having clumsily worked around that, now I can gdm into my customary sawfish session, and sofar everything seems to work fine.

Fancy needing gdm to set up the X server correctly!  They broke the straightforward way, and recreated it around something complicated...

---

### Post by FormatSeize on 2011-08-04
> **dapfy said:**
>  They broke the straightforward way, and recreated it around something complicated...
A wise, and probably very old man once said, "The easier you try to make things for average users, the more cumbersome simple things become for savvy users."
 
That is what is happening here.

---

