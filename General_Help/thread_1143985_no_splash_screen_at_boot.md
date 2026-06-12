---
title: "no splash screen at boot"
date: 2009-04-30
forum: General Help
---

### Post by champdood on 2009-04-30
Hi folks,

I recently upgraded to Ubuntu 9.04 from 8.10 and to my dismay my poop coloured splash screen is gone! What's even worse though is that I get a couple of seconds of the new splash screen, then it drops into the text status display (with the "Ubuntu is doing this....                   [OK]" list of stuff). It's like with 8.10 where the coloured bar would bounce back and forth a couple of times then start to fill the bar when it's loading, except the fill part is dropping to the system text instead.

A quick read on the forums suggested I probably didn't have "quiet splash" set in /boot/grub/menu.lst, however a quick check suggests that's fine (also, it starts in the splash screen, then drops out)

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7be3f4db-bc26-4187-8dd4-6d720279fc16 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```

Anyone have an idea on what could be going wrong? It's on an Acer Travelmate 6410, with the Intel 945 chipset (GMA950 graphics, which has given me enough trouble with Ubuntu already, so I'd like to blame it). Not a huge issue, but it's a production machine, so when something's wrong I tend to assume the worst and that it might be caused by a bigger problem :)

---

### Post by dcstar on 2009-04-30
> **champdood said:**
> Hi folks,

I recently upgraded to Ubuntu 9.04 from 8.10 and to my dismay my poop coloured splash screen is gone! What's even worse though is that I get a couple of seconds of the new splash screen, then it drops into the text status display (with the "Ubuntu is doing this....                   [OK]" list of stuff). It's like with 8.10 where the coloured bar would bounce back and forth a couple of times then start to fill the bar when it's loading, except the fill part is dropping to the system text instead.

A quick read on the forums suggested I probably didn't have "quiet splash" set in /boot/grub/menu.lst, however a quick check suggests that's fine (also, it starts in the splash screen, then drops out)

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7be3f4db-bc26-4187-8dd4-6d720279fc16 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```

Anyone have an idea on what could be going wrong? It's on an Acer Travelmate 6410, with the Intel 945 chipset (GMA950 graphics, which has given me enough trouble with Ubuntu already, so I'd like to blame it). Not a huge issue, but it's a production machine, so when something's wrong I tend to assume the worst and that it might be caused by a bigger problem :)

```
sudo update-initramfs -u all
```

---

### Post by spectre51 on 2009-05-03
I have the same problem except I never see the new splash screen at all it just goes straight into the text.

```
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=118e7d19-808f-4bd4-85f8-d93f914592ce ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=118e7d19-808f-4bd4-85f8-d93f914592ce ro  single
initrd /boot/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

```


I tried that command you posted but it didn't change anything.  Any other ideas?  I didn't have this issue until I upgraded 8.10 to the 2.6.28-11 kernel and then after I upgraded to 9.04 it stayed the same way.

---

### Post by champdood on 2009-05-04
Thanks for the help, but unfortunately II also had no luck updating initramfs. I also have no idea how to look into the one for 9.04, so I'm not sure how to figure out what it should be doing and whether it's doing that or not :)

anyone else have any suggestions?

---

### Post by spectre51 on 2009-05-04
Champdood just got mine working.  Open Add/Remove from your applications menu and install a program called startup manager.  Once that is installed open it and click on the Appearance tab and at the bottom there should be a Usplash Themes option.  Select your usplash theme and hit okay.  

When I first opened it there was nothing selected for the theme.  I chose usplash-theme-ubuntu and its working again.  Worth a try.  Let me know if if doesn't work.

---

### Post by champdood on 2009-05-07
> **spectre51 said:**
> Champdood just got mine working.  Open Add/Remove from your applications menu and install a program called startup manager.  Once that is installed open it and click on the Appearance tab and at the bottom there should be a Usplash Themes option.  Select your usplash theme and hit okay.  

When I first opened it there was nothing selected for the theme.  I chose usplash-theme-ubuntu and its working again.  Worth a try.  Let me know if if doesn't work.

Unfortunately I had no luck with this either, the theme was already selected when I opened the application, saving and rebooting after installing this app didn't achieve anything either :/

Thanks for your help anyway, much appreciated!

---

### Post by spectre51 on 2009-05-07
Did you try changing the theme to a different one?

---

### Post by champdood on 2009-05-08
> **spectre51 said:**
> Did you try changing the theme to a different one?

 There's no other ones listed to use. I'm a little hesitant about downloading a different one to run instead, I'm not a big fan of running unknown things while booting :)

---

### Post by spectre51 on 2009-05-08
Okay try these commands.  I ran these then used that program to select the usplash theme:
```

sudo dpkg-reconfigure -phigh usplash
```

then 
```

sudo apt-get install usplash*
```

Then after that is when I used start-up manager to select my usplash theme.  After that it was working.

---

### Post by spectre51 on 2009-05-08
Also found this on another page talking about splash screen issues:

Usplash:
It's also called bootsplash sometimes. That's what Ubuntu has enabled by default giving you Ubuntu's circle with an orange progress bar beneath. If you think the usplash itself is missing on your system do


```
ls -la /usr/lib/usplash/
```

There should at least be a file called usplash-theme-ubuntu.so. If not do

```
sudo aptitude update && sudo aptitude install usplash-theme-ubuntu
```

Otherwise you should do

```
sudo aptitude update && sudo aptitude reinstall usplash-theme-ubuntu
```

(notice the install/reinstall difference). To ensure the socalled initramfs is up-to-date proceed with (which should be done by the reinstalling usplash-theme-ubuntu but just to double check)

```
sudo update-usplash-theme usplash-theme-ubuntu
```

This will take a couple of seconds. Now, when restarting, you should see (hopefully) the orange progress bar (usplash) while booting until the xserver (gdm) is up and asks you for your username and password.

---

### Post by The Judderman on 2009-05-08
Thank you spectre! I've been struggling with this issue as well, and your instructions worked beautifully! It's nice to see the Ubuntu bar increasing again!!!

---

### Post by spectre51 on 2009-05-08
Glad I could help man.  It was driving me nuts too till I got it working.  Love the Ubuntu community and its helpful nature.

---

### Post by champdood on 2009-05-20
Unfortunately I haven't had much luck with this, I tried the above without any results. That it starts to load the splash screen then drops out suggests to me the usplash theme is fine, but I can't find where it's deciding to do a text display rather than a nice pretty splash screen.

Any help would be much appreciated :)

---

