---
title: "I upgraded to 8.04 and now I got no sound"
date: 2008-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsdieorksw on 2008-05-31
I recently finally got around to upgrading to Hardy Heron from Gutsy Gibbon on my new Dell laptop but now my audio doesn't work. Whenever I try to turn up the volume I get this error message:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


It worked just fine with 7.10 so I know I have the right equipment. 

I tried to do a search on the Synaptic Package Manager for the plugins but there are a large number of gstreamer plugins available and I wanted to see which one would solve my problem. Any help would be greately appreciated! Thanks guys!

---

### Post by Orion2000za on 2008-06-02
> **jsdieorksw said:**
> I recently finally got around to upgrading to Hardy Heron from Gutsy Gibbon on my new Dell laptop but now my audio doesn't work. Whenever I try to turn up the volume I get this error message:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


It worked just fine with 7.10 so I know I have the right equipment. 

I tried to do a search on the Synaptic Package Manager for the plugins but there are a large number of gstreamer plugins available and I wanted to see which one would solve my problem. Any help would be greately appreciated! Thanks guys!

check out this link from Dell Linux Wiki:
[http://tinyurl.com/4w8gqq](http://tinyurl.com/4w8gqq)

---

### Post by jsdieorksw on 2008-06-16
I checked out this link and it doesn't seem to work.  I copy and paste the first command and I get an error message. 

dpkg - warning: ignoring request to remove hsfmodem, only the config files of which are on the system.  Use --purge to remove them too. 

I don't want to mess anything up, any advice on what I should do next? Thanks

---

### Post by bryncoles on 2008-06-17
hallo. i foolishly started a new thread on this self same topic... im considering reporting myself to the mods about it!

anyway - i have the same issue. no sound after the upgrade, ubuntu tells me im missing a gstreamer plugin and the instructions on the dell website leave me with 

```
bryn@dell-desktop:~$ sudo dpkg -r hsfmodem
[sudo] password for bryn: 
(Reading database ... 110034 files and directories currently installed.)
Removing hsfmodem ...
bryn@dell-desktop:~$ sudo dpkg -r linux-backports-modules-2.6.22-14-generic
(Reading database ... 109903 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
bryn@dell-desktop:~$ cd /lib/modules/'uname -r'/ubuntu/sound/alsa-driver/pci/hda
bash: cd: /lib/modules/uname -r/ubuntu/sound/alsa-driver/pci/hda: No such file or directory
```

*edit* 

i solved my issue by going back to the dell page and cutting and pasting, rather than typing out. red face-me! sorry people!

---

### Post by VGF on 2008-06-17
I've this problem, also, and I'm struggling to figure out how I'm actually supposed to fix it.  I've tried entering thos commands in the terminal only to get no progress.

---

### Post by jsdieorksw on 2008-06-18
Solved! I figured it out using the link that was provided, thanks!

---

### Post by maxim9 on 2008-06-19
I have Dell M1330 and upgraded to Ubuntu 8.04. 

I performed the steps in the link but sound is still not working. 

When I ran the commands:

```
$ cd /lib/modules/2.6.24-18-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
```

I already had the right file name. 

```
$ cd /lib/modules/2.6.24-17-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko
```

I don't have the above files

```
$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot
```

worked OK. 

Anything else I should try?

---

### Post by stchman on 2008-06-19
> **jsdieorksw said:**
> I recently finally got around to upgrading to Hardy Heron from Gutsy Gibbon on my new Dell laptop but now my audio doesn't work. Whenever I try to turn up the volume I get this error message:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


It worked just fine with 7.10 so I know I have the right equipment. 

I tried to do a search on the Synaptic Package Manager for the plugins but there are a large number of gstreamer plugins available and I wanted to see which one would solve my problem. Any help would be greately appreciated! Thanks guys!

Do a clean install, upgrade is not as good and usually a lot slower.

Also try the LiveCD to see if volume works.

---

### Post by swordsmith on 2008-06-19
That happened to me as well, I have a Latitude D830.
Hardy was just plain painful for me, no sound, networking was really bad and for some reason much slower. I solved the problem by doing a complete fresh install of Gutsy, everything works perfectly now. WHo needs Hardy anyways!

---

### Post by oscarFrance on 2008-07-26
So? Everyone solved it's sound problem? I can give you some help if you want.

In my case, I had the same symptoms "Gstreams error" (due to incorrect snd-hda-intel loading). I solved it by following carefully the following link:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

Best regards,
Oscar FRANCOIS

---

### Post by lynchman on 2008-08-02
The dell site instructions worked for me as well on my 1420n.  Most of the steps I couldn't do since I'm running a newer kernel, but the last three steps worked and after reboot my sound was back:

```
$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot
```

I was previously getting the 'gstreamer' errors that others had as well.

---

