---
title: "[SOLVED] Getting started with kde. Im lost"
date: 2008-11-09
forum: Desktop Environments
---

### Post by ztrange on 2008-11-09
Hi

Just installed kubuntu-desktop to test kde and loved it.

Im just having a little trouble isolating gnome and kde, I mean, Im not sure if I like all the kde or gnome specific apps but would like to leave them in their desktop environments and use the kde ones in kde and de gnome ones in gnome.

Well, I feel kind of lost, I really dont have much time and want to use kde but there are some things that I cant get to figure out.

In kde tray I get the gnome network manager and cant get rid of it, Im also afraid taht i kill it in kde and it get killed in gnome...

The screenlets that live in my widget layer in gnome appear all over the kde desktop

In kde everything looks so big, my screen resolution is fine, but menues, buttons and everything is too big, I would like to change that.

The main issue is that i get lost between kde and gnome apps and dont know what can I configure and where. 

Ive been looing for some getting started kde guide that can help me to quick learn kde and use it for the next week and on but havent suceeded.

Well, any help will be appreciated.

---

### Post by aged hippy on 2008-11-09
How did you install it, with Adept, or via a console command (sudo aptget, etc.) ?

---

### Post by stitchmysmile93 on 2008-11-09
You can get knetworkmanager sudo apt-get install knetworkmanager that is what I do when I install kde.  And there are a lot of apps you can get for kde and gnome that do basically the samething.

---

### Post by ztrange on 2008-11-09
> **aged hippy said:**
> How did you install it, with Adept, or via a console command (sudo aptget, etc.) ?

Hi, thanks for your answer, I installed it with

sudo aptitude install kubuntu-desktop

> You can get knetworkmanager sudo apt-get install knetworkmanager that is what I do when I install kde. And there are a lot of apps you can get for kde and gnome that do basically the samething.

Hi, well, Im not looking for something to manage netwarks, I would like to be able to use both desktop systems for a while (while I can get used to the new one and decide if I really want to keep it) and be able to use them perfectly isolated, not just the network managers that both of them (the kde and the gnome tray icons) appear in both tray bars, but to be able to tell kde that the screenlets should stay in gnome and that each desktop manager has its own applications (specifically the ones that modify setting specific to each of the systems).

Also, isolate the window managers kwin and compiz

Thanks

---

### Post by benerivo on 2008-11-09
Have you looked in the kde4 system settings? In there is a section called something like autostart, and when i use kde4, i used it to disable gnome utilities for kde.
[IMG]http://polishlinux.org/reviews/kde-4-rev-790000/2a6f3940bc59bc460b3a9add408393cf.jpg[/IMG]

---

### Post by aged hippy on 2008-11-09
> **ztrange said:**
> Hi, thanks for your answer, I installed it with

sudo aptitude install kubuntu-desktop



That is the safest way to install it, it can be easily removed if you don't like it. :)

It is safe to use the <Menu Editor> in KDE to edit the menu (right-click on the K Menu ->Menu Editor) and remove what you don't want.... it won't affect the Gnome installation at all, and you can safely log in to Gnome and do the same there with the KDE applications there which you don't need.

---

### Post by ztrange on 2008-11-10
Well, now Im starting to get a hang of it... 

Tanks to all you for your help, I disabled a lot of the autostart programs, and edited the menu a little, though I still have to clean it up a little. I still have 3 things that I dont like:

Is there a way to make thing a litle smaller, I man, the window controls, the taskbar, the fonts, everything... My laptop has a 13" screen and I cant waste my precious available space.

i havent been able to find where to configure the desktop effects that are provided by Kwin.

The network manager applet from gnome is starting aven when I dont have any of the available applications from autostart checked, I dont know how to close it because it doesn't have a close option, and Im affraid of breaking it because I use it in gnome. As a workaround, Im leaving it as I disabled de Knetwork manager so I am using only one... Im wondering if maybe it is always on by default in kubuntu...


And lat but no least, Songbird is complainig that it cant find gstreamer... It works fine in gnome but not in kde, maybe Im missing something, but i love songbird, also could not find an option to change the gstreamer in songbid for something like kstreamer...

---

### Post by gsmlinux on 2008-11-11
In KDE use the program System Settings, select the tab "General", and click on Appearance. Here you can change the fonts, themes etc. used by KDE without effecting Gnome applications when ran from the Gnome desktop.

---

### Post by Marsolin on 2008-11-11
> **ztrange said:**
> Well, now Im starting to get a hang of it... 

Is there a way to make thing a litle smaller, I man, the window controls, the taskbar, the fonts, everything... My laptop has a 13" screen and I cant waste my precious available space.

i havent been able to find where to configure the desktop effects that are provided by Kwin.

The network manager applet from gnome is starting aven when I dont have any of the available applications from autostart checked, I dont know how to close it because it doesn't have a close option, and Im affraid of breaking it because I use it in gnome. As a workaround, Im leaving it as I disabled de Knetwork manager so I am using only one... Im wondering if maybe it is always on by default in kubuntu...


And lat but no least, Songbird is complainig that it cant find gstreamer... It works fine in gnome but not in kde, maybe Im missing something, but i love songbird, also could not find an option to change the gstreamer in songbid for something like kstreamer...

I have the same font issue.  I force fonts to 96 DPI to fix it.  You can do that on the same page that you can change font sizes in System Settings.

Desktop Effects are configured in System Settings by clicking the Desktop icon.  It should be the first option in the list.

Killing an app in KDE won't hurt it in Gnome.

I haven't tried Songbird, but the GStreamer packages are the same for any desktop environment.  You could try opening System Settings, Advanced tab, and selecting Solid.  GStreamer should be an option there if it is installed.  The default in Xine.

---

### Post by purplepaint on 2008-11-15
I, too, have recently installed the kubuntu-desktop packages in Interpid (and I really like KDE 4.1 - it's not perfect but it looks like there's loads planned for the future), and I'd love a way to keep GNOME's Network Manager Applet from starting up when I log in - it keeps asking for my password, and when I enter it, it connects to my wireless network and KDE's equivalent network manager says it's connected as well.  If I keep denying the GNOME one when it asks for my password, I get KDE's one asking me for my WEP key which I have to enter (if I just enter my password, I don't need to enter the key).  I'd really prefer just to have the KDE one connect my laptop automatically since the GNOME one stands out in KDE.

---

### Post by awakatanka on 2008-11-15
A good start is also the kde forum. There you have some tutorials like this one for the panel [http://forum.kde.org/showthread.php?tid=6902](http://forum.kde.org/showthread.php?tid=6902) and you can also go to kde userbase for more/others [http://userbase.kde.org/Tutorials](http://userbase.kde.org/Tutorials)

Here is some candy we going to expect in kde 4.2 [http://introducingkde4.blogspot.com/2008_11_09_archive.html](http://introducingkde4.blogspot.com/2008_11_09_archive.html)

---

### Post by purplepaint on 2008-11-15
Actually, my issue with the Network Manager Applet seems to be a known problem:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/268803](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/268803)

---

### Post by ztrange on 2008-12-25
Just found a good guide for KDE 4.2. I leave it here despite I no longer trying KDE 4; it produced too many conflicts with my Gnome... I reformated my pc and installed Intrepid form scratch after updating my BIOS and everything is working fine out of the box.

Here is the guide:
[http://ubuntulife.wordpress.com/2008/07/16/la-guia-imprescindible-para-kde-41/](http://ubuntulife.wordpress.com/2008/07/16/la-guia-imprescindible-para-kde-41/)

---

