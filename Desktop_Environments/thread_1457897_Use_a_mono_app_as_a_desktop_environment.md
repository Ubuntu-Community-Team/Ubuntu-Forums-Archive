---
title: "Use a mono app as a desktop environment?"
date: 2010-04-19
forum: Desktop Environments
---

### Post by kaigoh on 2010-04-19
Hi guys.

I have a shell I have written in C# for Windows. I have ported it over to Linux (Ubuntu) and it works well as an app running under Gnome.

What I would like to know is how to use the shell I have written instead of Gnome? What I want is a way of booting straight into my custom shell without the default desktop environment loading.

I have spent the morning searching but am yet to find any solutions.

If anyone can point me in the right direction it would be much appreciated!

Thanks,

Kai.

---

### Post by Stunts on 2010-04-19
Hi there.
I think what you need is to create a session using your sehll that you can login into from GDM (I suppose you are using GDM since it's Ubuntu's default).
You can start by looking here:
[http://ubuntuforums.org/showthread.php?t=61135](http://ubuntuforums.org/showthread.php?t=61135)

It's a bit old, but most of it is probably still true today.

You can try here too:
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

Have fun, and let us know how it turned out!

---

### Post by kaigoh on 2010-04-28
Thanks for the tip Stunts!

Kai.

---

### Post by Stunts on 2010-04-28
You're welcome!

Enjoy!

---

### Post by 3rdalbum on 2010-04-28
> **kaigoh said:**
> Hi guys.

I have a shell I have written in C# for Windows. I have ported it over to Linux (Ubuntu) and it works well as an app running under Gnome.

Link? If you need some web space I'd be happy to host/mirror a copy for you on my site.

---

### Post by kaigoh on 2010-04-30
No link just yet because it is a proof of concept project. Thanks for the offer of the hosting though!

Once I have got a bit further with my idea, I'll be sure to update this thread and provide a link.

Thanks,

Kai.

---

### Post by kaigoh on 2010-05-11
Thanks for all the above advice, I've now got my shell running perfectly from the GDM login screen.

However, if I configure the system so that it boots straight into my shell, rather than being run through GDM, the text looks messy and anti-aliasing dosn't work. Any ideas?

Also, I really want a way to totally remove Gnome from the system, including GDM, and have my shell operate as the window manager and the desktop manager. Can someone point me in the direction of how I can go about configuring the system to behave this way? I've searched, but I don't think I'm looking for the right thing.

Thanks,

Kai.

---

### Post by Stunts on 2010-05-12
Hi again kaigoh.
If you are looking to replace GDM, try the lightweight "slim" login manager.
The reason for loosing the anti-aliasing is that that feature is enabled by "gnome-settings-manager". If you're not loading GNOME, then the settings manager don't really apply so you don't get font effects. I'm sure there are other ways to do it tough.
after installing "Slim" just read the man page for it, it's quite detailed if my memory doesn't fail me.
Alternatively you can just start gnome-settings-manager as part of your session. That should get you anti-aliasing back up and running.
Let us know how it turned out.

---

