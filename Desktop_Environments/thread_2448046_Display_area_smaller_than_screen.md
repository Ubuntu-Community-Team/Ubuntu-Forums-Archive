---
title: "Display area smaller than screen"
date: 2020-07-31
forum: Desktop Environments
---

### Post by mringer on 2020-07-31
L-Ubuntu 16.04
Suddenly (a few days ago) a white margin has appeared at the LHS of my screen, about 2"
wide. If I try to drag a window left, it gets cropped at the margin. If I maximise the window
it only goes as far as the margin. The task bar goes all the way to the LH corner of the screen.
If I login as a different user, the display area behaves correctly.

This problem (or similar) has appeared before:

[https://ubuntuforums.org/showthread.php?t=2260555](https://ubuntuforums.org/showthread.php?t=2260555)

but the solutions given there do not work for me. These were:

```

openbox --reconfigure

```

No change.  Or to check the file:  ~/.config/openbox/lubuntu-rc.xml  .  
On my PC the file is   ~/.config/openbox/lxde-rc.xml  . But this file is dated
July 15 (long before the problem appeared) and the margins are all 0.

So I tried:

```

rmd@rmd-sns:~$ touch --date="26 july 2020 00:00" /tmp/x
rmd@rmd-sns:~$ find .??* -newer /tmp/x

```

The output was far too long so I have cut it:

```

.bash_history
.cache

[8000 files skipped in .cache ]

.config
.config/lxpanel/LXDE/panels
.config/lxpanel/LXDE/panels/left
.config/lxpanel/LXDE/config
.config/chromium

[ 500 more files skipped ]

.config/dconf
.config/dconf/user
.config/VirtualBox
.config/VirtualBox/selectorwindow.log
.config/VirtualBox/VirtualBox.xml
.config/VirtualBox/VBoxSVC.log
.config/VirtualBox/VirtualBox.xml-prev
.config/lxsession/LXDE
.config/lxsession/LXDE/desktop.conf
.config/libfm
.config/libfm/dir-settings.conf
.config/libfm/libfm.conf
.config/QtProject.conf
.config/pcmanfm/LXDE
.config/pcmanfm/LXDE/desktop-items-0.conf
.config/pcmanfm/LXDE/pcmanfm.conf
.config/gtk-3.0
.config/gtk-3.0/bookmarks
.config/lxterminal/lxterminal.conf
.dbus/session-bus/e98fa912a36da36d3a17942b5a2ad686-0
.dbus/session-bus/e98fa912a36da36d3a17942b5a2ad686-1
.emacs.d/auto-save-list
.emacs.d/auto-save-list/.saves-2455-rmd-sns~
.gconf
.local/share
.local/share/recently-used.xbel
.local/share/gvfs-metadata
.local/share/gvfs-metadata/home-8afd1ebe.log
.local/share/gvfs-metadata/home

[ and .mozilla ]

.Xauthority
.xsession-errors
.xsession-errors.old

```

and the obvious suspects are the files in ...LXDE   but I looked in these & cannot see anything about margins.

Please any help? Thank you.

---

### Post by guiverc on 2020-07-31
Lubuntu 16.04 LTS being a flavor of Ubuntu had only 3 years of supported life which ended 2019-April.

[https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/)
[http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7) have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case.

I suggest you move to a supported release of Lubuntu for security reasons, unless you're off-line or are aware of risks. Your alternative if you must use 16.04, is Ubuntu without desktop, the default desktop, or Kylin desktop (which Canonical supported for 5 years for 16.04 only)

---

### Post by ActionParsnip on 2020-07-31
Could even install Ubuntu minimal then install LXDE. This will give you a super light OS and full 5 years support. You may want to take this issue as a catalyst to upgrade to Ubuntu 20.04 after first running a final full backup and wiping the install off. Ubuntu 20.04 is LTS and supported until April 2025

---

### Post by mringer on 2020-08-05
Thank you who replied. I was (& still am) very reluctant to install L-Ub 20 because (1) this is a long job (2) recent versions of L-Ub have been badly bloated & (3) I had no reason to believe that this would have solved my problem. 

Eventually, I did:

```
adduser bill
rm -R /home/me/.??*
cp -R /home/bill/.??* /home/me
chown -R me /home/me
```

and a few tweaks. The problem disappeared. I dont call this a solution because I still have no idea what was wrong.

---

