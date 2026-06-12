---
title: "Theme messed up after update on remote connection"
date: 2009-08-10
forum: Desktop Environments
---

### Post by balmac on 2009-08-10
Hi

since one of the recent updates for Ubuntu (9.04) my gnome theme (default Human) is somehow messed up. I don't know which update in particular caused it, but its probably one in the last 1-2 months.
Strange thing is, it only happens when connected from remote using NoMachine NX, although I'm using the very same user (so all configuration files should be the same).

I don't know whether this is a problem in NoMachine NX or in gnome but since NoMachine wasn't updated I guess its the theme or gnome.

Please view the attached screenshots, the first shows the messed up theme (notice strange separator in the menubar, big fonts, "wrong" icons for trashbin and logout, "wrong" colors ie blue instead of orange etc) when connected from remote. The second one is from the same machine, same user but with a local login.

Any help much appreciated.
Thanks!

balmac

---

### Post by gjoellee on 2009-08-10
Usually when this happens you don't have the gtk engine for the current theme. Just try to find the theme engine and install it. Then reinstall the theme.

And a little tip: if Synaptic does not use the same theme as the one you have enabled, read this page: [http://kshoster.net/?q=tutorials/ubuntu/themegnomeroot](http://kshoster.net/?q=tutorials/ubuntu/themegnomeroot)

---

### Post by balmac on 2009-08-10
gjoelle, thank you for your reply.

But if the gtk engine was missing, wouldn't the theme be wrong on the local user too? 

During search on the net I found the suggestion to install gtk2-engines-ubuntulooks. But before installing, synaptic wants to remove "human-theme", "ubuntu-artwork" and "ubuntu-desktop", I'm not sure if this is a good idea?!?

---

### Post by gfendle on 2009-08-13
> **gjoellee said:**
> Usually when this happens you don't have the gtk engine for the current theme. Just try to find the theme engine and install it. Then reinstall the theme.
That isn't the case this time. 

I've got the same problem as the OP on two machines, both of which were recently updated (with security updates only) and now display the [slightly messed up] default Gnome theme when connecting remotely via nomachine. 

Logging in locally doesn't exhibit the same problems. Everything is just fine.

---

### Post by loeppel on 2009-08-14
Just the same Problem here.
Any suggestions? Is there a GTK log?

Edit:
Really strange is that if i call the gnome-appearance-properties the theme is correct, but the buttons not.
Every other application is just in the gtk-default theme with gnome-default icons.

---

### Post by gjoellee on 2009-08-14
Maybe you should report this is a bug at launchpad?

Also, I think there is is a file named ".gtkrc-2.0" which is located in your home folder. This does usually contain some info about themes and icons etc...

NOTE: It is a hidden file. You can show hidden files by hitting CTRL + H.

---

### Post by masc82 on 2009-08-14
Same here on jaunty. I assume it's not ubuntu related, since I got the very same on a gentoo box since months now, where it's even worse, in addition to the (same) theme/rendering issue, gnome segfaults when opening the appearance dialog.

Cleaning out configurations doesn't help. I've reverted to kde for now due to this :(

edit: btw. it happens with both freenx and nomachine nxserver, though vnc apparently works.

---

### Post by gfendle on 2009-08-14
> **masc82 said:**
> Same here on jaunty. I assume it's not ubuntu related
I've got the same issue on a clean Debian Lenny install here, too.

---

### Post by gfendle on 2009-08-15
Not seeing this problem on my 8.04.3 desktop install here, despite updating everything available today.

This isn't the first time I've regretted installing 9.04 on a machine. For all the bells and whistles, it just doesn't feel anything like as stable and polished as earlier releases. 

I saw someone equate 9.04 to Windows Vista elsewhere, seems about right to me with 8.04 being Windows XP. 

Lesson learned, even if the fault does lie with nomachine.

---

### Post by loeppel on 2009-08-17
So i have a workaround for the theme issue!

There is no .gtkrc-2.0 in my $HOME.
So i've created one with the following content.

```
gedit ~/.gtkrc-2.0
```
```

gtk-theme-name="Human"
gtk-icon-theme-name = "Human"

```

I think this issue is with Gnome > 2.24 and is related to the gnome-settings-dameon which seems to fail! I've heard that there is a known issue with it in 2.26 but that one should be fixed in 2.26.1.

---

### Post by gfendle on 2009-08-17
> **loeppel said:**
> So i have a workaround for the theme issue!
This is excellent. Well done and thank you!

I've just done a clean install of 9.04 Desktop in a VM, installed nomachine, did the updates, and it exhibited the aforementioned problems. Applied your fix and everything was back to normal. 

I've just repeated the exercise on a spare laptop here with exactly the same results. 

Many thanks.

---

### Post by loeppel on 2009-08-18
There is a Bug Report for this issue:
[https://bugs.launchpad.net/freenx-server/+bug/399758](https://bugs.launchpad.net/freenx-server/+bug/399758)

---

### Post by spiorf on 2009-08-25
i think i found the solution:
downgrade libxklavier to version 3.9-0ubuntu1. for some reason the new version crashes gnome-settings-daemon when connected with freenx-nomachine.

I locked the package version in synaptic to avoid future auto-updates.

---

### Post by wuhaa on 2009-08-26
> **spiorf said:**
> i think i found the solution:
downgrade libxklavier to version 3.9-0ubuntu1. for some reason the new version crashes gnome-settings-daemon when connected with freenx-nomachine.

I locked the package version in synaptic to avoid future auto-updates.

How do you do this?

---

### Post by spiorf on 2009-09-10
you can force a package version in synaptics, and then you lock it. remembar to not upgrade throug apt-get dist-upgrade, but only with synaptics or update-manager, because apt ignores the lock setting in synaptics

can't provide step-by-step because i have a different language

---

### Post by ryanferreri on 2009-10-30
Can anyone provide instructions for this in Karmic? I Synaptic all I see is the currently installed version. Older versions do not seem to be available.

---

### Post by gfendle on 2009-11-03
> **ryanferreri said:**
> Can anyone provide instructions for this in Karmic? I Synaptic all I see is the currently installed version. Older versions do not seem to be available.Have you tried the workaround [here]("https://bugs.edge.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245/comments/1")?

Disabling the keyboard plugin for Jaunty works for me on the two machines I access remotely with Nomachine, so I'm sticking with it. Works even with the latest version of libxklavier installed. 

Thankfully I installed Karmic on a spare machine. Some aren't so lucky to have such things available to them. I was very disappointed to see a large number of bugs carried over from previous releases, plus a bunch of new ones. Maybe this is just another one to add to the list. 

I gave up on Karmic when I couldn't get shared printing working at all. Others are having the same problem it seems. This whole new release every six months thing is quite hilarious at times.

---

