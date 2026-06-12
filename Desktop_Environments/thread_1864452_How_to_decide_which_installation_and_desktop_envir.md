---
title: "How to decide which installation and desktop environment to go with?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by MarjaE on 2011-10-19
I had a lot of trouble with Unity and stuck with Gnome 2/Classic in 11.04. But after trying the live cd I decided to switch to Xubuntu for 11.10. It worked well on the live cd but has worked spectacularly badly after installation, not to mention the bugs during installation.

After this fiasco I'm planning to back up what little work I've accomplished since installing Xubuntu, and switch to another system, possibly Ubuntu 10.10.

So can anyone offer advice on what to look for, what to do, and what to avoid when deciding the best installation and desktop environment?

A good comparison list would be nice, but I'm going to discuss some of my needs and concerns.

I decided to switch from Ubuntu 11.04 and not consider Kubuntu 11.10 because of all the freezes and delays I'd encountered in Gnome 2/Classic in Ubuntu 11.04. I understood that Gnome and Kubuntu have the most processor and memory demands, while in theory Lxde and Xfce have the least.

I had a lot of trouble with the Xubuntu 11.10 install disk because it demanded a network connection and I couldn't set up a network connection until after I had completed the installation. So I would strongly prefer a version which doesn't present these Catch-22s. As it is, this catch-22 may be one reason the system clock is wrong and can't be rest.

I really like the window switching on Gnome 2/Classic and Xfce. I haven't found the same feature in Unity, and understand it's absent from Gnome 3.

I really dislike desktop animations, visible-on-mousover features, and the like. All of these are likely to stutter, and some of these are likely to make one accidentally hit the visible-on-mouseover feature when trying to use the window behind it, or accidentally hit the window behind when trying to use the visible-on-mouseover feature.

I have a lot of trouble with applications in Xubuntu. Some of the ones I need and I have installed aren't even showing up in the Applications menu.

I had a lot of trouble with my touchpad in every system I've used. I had to install a special patch to fix it, and I had to install additional software because Xubuntu has no touchpad preferences.

P.S. Also I do most of my work in LibreOffice, and it's been glitching since this install.

---

### Post by meatytaco on 2011-10-19
Recently, I've tried Ubuntu 11.04 with the ubuntu desktop, lxde desktop and xfce desktop, xubuntu, and Linux mint 11 using the xfce desktop and the Gnome desktop.  As far as installation goes, to me they were pretty much the same minus Linux mint which connected to my wireless during installation (I'm on a laptop and not sure why the ubuntus didn't) an so far the only problem I've had with Mint is my volume buttons above my keyboard not working in xfce. Not terrible, but kind of annoying. Running the Gnome desktop on Linux mint fixes that but uses more of my RAM :/. I'd suggest making a live cd/USB of whatever distro you want (I'd recommend mint :P) an try it out. Btw, mint is basically Ubuntu. So if you have any issues with it, fixes from here generally work (although not always) Just giving my input :)

Edit: as far as your install bugs, I'm not sure what would be causing that. Maybe if you're on an older comp, you could try Lubuntu?

---

### Post by MarjaE on 2011-10-19
I made a live cd of Xubuntu. For whatever reason, the live cd seemed to work wonderfully, but the installed version runs into all kinds of bugs.

At least one of the bugs is that the live cd insisted on having a network connection in order to install. I had to create the alternate live cd and use that, and cancel and skip certain steps, in order to install. I think the cancellation may have caused at least one of the bugs on my system.

---

### Post by meatytaco on 2011-10-19
That's really strange to me, I set up my installs on a windows comp by downloading the iso and putting it on a USB with the Linux live USB creator. All but mint wouldn't connect to wifi during installation, but once I got it installed (it didn't demand to be connected for the install to work) I could update and I was fine. As far as the live cd working but the install not so much, maybe it has something to do with your hard drive speed. Cause a live cd I believe runs the OS off your RAM, which is always much faster than a hard drive anyway. But if your hard drive has a low speed, I could see where that would at the very least slow boot up considerably. You could get a big thumb drive and just run your OS live with persistence :P but really, I haven't had the buginess problem an xubuntu ran pretty well for me, so I can't honestly give you any more suggestion than that o.o Someone will come along with a better plan :D

---

### Post by MarjaE on 2011-10-19
I've occasionally had Xubuntu freeze, and once had it crash, but speed hasn't been my big problem; it's missing preferences, applications not running or not showing up, applications developing new bugs, etc. that has been my problem.

When I look for a needed feature, all too often it's not there, or it's only there after installing additional software, or after using the command line [but since I've had so many bugs on this installation, I'm staying away from anything too technical on this installation]. When I install needed software, at times it doesn't show up in the Applications menu.

---

### Post by fantab on 2011-10-19
> **MarjaE said:**
> So can anyone offer advice on what to look for, what to do, and what to avoid when deciding the best installation and desktop environment?

A good comparison list would be nice, but I'm going to discuss some of my needs and concerns.

I had a lot of trouble with the Xubuntu 11.10 install disk because it demanded a network connection and I couldn't set up a network connection until after I had completed the installation. 

I had a lot of trouble with my touchpad in every system I've used. I had to install a special patch to fix it, and I had to install additional software because Xubuntu has no touchpad preferences.

P.S. Also I do most of my work in LibreOffice, and it's been glitching since this install.

First of all, if your desktop or laptop is relatively new and has good CPU and Memory then almost any Desktop Environment (DE) will do. If not, then XFCE and LXDE are lighter on system resources and are mostly recommended for older systems. Check out these links if you haven't already: [Link1]("http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce"), [Link2]("https://wiki.archlinux.org/index.php/Desktop_Environment") and [Link3]("http://www.internetling.com/2008/07/16/the-big-x-window-manager-guide-with-screenshots/"). Also please [read this]("http://linux.oneandoneis2.org/LNW.htm").

When picking up a Linux Distro, it is better to know what their default DE is. For instance Unity is default to Ubuntu, Gnome3 is default to Fedora, KDE is default to OpneSUSE and so on. The logic is most of the development work is primarily done on default and later hacked and patched to suit other flavors. So in a way, a Distro's default DE has to be the best it has to offer. 

If you are after stability in a distro I suggest you take a look at [Debian]("http://www.debian.org/releases/stable/") or [CentOS]("http://www.centos.org/"). One should not also discount the support factor, here Ubuntu stands out. If you are after the latest then I suggest Fedora or Ubuntu. Linux Mint is based on Ubuntu they have not yet migrated to either Unity or GnomeShell, have look at[ LinuxMint 11-katya]("http://www.linuxmint.com/"), and also try [LinuxMint Debian Edition]("http://www.linuxmint.com/download_lmde.php") (LMDE) its a rolling distro based on Debian Testing and quite stable. It comes in flavors of Gnome and XFCE.

I am not really aware of touchpad suitable distros.

The Xubuntu may have "demanded network connection" because you may have opted to install updates too with primary installation. If you don't check that then it wont. 

Since you do "most of your work in LibreOffice"... Almost every major distro ships LibreOffice by default so that should not be any issue.

I have a relatively new desktop and Ubuntu 11.10 with Unity works beautifully with latest updates most of the initial glitches are taken care of. I also use Fedora with Gnome-Shell its works like a charm. I too work mostly with LibreOffice and it works without any glitch on both distros.

I hope this information helps. 
Happy Hunting.

---

### Post by MarjaE on 2011-10-19
I get the impression - from the lack of touchpad support, and the fact I had to install three different things to disable the touchpad - that Xubuntu isn't appropriate for laptops. [It's an issue with Xfce 4.8 that is supposed to be fixed by Xfce 4.10.] I am downloading Kubuntu right now.

But I am nervous about judging anything by the live cd, precisely because I loved the Xubuntu live cd and hate the Xubuntu installation I ended up with.

P.S. I don't know how to find the RAM and CPU speed for this computer.

P.P.S. I don't know Windows. I switched from the Mac.

---

### Post by vasa1 on 2011-10-19
> **MarjaE said:**
> ... the live cd insisted on having a network connection in order to install. ...

They should make it clear. More people, especially where the internet isn't too consistent, may then prefer, correctly, to go for the alternate CD.

---

### Post by iamnotthemessiah on 2011-10-19
i switched to xubuntu because it can mimic gnome2 almost perfectly. i didnt have network connection during installation either but it never asked for it or caused trouble. had a prob with the install cd but installing from usb worked perfectly, no crashes.

---

### Post by fantab on 2011-10-20
> **MarjaE said:**
> 
But I am nervous about judging anything by the live cd, precisely because I loved the Xubuntu live cd and hate the Xubuntu installation I ended up with.

P.S. I don't know how to find the RAM and CPU speed for this computer.

P.P.S. I don't know Windows. I switched from the Mac.

You can find RAM and CPU speed from LiveCD... find **System Monitor** from the DASH or APPLICATIONS. It will show you all the necessary details.

Initially when I was trying out LINUX I made **three **10GB ext4 Partitions and **one** swap. I installed the Linux Distros I wished to try on these Partitions. LiveCD is very slow compared to actual installation. Try KDE on One, on another you can have Gnome, on yet another DE on another partition. Install and run your most used application on all of them and see the performance. I tried and tested until I found my comfort and flavor.

---

