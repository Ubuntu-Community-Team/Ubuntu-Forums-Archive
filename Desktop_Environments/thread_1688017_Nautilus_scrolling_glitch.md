---
title: "Nautilus scrolling glitch"
date: 2011-02-14
forum: Desktop Environments
---

### Post by MichaelGld on 2011-02-14
Whenever I use Nautilus to look at a file list (detail view) I encounter problems when I scroll up or down through the list. The lines of text at the top or bottom of the window scrunch up (or down) making the text unreadable. If I move the mouse up or down without clicking, the text unravels, becoming clear again.  Look at the top part of the image I'm attaching to see. What's going on and how can I fix it?

Thanks

---

### Post by Krytarik on 2011-02-14
You are using Nautilus Elementary, right?!

I've exact the same issue when running NE, but no issues with vanilla Nautilus.
I didn't search for solution so far however, because I can live with the downsides of the latter.

What video card/driver setup do you have?

Mine is a pretty old Nvidia card, GeForce4 Ti 4200, running proprietary driver version 96, installed via "Hardware Drivers".

---

### Post by MichaelGld on 2011-02-15
> **Krytarik said:**
> You are using Nautilus Elementary, right?!

I've exact the same issue when running NE, but no issues with vanilla Nautilus.
I didn't search for solution so far however, because I can live with the downsides of the latter.

What video card/driver setup do you have?

Mine is a pretty old Nvidia card, GeForce4 Ti 4200, running proprietary driver version 96, installed via "Hardware Drivers".

I never heard of Nautilus Elementary, I'm just using what came with Ubuntu. Help>about says, "Nautilus 2.31.1".

My video card is a GeForce 7300 GS with 512MB.  Samsung Syncmaster monitor at 1680x 1050.  I am using the "recommended" video driver.

---

### Post by Krytarik on 2011-02-15
> **MichaelGld said:**
> I never heard of Nautilus Elementary, I'm just using what came with Ubuntu. Help>about says, "Nautilus 2.31.1".

My video card is a GeForce 7300 GS with 512MB.  Samsung Syncmaster monitor at 1680x 1050.  I am using the "recommended" video driver.
If you are indeed running Lucid, you should have version 2.30.1, like my "About" says.
```
krytarik@krytarik-desktop:~$ dpkg -l|grep nautilus
ii  libnautilus-extension1                1:2.30.1-0ubuntu1.1                             libraries for nautilus components - runtime 
[B]ii  nautilus                              1:2.30.1-0ubuntu1.1                             file manager and graphical shell for GNOME
ii  nautilus-data                         1:2.30.1-0ubuntu1.1                             data files for nautilus
[/B]ii  nautilus-sendto                       2.28.4-0ubuntu1                                 integrates Evolution and Pidgin into the Nau
ii  nautilus-share                        0.7.2-12build1                                  Nautilus extension to share folder using Sam
krytarik@krytarik-desktop:~$ 

```Whereas Nautilus Elementary is indeed the version you mentioned:
[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa?field.series_filter=lucid]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa?field.series_filter=lucid")

You somehow installed it. Maybe as a suggestion by a theme install?

However, if you want to revert to vanilla Nautilus, you have to "downgrade" the respective packages, I recommend using "ppa-purge" for that:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa

```
After that restart Nautilus with:
```
killall nautilus
```

---

### Post by mikewhatever on 2011-02-15
> **MichaelGld said:**
> I never heard of Nautilus Elementary, I'm just using what came with Ubuntu. Help>about says, "Nautilus 2.31.1".

My video card is a GeForce 7300 GS with 512MB.  Samsung Syncmaster monitor at 1680x 1050.  I am using the "recommended" video driver.

Try switching to the default theme just to see if the problem persists.

---

### Post by MichaelGld on 2011-02-15
> **Krytarik said:**
> If you are indeed running Lucid, you should have version 2.30.1, like my "About" says.
```
krytarik@krytarik-desktop:~$ dpkg -l|grep nautilus
ii  libnautilus-extension1                1:2.30.1-0ubuntu1.1                             libraries for nautilus components - runtime 
[B]ii  nautilus                              1:2.30.1-0ubuntu1.1                             file manager and graphical shell for GNOME
ii  nautilus-data                         1:2.30.1-0ubuntu1.1                             data files for nautilus
[/B]ii  nautilus-sendto                       2.28.4-0ubuntu1                                 integrates Evolution and Pidgin into the Nau
ii  nautilus-share                        0.7.2-12build1                                  Nautilus extension to share folder using Sam
krytarik@krytarik-desktop:~$ 

```Whereas Nautilus Elementary is indeed the version you mentioned:
[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa?field.series_filter=lucid]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa?field.series_filter=lucid")

You somehow installed it. Maybe as a suggestion by a theme install?

However, if you want to revert to vanilla Nautilus, you have to "downgrade" the respective packages, I recommend using "ppa-purge" for that:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa

```After that restart Nautilus with:
```
killall nautilus
```
Looks like something else is broken:
```
mike@mike-desktop:~$ sudo apt-get install ppa-purge
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ppa-purge
mike@mike-desktop:~$
```

---

### Post by Krytarik on 2011-02-15
> **MichaelGld said:**
> Looks like something else is broken:
```
mike@mike-desktop:~$ sudo apt-get install ppa-purge
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ppa-purge
mike@mike-desktop:~$
```
Sorry, I was mistaken in believing that "ppa-purge" also made into the official Lucid repos.

Then just do it the manual way, offers more control anyways:
[http://ubuntuforums.org/showthread.php?p=10385434#post10385434](http://ubuntuforums.org/showthread.php?p=10385434#post10385434)

If you really want to use "ppa-purge" or for later purposes, you may install it via the PPA of Ubuntu-X-Swat, but disable it after the install, otherwise your video driver also gets upgraded!:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by MichaelGld on 2011-02-16
> **mikewhatever said:**
> Try switching to the default theme just to see if the problem persists.

I can't find a theme named "default". Is there another name for it? If it's somehow been deleted, how do I get it back?

---

### Post by Krytarik on 2011-02-16
> **MichaelGld said:**
> I can't find a theme named "default". Is there another name for it? If it's somehow been deleted, how do I get it back?
He means "Ambiance" or one of the other pre-installed themes. But I doubt if it helps, I had that issue exactly with "Ambiance". Just try it.

---

