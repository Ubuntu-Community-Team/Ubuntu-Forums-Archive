---
title: "Kubuntu/Ubuntu Freezing"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Krogen on 2005-06-12
Hey everyone,

Here's the story.

I'm a Linux newbie who started using it just couple weeks ago. I started by downloading Knoppix since I read about it in a recent PC Mag and got hooked. I did a  Knoppix HD installation and it ran well but I ran into couple of weird problems (a whole another story). I decided to install Fedora Core 3. I installed a desktop installation and after the install, everything worked fine except when I rebooted [COLOR=Blue]my FC3 kept freezing![/COLOR] That was the end of my adventure with Fedora. After that, I decided to download Kanotix. Downloaded it, burned it, booted from the CD. Misteriously, my [COLOR=Blue]Kanotix froze during the "loading KDE" screen.[/COLOR] I rebooted a bunch of times before, finally, making Kanotix not freeze. I did a Kanotix HD installation, all went well. I booted to my new Kanotix desktop and guess what? [COLOR=Blue]It FROZE![/COLOR] Somehow, after a bunch of retries, I did [COLOR=Red]something[/COLOR] and, finally, I was trouble-free. Having not enough, I downloaded Gentoo. As a newbie, I desperately failed during the manual 10-hour installation.

Couple days ago, I decided to download Ubuntu. You won't believe me how much trouble I had with downloading CDs. I WASTED about 8-9 cds, downloaded the images (from different sources)  about 6-7 times. ALL CORRUPTED.

I installed Ubuntu [COLOR=Blue]anyways[/COLOR]. After a couple of retries, I finally got it to work (had to download a lot of packages from the internet). [COLOR=Blue]Ubuntu did not freeze.[/COLOR] I rebooted, and [COLOR=Blue]Ubuntu froze during the gnome loading.[/COLOR] I installed Kubuntu, [COLOR=Red]got the same thing.[/COLOR]

I decided to do a standard "server" installation (base system only). All went well. I downloaded Kubuntu, installed it. OK. I ran KDE, ok. I logged in, [COLOR=Blue]Kubuntu froze.[/COLOR]

During this.... nightmare, lemme call it that, I had my Windows XP installed all the time (so I ran dual boot with Grub).

No, I didn't give up yet. Or should I? Kanotix was sweet, but I'd like to try something different. 

Any suggestions/comments are welcome! Thanks!!!

Here's my PC:
AMD Athlon 64 3200+ (ClawHammer)
Albatron K8X800 Pro 2
1 GB DDRAM 400
120GB Seagate SATA HD
Gigabyte NVIDIA 6800

---

### Post by Xian on 2005-06-12
The list of things this could be the result of are numerous to say the least. However, the very first thing I would try is adding "acpi=off" to the kernel line in grub's menu.lst [/boot/grub/menu.lst] and then reboot using that configuration.

It would look something like this example:

```
kernel	/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda9 ro acpi=off vga=791
```

---

### Post by Xian on 2005-06-12
Oh, and if you can't do this due to system freezes then you can also add that parameter to the boot command while at the grub bootloader screen. You just select your Ubuntu install from the list presented, and then use the keyboard to enter the edit mode, then append the acpi=off notation to whatever is presently there.

---

### Post by Krogen on 2005-06-12
[QUOTE=Xian]The list of things this could be the result of are numerous to say the least. However, the very first thing I would try is adding "acpi=off" to the kernel line in grub's menu.lst [/boot/grub/menu.lst] and then reboot using that configuration.

It would look something like this example:

```
kernel	/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda9 ro acpi=off vga=791
```[/QUOTE]

Yes, I tried that. I also tried adding a lot of other options to the boot line but I had no luck.

I heard that those might be my NVIDIA drivers but I tried changing the main driver to vesa/nv and finally installing the nvidia ones, no luck with that either.

Thanks though. Every comment is like a diamond. Priceless.

---

### Post by Xian on 2005-06-12
If you are getting this on every distro so far you might just have a flaky video card that windows is able to deal with but Linux can't. 

Like I said, it could be numerous things. I'm sure you've also commented out some things like dri and glcore in your xorg.conf file to test that as well. If Knoppix didn't freeze upon boot then you might copy over that X config to your Ubuntu install and see if you get a better response.

---

### Post by Krogen on 2005-06-12
[QUOTE=Xian]If you are getting this on every distro so far you might just have a flaky video card that windows is able to deal with but Linux can't. 

Like I said, it could be numerous things. I'm sure you've also commented out some things like dri and glcore in your xorg.conf file to test that as well. If Knoppix didn't freeze upon boot then you might copy over that X config to your Ubuntu install and see if you get a better response.[/QUOTE]

Will do! 

And, yes, I did try to comment out dri (actually I just put # in the front) and glcore.

---

