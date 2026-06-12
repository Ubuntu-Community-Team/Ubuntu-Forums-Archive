---
title: "Nomachine on ubuntu 10.10 very slow"
date: 2010-11-19
forum: Desktop Environments
---

### Post by mgiammarco on 2010-11-19
Hello,
I use a lot nomachine/nx. Unfortunately with ubuntu 10.10 has become incredibly slow. 

The text has jpeg artifacts: it seems like that the new ubuntu renders the screen in a private framebuffer than it gives the Xserver the final bitmap.

So the only thing that now NX can do is to send the screen as a jpeg compressed image to client.

What can I do?

Thanks in advance for any help!

Mario Giammarco

---

### Post by alienprdkt on 2010-11-19
odd i am running nxnomachine right now on 10.10 netbook edition. Seems to be working great for me, you sure its not a bandwidth issue or resource issue? Try this...

First check your resources by 

look in all applications open System Monitor and click the resource tab.

If nothing seems rather high (on mine CPU1 4% CPU2 .09% & Memory 915.1 of 3.8 GiB) then try:

shutdown computers,

unplug modem
unplug router

-- wait 30 secs 

plug in modem
wait 30 secs
plug in router

turn on computers

---

### Post by perryjp on 2010-12-13
I don't know if this is the same issue but I'm also having nomachine problems when connecting from a windows client to my 10.10 box (that's the only thing I've tried so far).

The first time I logged in no problem, everything worked fine. I disconnected, reconnected and it took a little bit for the bar across the top of the screen to come up (20 or so seconds?) after the desktop was loaded. I tried opening the terminal and... nothing. I do see the "Starting Terminal" on the bottom but it doesn't seem to come up. Starting several programs doesn't do anything either, I tried open office word processor and I see the splash screen and then... nothing.

I'm logged into my box so I looked at top and nothing seems to be going crazy CPU or memory wise. I do see a process for the guy I just launched, ex:
> $ps aux |grep gedit
UID        PID  PPID  C STIME TTY          TIME CMD
jp        9640  0.0  0.1  19684  5384 ?        S    15:44   0:00 gedit

any ideas? I just downloaded the most recent version of nomachine on both the 10.10 box and windows last week. I've also heard of the same problem from a friend who said they got the same results with freenx.

EDIT: just to clarify, the same results with 10.10 and nomachine and then also the same problem with freenx

Thanks

---

### Post by mgiammarco on 2010-12-23
> **alienprdkt said:**
> 
shutdown computers,

unplug modem
unplug router

-- wait 30 secs 

plug in modem
wait 30 secs
plug in router

turn on computers

Sadly doing this has not helped me, but probably solving this serious bug will do:

[https://bugs.freedesktop.org/show_bug.cgi?id=32014]("https://bugs.freedesktop.org/show_bug.cgi?id=32014")

[https://bugs.freedesktop.org/show_bug.cgi?id=32014]("https://bugs.freedesktop.org/show_bug.cgi?id=32014")

---

### Post by Zoide7777 on 2011-03-23
Victory! I was able to get NX working at a good speed under Ubuntu 10.10 / Maverick thanks to Ryan Prichard's [discovery]("https://bugs.freedesktop.org/show_bug.cgi?id=32014") that the older libcairo2 from 10.04 / Lucid, 1.8.10-2ubuntu1, does not suffer from the slowness.

Steps:

[LIST=1]
[*] Open Synaptic and install libdirectfb-1.2-0.  This is one of the dependencies of the old libcairo2 and thankfully it's still available in the Maverick repositories.


[*] Go to your browser and download the old libcairo2 for [amd64]("http://launchpadlibrarian.net/39798495/libcairo2_1.8.10-2ubuntu1_amd64.deb") or [i386]("http://launchpadlibrarian.net/39798382/libcairo2_1.8.10-2ubuntu1_i386.deb").


[*] Right-click on the file from Nautilus and open it with Archive Manager.


[*] From within the archive, go to /usr/lib/ and extract the file libcairo.so.2.10800.10 .  Copy the file into your real filesystem's /usr/lib/ directory .


[*] If you wish, backup the old /usr/lib/libcairo.so and /usr/lib/libcairo.so.2 softlinks by renaming them to libcairo.so_old and libcairo.so.2_old .


[*] Recreate the softlinks, this time pointing to the old library:

ln -s libcairo.so.2.10800.10 libcairo.so
ln -s libcairo.so.2.10800.10 libcairo.so.2


[*] Close all programs and close the NX session with Terminate, not Disconnect.


[*] Create a new NX session by reconnecting to your machine.
[/LIST]

You're done!  This should get rid of the glitchy text and greatly reduce the slowness.

Many thanks to Ryan Prichard for finding the root cause!  This method is by no means a real fix but it's a very decent workaround for the time being.

Let me know if it doesn't work for you since I might have missed something in the writeup.

---

### Post by Th3BlackShadow on 2011-04-22
I also got it to work on Ubuntu 10.10 64-bit using this solution. However I was unable to get libdirectfb-1.2-0 from the synaptic package manager. Instead I downloaded it from [amd64]("http://packages.ubuntu.com/pl/lucid/amd64/libdirectfb-1.2-0/download") or use [i386]("http://packages.ubuntu.com/pl/lucid/i386/libdirectfb-1.2-0/download"). You can then install it like any other *.deb file. I was also missing the libxcb-render-util0 dependency which I was able to get from the synaptic package manager. Missing a dependency will prevent tools like gedit or gnome-terminal from starting. To find out which dependency I was missing I already had a gnome-terminal open before replacing the libcairo.so.2 link and tried to launch another gnome-terminal from that window. This gave the following error, which is easy to solve when you look at the dependency list:
```
gnome-terminal: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory
```So if you are experiencing similar troubles when trying this workaround try to get the error message like I did and see if it matches any of the following dependencies ([source]("https://launchpad.net/ubuntu/maverick/amd64/libcairo2/1.8.10-2ubuntu1")):

[LIST]
[*] libc6 (>= 2.11)
[*] libdirectfb-1.2-0
[*] libfontconfig1 (>= 2.8.0)
[*] libfreetype6 (>= 2.3.5)
[*] libpixman-1-0 (>= 0.15.16)
[*] libpng12-0 (>= 1.2.13-4)
[*] libx11-6 (>= 0)
[*] libxcb-render-util0 (>= 0.3.6)
[*] libxcb-render0 (>= 0)
[*] libxcb1 (>= 0)
[*] libxrender1
[*] zlib1g (>= 1:1.1.4)
[/LIST]
  I hope this helps anybody who has troubles with this workaround.

---

### Post by EReckase on 2011-06-14
I recently upgraded to Natty and am experiencing this same problem.  Before I jump through all the hoops, do you suspect that these steps will solve the problem on Natty as well?

---

### Post by fleckenzwerg on 2011-08-16
The trick works on Ubuntu 11.04, too.

I had this "fix" in place when I used 10.10, and cairo got updated when upgrading to 11.04. However, the old cairo libs were still in /usr/lib, so all I had to do was to symlink the old cairo libs again (the "ln -s" commands above), and everything worked.

Sad to see that the problem persists...

---

### Post by mgiammarco on 2011-12-13
I have oneiric and problem persists...
It is incredible that it seems that noone uses nomachine or x2go.

---

### Post by Diego318 on 2012-01-11
I followed Zoide7777's steps successfully, however the freenx remote desktop is still very slow.  This software should run faster than mstsc!  I used to be able to playback youtube videos almost perfectly!  This is now at the level of VNC is seems (or worse). I hope we can figure this issue out...

---

### Post by Zoide7777 on 2012-05-01
Does anyone know how to get this to work on Ubuntu 12.04 (Precise Pangolin)? I tried the old trick of installing libcairo.so.2.10800.10, but it no longer works because this version of Ubuntu also requires libcair-gobject.so.2.11000.2.

As far as I can tell, there is no libcairo-gobject.so.2.10800.10 with which to replace it.

Thanks

---

### Post by Zoide7777 on 2012-05-04
Good news! There is a test patch by Evan Broder that fixes the NX speed issue on Ubuntu 12.04.  It might also work on older versions:

To install it:


1) Add Evan's repository to your list of sources:

sudo add-apt-repository ppa:broder/ubuntu-tests


2) Update your package list:

sudo apt-get update


3) Upgrade your packages:
 
sudo apt-get upgrade


4) Close all of your programs / terminals in the NX session, and close the session with Terminate instead of Suspend.  Just to be sure, you can kill the nxagent process manually from a terminal via SSH.

 
5) Create a new NX session and re-open your programs.  You should see a significant speed boost.


I hope this helps ;)

---

### Post by TheCan on 2012-05-08
Hi Ziode,

thanks for pointing this out. Yesterday I installed the packages from broder's PPA but unfortunately nothing got better. Did you really try this on 12.04? If yes: With amd64 or i386? And which NX versions are you using?

---

### Post by Zoide7777 on 2012-05-09
> **TheCan said:**
> Hi Ziode,

thanks for pointing this out. Yesterday I installed the packages from broder's PPA but unfortunately nothing got better. Did you really try this on 12.04? If yes: With amd64 or i386? And which NX versions are you using?

Yes, I tried it with Ubuntu 12.04 on amd64.  I'm using NX 3.5.x for both the client and the server.  The difference was pretty clear in Gnome Terminal, Eclipse, and Firefox.  Chrome remained the same as it seems to have been unaffected by the bug.

---

### Post by TheCan on 2012-05-09
That's strange then, indeed. I also tried with NX 3.5 and 12.04 on amd64. I experienced this slowness in KDE though. Will retry with Gnome or LXDE and broder's PPA - but of course it's not a solution for me if the fix does only work with GTK and not with QT/KDE...

---

### Post by Zoide7777 on 2012-05-09
> **TheCan said:**
> That's strange then, indeed. I also tried with NX 3.5 and 12.04 on amd64. I experienced this slowness in KDE though. Will retry with Gnome or LXDE and broder's PPA - but of course it's not a solution for me if the fix does only work with GTK and not with QT/KDE...

Maybe that's the reason. I'm running xfce4. Let us know how it turns out.

---

### Post by Diego318 on 2012-05-29
:mad::mad::mad::mad::mad::mad::mad:

---

### Post by Diego318 on 2012-06-07
So nobody's figured this out for KDE users?

---

### Post by Zoide7777 on 2012-06-18
Good news!

The NoMachine (NX) people have a new version out that fixes the bug:

[http://www.nomachine.com/tr/view.php?id=TR01J02646]("http://www.nomachine.com/tr/view.php?id=TR01J02646")

---

### Post by TheCan on 2012-06-24
Zoide7777: Can you confirm the fix? I tried on 12.04 with a USB live system and did not see any significant improvements in KDE.

---

### Post by Zoide7777 on 2012-06-25
> **TheCan said:**
> Zoide7777: Can you confirm the fix? I tried on 12.04 with a USB live system and did not see any significant improvements in KDE.

I'm not a Ubuntu / Nomachine developer, so I can't unequivocally state that the issue has been fixed.

However, it seemed to work for me after following these steps:

1)	Remove the PPA from the previous workaround:

$ sudo add-apt-repository --remove ppa:broder/ubuntu-tests

2)	Download and install the new NX packages following the instructions at:
[http://www.nomachine.com/download-package.php?Prod_Id=3776](http://www.nomachine.com/download-package.php?Prod_Id=3776)

3)	Close all your programs on the remote session and Kill it (not Resume) from your Windows client.

If you killed it successfully you won&#8217;t see any nxssh, nxnode, or nxagent processes on your Linux machine.

4)	Just to be safe, restart the nxserver:

$ sudo /etc/init.d/nxserver restart

5)	Create a new NX session by connecting to your server again from the Windows client.

I hope this helps.

---

### Post by TheCan on 2012-07-28
Thanks for pointing this out Zoide7777. Actually I gave Ubuntu 12.04 another try with a fresh installation and while the performance in GTK apps was quite adequate, the problem with the bad performance in QT apps was still the same issue, even with the updated packages from NoMachine. If you compare scrolling i.e. between kate and gedit you can see that gedit is at least 5x faster with redrawing the content over the NX connection!

I spent many hours today googling around and trying numerous things until I found the working solution! And here it is:

First, you have to install the "kcm-qt-graphicssystem" package:

[https://launchpad.net/ubuntu/+source/kcm-qt-graphicssystem/](https://launchpad.net/ubuntu/+source/kcm-qt-graphicssystem/)

Now you can try the following for a speed comparison:

```
QT_GRAPHICSSYSTEM=native kate
```

versus:

```
kate
```

Load a lengthy text file into file and scroll around. You should be able to notice a huge speed improvement! The reason behind this is that the kde or kubuntu folks switched to the "raster" renderer as default with QT 4.7 (so I guess Ubuntu 11.10 was also affected), but NX seems to deliver a much better performance with this "native" rendering.

To make this change permament you can create the file

```
/home/username/.kde/env/qt-graphicssystem.sh
```

and put the following content in there:

```
export QT_GRAPHICSSYSTEM=native
```

(thanks to this posting for the instructions: [http://forum.kde.org/viewtopic.php?f=66&t=90821](http://forum.kde.org/viewtopic.php?f=66&t=90821))

Now when you terminate your NX session and start a new one the performance leven should be the same as with running a session in 10.04.

The only open issue for users of 12.04 + KDE + NX is the crashing KWin Manager:

[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/985202](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/985202)

Instead of the workaround posted in this bug report I rather recommend switchting to an alternative window manager like openbox until the issue gets resolved upstream.

---

### Post by Zoide7777 on 2012-08-02
Does anyone have a workaround for the Google Chrome slowness issue with NX?

There is a bug entered in Google's tracker but it's not doing much good ([http://code.google.com/p/chromium/issues/detail?id=28544]("http://code.google.com/p/chromium/issues/detail?id=28544")).

---

### Post by TheCan on 2012-08-03
The bug seems pretty old, although people seem still to be affected by it. I am running Chromium with NX under 10.04 and it works pretty okay for me. Of course you notice this flicker, but if you are used to scroll through pages using pgup/pgdown you don't really notice much of a difference when compared with Firefox.

This issue discussed here before the latest fix by Nomachine and the regular performance in QT 4.8 apps is WAY more annoying than this rather minor Chrome problem.

Another issue is the performance in Java Swing apps, especially Netbeans is pretty awful. But I guess this happens with all applications which render their content as Images. Probably the new NX4 with its image streaming approach will do better in such cases.

---

