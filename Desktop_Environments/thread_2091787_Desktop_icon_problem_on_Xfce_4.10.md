---
title: "Desktop icon problem on Xfce 4.10"
date: 2012-12-06
forum: Desktop Environments
---

### Post by wgerven on 2012-12-06
Hello everybody,
I am running xubuntu 12.04 with Xfce 4.10. Lately some strange behaviour developed about my desktop icons. I have them ordered in a specific way on my desktop, but upon reboot, the DE doesn't want to remember this ordering any more. Instead, it just orders them the standard way from up to down, left to right. Regardless of whether I put them again in the right positions on my desktop or not. 
Could somebody perhaps point out to me how to solve this problem? Would it help to reinstall my DE? And how would that go about? 
Any help is very much appreciated!

Best regards,
Willem.

---

### Post by Toz on 2012-12-06
Hello and welcome to the forums.

Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1919849") thread and LewisTM's suggestion about using chattr to lock the icon positions.

---

### Post by wgerven on 2012-12-06
Hello Toz, thank you for your reply and welcome.
I will try tonight this suggested solution. I just don't understand where it comes from. At my work I run exactly the same configuration without this problem showing up. However, there is a minor difference: At my work my desktop nicely shows the preview of the pdf's on my desktop, at my laptop at home (which has the stated problem) this is not shown, although both are upgraded by this same way 
[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)
to xfce 4.10. 
Any thought on where this comes from, whether it is related to my already mentioned problem and how to cure this?
Many thanks!

Willem.

---

### Post by Toz on 2012-12-06
> **wgerven said:**
> Hello Toz, thank you for your reply and welcome.
I will try tonight this suggested solution. I just don't understand where it comes from. At my work I run exactly the same configuration without this problem showing up. However, there is a minor difference: At my work my desktop nicely shows the preview of the pdf's on my desktop, at my laptop at home (which has the stated problem) this is not shown, although both are upgraded by this same way 
[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)
to xfce 4.10. 
Any thought on where this comes from, whether it is related to my already mentioned problem and how to cure this?
Many thanks!

Willem.
Is it possible that on your home computer, another process is managing the desktop (i.e. nautilus)?

---

### Post by wgerven on 2012-12-06
Hi Toz, I am not aware of any other process managing my de on my laptop. But I think I already found the (partial) source of my problem.
Together with the strange behaviour of the desktop icons I also noticed that gnome-do started to crash every time it started on login. It loaded but then didn't "get through". The keyboard shortcut didn't start it also anymore, and I had to first select it from the applications menu to start, and only after that I could use gnome-do by the keyboard shortcut. I thought this was an unrelated problem, but in some way it seems both are related. This afternoon I made a purge remove of gnome-do and then installed it again, and now both the problem with gnome-do and my desktop icons is solved! 
I only don't know what caused gnome-do to malfunction, and how gnome-do is related to any desktop misbehaviour.. Any insights on this would be very welcome! 
Anyway my initial problem is solved now. However, the problem with previewing the pdf's as described in my previous most remains.. (I once by accident installed nautilus, but then I again purge removed it, so this should be no compromise right? Or could this be a source of this problem?)
Thanks for your help!

Best,
Willem.

---

### Post by Toz on 2012-12-06
I'm sorry but I've never used gnome-do, so I can't really comment on it.

Can you post the results of this command:
```
ps -ef | grep xf
```
...so I can see what parts of Xfce are running?

---

### Post by wgerven on 2012-12-07
Hi Toz, that is:
```
$ ps -ef | grep xf
1000      2472  2406  0 08:03 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
1000      2504  2472  0 08:03 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
1000      2507     1  0 08:03 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session startxfce4
1000      2515  2472  0 08:03 ?        00:00:00 xfce4-session
1000      2517     1  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
1000      2521     1  0 08:03 ?        00:00:00 xfwm4 --replace
1000      2523     1  0 08:03 ?        00:00:00 xfce4-panel
1000      2527     1  1 08:03 ?        00:00:01 xfdesktop
1000      2625     1  0 08:03 ?        00:00:00 xfce4-volumed
1000      2628     1  0 08:03 ?        00:00:00 xfsettingsd
1000      2632     1  0 08:03 ?        00:00:00 xfce4-power-manager
1000      2642     1  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd
1000      2654  2523  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 4 14680097 systray Notification Area Area where notification icons appear 
1000      2656  2523  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/xfce4/panel-plugins/libnotes.so 10 14680098 xfce4-notes-plugin Notes Ideal for your quick notes 
1000      2657  2523  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-indicator-plugin  5 14680099 indicator Indicator Plugin An indicator of something that needs your attention on the desktop 
1000      2659  2523  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/xfce4/panel-plugins/libdatetime.so 7 14680100 datetime DateTime Date and Time plugin with a simple calendar 
1000      2660  2523  0 08:03 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libactions.so 12 14680101 actions Action Buttons Log out, lock or other system actions 
1000      3995     1  0 08:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/exo-1/exo-helper-1 --launch TerminalEmulator
1000      3996  3995  6 08:04 ?        00:00:00 /usr/bin/xfce4-terminal
1000      3998  3996  0 08:04 ?        00:00:00 [xfce4-terminal] <defunct>
1000      4055  3999  0 08:04 pts/0    00:00:00 grep --color=auto xf
```Thanks for you help! 
Willem

---

### Post by Toz on 2012-12-07
Do you have evince-common installed?
```
apt-cache policy evince-common
```

Do you have an **evince.thumbnailer** file in /usr/share/thumbnailers?

---

### Post by wgerven on 2012-12-10
```
$ apt-cache policy evince-common
evince-common:
  Installed: 3.4.0-0ubuntu1.4
  Candidate: 3.4.0-0ubuntu1.4
  Version table:
 *** 3.4.0-0ubuntu1.4 0
        500 http://si.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.4.0-0ubuntu1 0
        500 http://si.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

```
/usr/share/thumbnailers$ ls
evince.thumbnailer  gnome-font-viewer.thumbnailer  totem.thumbnailer

```

thanks for the help!

---

### Post by Toz on 2012-12-10
Does deleting the ~/.thumbnails folder help? (You may have to log out and back in again.)

---

### Post by wgerven on 2012-12-11
Hi Toz, no that didn't do the trick. However, one clue might be that at my work the folder ~/.thumbnails contained a subfolder "large" with in there .png's being the previews of the pdf's on my desktop. At my home laptop (with the problem) this folder does not exist.

---

### Post by dentaku65 on 2012-12-11
Hi,

since I need to have my icons on the desktop on left side, I just made right click on desktop and choose "Arrange Desktop icons" this is how my desktop looks like... of course I'm pretty sure that "Arrange Desktop icons" works only in case you need the icons on the left...

---

