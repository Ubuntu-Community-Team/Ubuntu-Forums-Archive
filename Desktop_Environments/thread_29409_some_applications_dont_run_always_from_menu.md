---
title: "some applications dont run always from menu"
date: 2005-04-24
forum: Desktop Environments
---

### Post by zupermanz on 2005-04-24
Ive noticed that some applications dont allways run from the kde menu nor the taskbar...For example kynaptic...that once in a while if i run it i get an hourglass...wait for a minute then nothing happens,i try to run it agian the same... :(
But if i sudo kynaptic everithing works! Why? Any ideas?
Besides that i think kubuntu is a great distro even for noobs like me (ive switheced from mdk 10.1 2 weeks ago)
Thanks in advance

---

### Post by Oxy42 on 2005-04-24
After having upgrading the kde lib and running through every problems described everywhere in the forum no applications is working from the kde menu.
I cannot launch terminal, synaptic ou anything...

---

### Post by Oxy42 on 2005-04-24
A bit more constructive.
here are the logs I am getting when launching many applications from the menu:
```

There was an error loading config value for whether to use menubar access keys. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config value for whether to use menu accelerators. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error getting the list of terminal profiles. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config from /apps/gnome-terminal/profiles/Default. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config value for whether to use image in menus. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config value for whether to use mnemonics. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
There was an error loading config from /desktop/gnome/interface. (Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

(gnome-terminal:23641): Gdk-CRITICAL **: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed

(gnome-terminal:23641): GConf-WARNING **: Directory `/desktop/gnome/interface' was not being monitored by GConfClient 0x80f0610

```

However, it seems that after many trying the applications finally come up and work. Go figure out.

---

### Post by ludi on 2005-04-24
[QUOTE=zupermanz]Ive noticed that some applications dont allways run from the kde menu nor the taskbar...For example kynaptic...that once in a while if i run it i get an hourglass...wait for a minute then nothing happens,i try to run it agian the same... :(
But if i sudo kynaptic everithing works! Why? Any ideas?
Besides that i think kubuntu is a great distro even for noobs like me (ive switheced from mdk 10.1 2 weeks ago)
Thanks in advance[/QUOTE]
 Hi,
Sudo have no action for me in KDE. So, instead of sudo I use kdesu nameofapp and everything works just fine.
Try this.

---

### Post by zupermanz on 2005-04-25
Sudo and kdesu works....but i want to work from the menus and not the command line,,,,

---

### Post by beefsprocket on 2005-08-21
Having the same problem just a few months after this thread. Sometimes they start, sometimes they don't. Then when they do there are two slots in the taskbar for the app until it goes into an idle state. 

Not to revive a dead thread or anything -- no one seems to have figured this out?

Edit: For anyone who may run into this problem in the future, upgrade to 3.4.2. Seems to have drastically reduced occurences of this problem.

---

