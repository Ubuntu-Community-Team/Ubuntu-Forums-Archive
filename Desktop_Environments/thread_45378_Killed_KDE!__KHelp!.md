---
title: "Killed KDE!  KHelp!"
date: 2005-06-29
forum: Desktop Environments
---

### Post by underpope on 2005-06-29
Somehow in the process of trying to get wireless networking going on my shiny new Kubuntu laptop (and tightVNC), I managed to kill KDE to the point where it won't start up.  I get the login screen and the splashscreen, and it gets as far as "Setting up interprocess communication", 7but it dies before launching KDE with this error message:

```

There was an error setting up inter-process communications for KDE.  The message returned by the system was:

Could not read network connection list.
/home/richard/.DCOPserver_musicserver__0

Please check that the "dcopserver" program is running!

```

I know that I can get into "safe mode" to fix things up -- I just don't know what to fix.

---

### Post by apollo2011 on 2005-06-29
OK, I got a similar (if not identical) message on my SuSE system right after I started using Ubuntu.  I never tried very much to get SuSE working anymore because I like Ubuntu better.  I am not sure what causes this, but you might try the second option in the boot loader, Recovery Mode.  At least if you get into that, you can use the machine and work from there to find out what is working.  The Recover mode is similar to WinXP's Safe Mode.

---

### Post by ltmon on 2005-06-30
With recovery mode I don't think you get a graphical desktop.  Once your system freezes you can also keep going by pressing CTRL-ALT-F1 to get to a virtual terminal.

Once there login.

> cd ~/.kde

> ls

You should see the directories share/, config/ and some cache directories. 

They are named  cache something-or-other or temp something-or-oither.  There's 2 or 3 of them.  I'm not at my home PC so I can't remember.

Delete the contents of each of the cache directories:

> rm -rf <cache-directory-name>/*

Then restart KDE

> sudo /etc/init.d/kdm stop
> sudo /etc/init.d/kdm start

If this trick doesn't work you may have to delete some settings.  A quick way is to remove the entire ~/.kde directory, but then you lose ALL your settings for all programs.  This can be a pain if you've worked with your desktop for a while.

Post back here with the results and I'll see if I can find a less damaging way of removing your settings (i.e. just remove the network settings or something).

Cheers,

L.

EDIT:

The names of the directories whose contents you should delete on the first try are:

~/.kde/socket-<hostname>

~/.kde/tmp-<hostname>

and

~/.kde/cache-<hostname>

L.

---

### Post by apollo2011 on 2005-06-30
[QUOTE=ltmon]With recovery mode I don't think you get a graphical desktop.[/QUOTE]

No you definitely get a graphical desktop if you chose to.  When it loads it asks for the root password.  If you hit Ctrl+D, it loads the default DM and loads the desktop.

---

### Post by ltmon on 2005-06-30
[QUOTE=apollo2011]No you definitely get a graphical desktop if you chose to.  When it loads it asks for the root password.  If you hit Ctrl+D, it loads the default DM and loads the desktop.[/QUOTE]


In that case, refer to my previous post.... but just press CTRL-ALT-F1 after KDM has loaded (before you try to log in, or when it freezes if you have autologin set up).

L.

---

