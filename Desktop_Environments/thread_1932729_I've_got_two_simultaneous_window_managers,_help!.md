---
title: "I've got two simultaneous window managers, help!"
date: 2012-02-28
forum: Desktop Environments
---

### Post by trendle on 2012-02-28
Tired of having a crude screen 640x480 or something every time I forgot to switch my KVM after hitting the start button I stupidly followed some advice.... 
sudo dpkg-reconfigure xserver-xorg
So now when I login, I see my original screen briefly, then it disappears for an unwanted screen with an on screen keyboard :confused:

After wasting a few hours on this.  I have no idea where to look to track whats going on after login.  It's nothing in my .bashrc
Eventually, running the process monitor I saw two different window manager processes with -display :0  Duh!.
So I killed the one with the higher process id and now I'm back to my original screen.  Hooray. but it won't last.  I'm sure as soon as I login again I'll be back to the same cr*p.

So please, can anyone suggest which file I have to attack to fix this.
Thanks.

---

### Post by Toz on 2012-03-05
> **trendle said:**
> Tired of having a crude screen 640x480 or something every time I forgot to switch my KVM after hitting the start button I stupidly followed some advice.... 
sudo dpkg-reconfigure xserver-xorg
So now when I login, I see my original screen briefly, then it disappears for an unwanted screen with an on screen keyboard :confused:

After wasting a few hours on this.  I have no idea where to look to track whats going on after login.  It's nothing in my .bashrc
Eventually, running the process monitor I saw two different window manager processes with -display :0  Duh!.
Out of curiosity, what are the two window managers?
> So I killed the one with the higher process id and now I'm back to my original screen.  Hooray. but it won't last.  I'm sure as soon as I login again I'll be back to the same cr*p.

So please, can anyone suggest which file I have to attack to fix this.
Thanks.

Not sure why you've got two window managers running after reconfiguring xorg. Doesn't make sense.

What happens, after you kill the other window manager process, when you go to Settings Manager->Session and Startup->Session tab and click on "Save Session" and logout and in again? Perhaps you've got two window managers cached to start. This should save it. 

If not, you can always reset the saved sessions cache by deleting the ~/.cache/sessions directory.

---

### Post by trendle on 2012-03-06
Hi,
I see 
xfwm4 --display :0.0
and
xfce-panel --display :0.0
and
xfdesktop --display :0.0

all with their ppid 
xfce4-session
who's ppid is
/etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc

I don't recall doing anything else other than the reconfigure,  but perhaps I got a different prompt at login and answered wrongly.  I can't quite remember, since I've been thrashing around trying to see what would fix this.

---

### Post by trendle on 2012-03-06
There was one other time on a different PC also with an older Xubuntu,  that showed something that may be similar.  For some reason,  Xdisplay had two entries, laptop and the actual screen (it was a desktop).  If they were both enabled then I saw a smaller window manager overlapping the other.  Once I made sure that only the desktop was enabled that cured it.  But no such luck this time.  Only 1 display is listed.

---

### Post by Toz on 2012-03-07
What version of Xubuntu are you using?

Can you post back the results of:
```
ps -ef | grep xf
```

When you ran > sudo dpkg-reconfigure xserver-xorg...was an /etc/X11/xorg.conf file created? If so, can you post back the contents of that file?

Also, when you go to Settings Manager->Display, how many displays show?

---

### Post by trendle on 2012-03-08
Actually, that's always been something that's bamboozled me. Where do you find out what version of Xubuntu you're on ?  I can find the version of the kernel and xfce...  But I'm pretty sure it's 11.10, since I only installed it around Xmas.

But on to your request.  ps -ef | grep xf
bill      1820   900  0 19:17 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
bill      1851  1820  0 19:17 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startxfce4
bill      1854     1  0 19:17 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startxfce4
bill      1863     1  0 19:17 ?        00:00:00 /usr/lib/xfce4/xfconf/xfconfd
bill      1873  1820  0 19:17 ?        00:00:00 xfce4-session
bill      1878  1873  0 19:17 ?        00:00:01 xfwm4 --display :0.0 --sm-client-id 289a3ed63-f6d7-4a68-8021-4479b6fd0847
bill      1880     1  0 19:17 ?        00:00:00 xfsettingsd --force
bill      1886  1873  0 19:17 ?        00:00:04 xfce4-panel --display :0.0 --sm-client-id 25d7834b4-7ae0-4a52-b988-a37b476d9c60
bill      1897     1  0 19:17 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 232ebdd2c-3590-40d9-bb6c-1fbcc0ac43b9
bill      1898     1  0 19:17 ?        00:00:00 xfce4-settings-helper --display :0.0 --sm-client-id 244913a26-05b6-4be0-a1de-4b1604a188cc
bill      1901     1  0 19:17 ?        00:00:00 /usr/lib/xfce4/notifyd/xfce4-notifyd
bill      1902  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libsystray.so 4 20971572 systray Notification Area Area where notification icons appear 
bill      1904  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4-indicator-plugin/xfce4/panel-plugins/xfce4-indicator-plugin  5 20971573 indicator Indicator Plugin An indicator of something that needs your attention on the desktop 
bill      1906  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libxfsm-logout-plugin.so 9 20971578 xfsm-logout-plugin Session Menu Shows a menu with options to lock the screen, suspend, shutdown, or log out 
bill      1909  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libthunar-tpa.so 24 20971601 thunar-tpa Trash Applet Display the trash can 
bill      1961     1  0 19:17 ?        00:00:00 xfce4-volumed
bill      1992     1  0 19:17 ?        00:00:01 xfce4-terminal --geometry=138x40 --display :0.0 --role=Terminal-0x20a8f800-2790-1331262387 --show-menubar --show-borders --hide-toolbars --working-directory /etc/X11
bill      2015  1992  0 19:17 ?        00:00:00 [xfce4-terminal] <defunct>
bill      2279     1  0 19:19 ?        00:00:02 xfce4-settings-manager
bill      2287     1  0 19:20 ?        00:00:02 xfdesktop-settings --socket-id=65012403
bill      2362     1  2 19:22 ?        00:00:04 xfce4-settings-manager
bill      2365  1886  7 19:22 ?        00:00:11 xfce4-taskmanager
bill      2373  2307  0 19:25 pts/1    00:00:00 grep --color=auto xf


I don't think dpkg-reconfigure xserver-xorg did generate /etc/X11.xorg.conf.  There is one there,  but it has nothing in it, except..
bill@xubuntu:~$ cat /etc/X11/xorg.conf 

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "InputClass"
	Identifier "Keyboard Defaults"
	Option "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection

There is only one display device listed.

One thing I notice that makes me wonder... 
Normally when I try it wit hXubuntu live,  if I change the background from the system settings, it changes immediately.  But here I don't.  I also don't see my desktop icons... which according to the systems settings I should have Home etc.  I do see them briefly after logging in, but then they seem to get overlaid with a solid blue screen.

I'm sorry if this thread seems to be a bit slow... I was using the problem pc to run ddrescue on a 2TB drive that took 2.5days to complete.  So not much chance to experiment on it.
Thanks for your patience.

---

### Post by Toz on 2012-03-09
> **trendle said:**
> Actually, that's always been something that's bamboozled me. Where do you find out what version of Xubuntu you're on ?  I can find the version of the kernel and xfce...  But I'm pretty sure it's 11.10, since I only installed it around Xmas.
This will tell you what *buntu version you are using:
```
cat /etc/lsb-release
```

> But on to your request.  ps -ef | grep xf
bill      1820   900  0 19:17 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
bill      1851  1820  0 19:17 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startxfce4
bill      1854     1  0 19:17 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startxfce4
bill      1863     1  0 19:17 ?        00:00:00 /usr/lib/xfce4/xfconf/xfconfd
bill      1873  1820  0 19:17 ?        00:00:00 xfce4-session
bill      1878  1873  0 19:17 ?        00:00:01 xfwm4 --display :0.0 --sm-client-id 289a3ed63-f6d7-4a68-8021-4479b6fd0847
bill      1880     1  0 19:17 ?        00:00:00 xfsettingsd --force
bill      1886  1873  0 19:17 ?        00:00:04 xfce4-panel --display :0.0 --sm-client-id 25d7834b4-7ae0-4a52-b988-a37b476d9c60
bill      1897     1  0 19:17 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 232ebdd2c-3590-40d9-bb6c-1fbcc0ac43b9
bill      1898     1  0 19:17 ?        00:00:00 xfce4-settings-helper --display :0.0 --sm-client-id 244913a26-05b6-4be0-a1de-4b1604a188cc
bill      1901     1  0 19:17 ?        00:00:00 /usr/lib/xfce4/notifyd/xfce4-notifyd
bill      1902  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libsystray.so 4 20971572 systray Notification Area Area where notification icons appear 
bill      1904  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4-indicator-plugin/xfce4/panel-plugins/xfce4-indicator-plugin  5 20971573 indicator Indicator Plugin An indicator of something that needs your attention on the desktop 
bill      1906  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libxfsm-logout-plugin.so 9 20971578 xfsm-logout-plugin Session Menu Shows a menu with options to lock the screen, suspend, shutdown, or log out 
bill      1909  1886  0 19:17 ?        00:00:00 /usr/lib/xfce4/panel/wrapper /usr/lib/xfce4/panel/plugins/libthunar-tpa.so 24 20971601 thunar-tpa Trash Applet Display the trash can 
bill      1961     1  0 19:17 ?        00:00:00 xfce4-volumed
bill      1992     1  0 19:17 ?        00:00:01 xfce4-terminal --geometry=138x40 --display :0.0 --role=Terminal-0x20a8f800-2790-1331262387 --show-menubar --show-borders --hide-toolbars --working-directory /etc/X11
bill      2015  1992  0 19:17 ?        00:00:00 [xfce4-terminal] <defunct>
bill      2279     1  0 19:19 ?        00:00:02 xfce4-settings-manager
bill      2287     1  0 19:20 ?        00:00:02 xfdesktop-settings --socket-id=65012403
bill      2362     1  2 19:22 ?        00:00:04 xfce4-settings-manager
bill      2365  1886  7 19:22 ?        00:00:11 xfce4-taskmanager
bill      2373  2307  0 19:25 pts/1    00:00:00 grep --color=auto xf
This looks okay.

> I don't think dpkg-reconfigure xserver-xorg did generate /etc/X11.xorg.conf.  There is one there,  but it has nothing in it, except..
bill@xubuntu:~$ cat /etc/X11/xorg.conf 

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "InputClass"
	Identifier "Keyboard Defaults"
	Option "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection
Nothing that could cause the problem here

> There is only one display device listed.
Ok.

> One thing I notice that makes me wonder... 
Normally when I try it wit hXubuntu live,  if I change the background from the system settings, it changes immediately.  But here I don't.  I also don't see my desktop icons... which according to the systems settings I should have Home etc.  I do see them briefly after logging in, but then they seem to get overlaid with a solid blue screen.
Would you happen to have nautilus installed? Is it running?
```
ps -ef | grep nautilus
```
If so, nautilus by default will by default take over control of the desktop. See this link: [http://ubuntuforums.org/showpost.php?p=11736713&postcount=6]("http://ubuntuforums.org/showpost.php?p=11736713&postcount=6") for info on how to disable that behaviour.

> I'm sorry if this thread seems to be a bit slow... I was using the problem pc to run ddrescue on a 2TB drive that took 2.5days to complete.  So not much chance to experiment on it.
Thanks for your patience.
No worries.

---

### Post by trendle on 2012-03-09
Hi, Toz,
Thanks for taking the time over this.
So I am running 11.10 Xubuntu and I do have Nautilus lurking away in the background.

I did try one other thing that brought the problem more into focus.. 
If I logged in as guest (I should have disabled it but hadn't yet) I did not get the overlay of managers,  I didn't quite get the one I had as my proper desktop, but pretty close.

So I wend a bit further with purging, not only ~/.cache  but also .config/xfce4 and maybe a bit more..  Ok so I now have to repair my preferences etc.

But it seems to have worked.  UPDATE ** No it didn't,  on another login it's back to the same old same old.**
I've now got the desktop I expected to get when I login.

I'll check out the nautils link though,  since it might come back. (* It Did* So I'll check out that link now).

Many thanks.:D

---

### Post by Toz on 2012-03-09
Nautilus will take over and manage the desktop. If you are using xfce (xubuntu) you can disable this functionality by opening a terminal window and executing thee commands:
```

gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.gnome.desktop.background draw-backround false

```

---

### Post by trendle on 2012-03-09
Hi Toz,
You're right, Nautilus is the cuase of the problem.  I'm not sure but it might be associated with my instal of drop-box which seems to set up some nautilus based triggers.

If run start nautilus from the cli, after clearing the problem it comes back.
If I simply kill nautilus after login I get my desktop back too.
bill      1797     1  3 17:47 ?        00:00:03 nautilus
bill      2069  1920  0 17:50 pts/0    00:00:00 grep --color=auto naut
bill@xubuntu:~$ kill 1797

Now to try your gsettings suggestion.  Though gsettings doesn't seem to come with Xubuntu, I have to install it too.

thanks.

---

### Post by trendle on 2012-03-09
Many Thanks,  that's done the trick.

I'll probably go for a rant now about software getting bloated....
I thought of Nautilus as a file browser,  now it seems that they want it to take over my desktop too.  I'm a big fan of simplicity when it come to software, do the task its designed for and do it well.

Sorted.. thanks.:D

---

