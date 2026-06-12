---
title: "Is Gnome really that fragile?"
date: 2005-12-07
forum: Desktop Environments
---

### Post by badtyprr on 2005-12-07
I'm a relatively new linux user and have recently discovered that Red Hat isn't the only distribution option available. :D I'm really happy with Ubuntu (Breezy) and had more of my hardware work with Ubuntu than with Fedora. I've found Ubuntu to be more than friendly, but I ran into some issues which I could not solve.

I was installing packages via Synaptic, solving small problems like inputting Chinese, installing multimedia codecs, installing video drivers, etc. All was well until something snapped.. I booted into Ubuntu one day to find that several apps would load, then crash within seconds. Also, some programs would say they were starting, like the Networking utility in the system menu (I think it's there..), then it would quit immediately. I'm assuming it crashed, but I didn't know how what the program's name was to run it in terminal to get debug info. I've seen cases on the Ubuntu forums where Gnome becomes sluggish for many, taking half a minute to load programs, and the like. I checked the running processes, and all programs were taking up 5% or so of my CPU total. I did find that it was running around 190MB RAM usage, which seemed uncharactaristically high for Linux. But, I guessed that it was normal for the amount of programs I installed just to "try".  I opted to format instead fix, being more wary of what I install this time. I think the last thing I installed was scim, if that helps any.

Is there a fix for this problem? Because if so, I must've missed it when I searched the forums. If there's any extra info you think you might need to help me with this problem, please ask. I don't think Gnome has a limit to how many programs you can install, is there? That would just be silly. Just installing a lot packages wouldn't necessarily take a system down, right?

I'd really appreciate the help, thanks.

---

### Post by soulestream on 2005-12-07
1. you probably broke something

2. Hardware support isnt distro specific. If ubunut supports it, redhat supports it (with the same kernel)

soule

---

### Post by badtyprr on 2005-12-07
Obviously, something is broken. But can Linux be broken by only installing packages from Synaptic? I'll keep the hardware comment in mind, but I do have to say that it's much less headache if everything just works. If possible, I'd like to know what exactly causes Gnome to slow to a crawl, is it a specific package that causes this? Is it a combination of packages? Is it not package related?

---

### Post by karmon on 2005-12-07
i used to have this exact problem when i was using ubuntu 5.04, and even a reinstallation wouldnt solve it.

---

### Post by RAOF on 2005-12-07
From memory, during Breezy testing SCIM broke **everything**.  I'm not sure if they fixed that fully before release - it's in Universe, so maybe they didn't.  Could you try running one of the programs that crashes from a console window, and noting any of the debug messages it spits out?

[quote=soulestream]
...
2. Hardware support isnt distro specific. If ubunut supports it, redhat supports it (with the same kernel)
...
[/quote]

This isn't necessarily true - there's more to hardware support than just the kernel version.  There's all sorts of userspace tools, what modules the kernel was built with, what patches the devs have applied to the kernel (neither Redhat nor Ubuntu run stock vanilla kernels - they're both patched in some way).  In short, it is **perfectly** possible for Ubuntu to work better with your hardware than Redhat.

---

### Post by badtyprr on 2005-12-08
So, I run the gnome-app-install and get a few results from the console, but no crashing or abnormal exit codes. When I run it from the Gnome menu, it will not open. But when run from the console, it opens after a delay.. odd.. Anyways, here's what the console spit out:
```
$ /usr/bin/gksudo /usr/bin/gnome-app-install
/usr/lib/gnome-app-install/AppInstall.py:196: GtkWarning: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
  LaunchpadIntegration.add_items (widget, -1, False, True);
Launching a SCIM daemon with Socket FrontEnd...
GTK Panel of SCIM 1.0.2

Starting as daemon ...
Launching a SCIM daemon with Socket FrontEnd...

(synaptic:9547): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9547): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9547): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

```

Note, *scim -d* is already running. Obviously, everytime it loads something in the GUI, it kicks off a thread to handle each instance of a window, apparently accompanied by the delay or crashing of the window altogether. Is it really necessary to have a thread for every window? Why can't scim just translate keyboard entries, resolve keystrokes through a database, and spit it out into a window without making such a fuss? The delay for each worker thread is about 5 seconds long, and this makes the Gnome GUI **very** annoying to use. I have not tested scim with KDE. Anybody have any idea how to fix the "5 second delay problem"? If it helps, the language I am using scim for is Chinese (pinyin NOT chewing).

Edit: Also, I found something disturbing when running the scim input method setup:
```
$ sudo scim-setup
Loading Config Module gconf
Loading Config Module simple
Loading Config Module socket
Loading Setup Module panel-gtk-setup
Loading Setup Module pinyin-imengine-setup
Segmentation fault

```
That can't be good. :) I know I have all of the dependencies and files necessary for scim to function.. it just doesn't work. 

Edit: Apparently, every application is getting seg faults from scim. I just tested it with the gnome-app-install again and got this:
```
$ /usr/bin/gksudo /usr/bin/gnome-app-install
Launching a SCIM daemon with Socket FrontEnd...
Segmentation fault

```

Is there a way to fix this? Or am I just going to have to uninstall this? If this isn't a viable option, is there another IM to go with here for Simplified Chinese? Also, is there somewhere I can report this to? I'm sure the developers would like to know if there are bugs in scim. I think it's fairly reproducible and all, but I've never submitted a report. So, I'm not sure how.

Thanks, any help would be appreciated. :)

---

### Post by badtyprr on 2005-12-08
I can't seem to find any resources on this problem. karmon seems to have had the same problems, and RAOF confirms that SCIM breaks everything. I'm reading every guide that I can, and I can't find anything that helps. Please, if you know something post. Thanks.

Edit: After fiddling around with SCIM a little more, I was able to resolve the issue. I did NOT add *scim -d* to the sessions startup list. Also, I used this guide which was helpful: [http://ubuntuguide.org/#scim](http://ubuntuguide.org/#scim)

I believe that if you follow through with this guide, you should have no issues. Do not add *scim -d* to the sessions startup list, as the howto on the ubuntu forums states.

---

