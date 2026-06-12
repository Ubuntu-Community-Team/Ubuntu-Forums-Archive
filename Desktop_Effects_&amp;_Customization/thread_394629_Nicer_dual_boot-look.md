---
title: "Nicer dual boot-look?"
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by Staach on 2007-03-27
So..I just installed 7.04 on 2nd partition of a Vista HD. Love it already (no - not Vista!!). However my girlfriend think the grub is too confusing to be used (even with the fiesta img as background..I think it´s great!!). In stead she asked me if something like apple´s Boot Camp is possible instead of grub? Beeing quite new to linux, I said no!
But just to make sure - is it possible to get a dual boot like Boot Camp?:confused: 

Cheers

---

### Post by jtibau on 2007-03-27
> **Staach said:**
> So..I just installed 7.04 on 2nd partition of a Vista HD. Love it already (no - not Vista!!). However my girlfriend think the grub is too confusing to be used (even with the fiesta img as background..I think it´s great!!). In stead she asked me if something like apple´s Boot Camp is possible instead of grub? Beeing quite new to linux, I said no!
But just to make sure - is it possible to get a dual boot like Boot Camp?:confused: 

Cheers

What's so hard about using grub??? I guess you haven't edited the menu.lst at all since you say you are a noob (no offense, I considere myself a noob too lol).

Well you could at least try a couple of things:
1) Erase all options but two: Ubuntu, Vista... That way she'll have only two choices, not two per kernel, plus memcheck blah blah...
2) If she isn't interested in dual booting (meaning only you are interested in linux or vista) have grub remain hidden and make her preferred option be the default...

Here's how to do it:
The file is /etc/grub/menu.lst you have to edit it as root. You can type:
```
sudo gedit /etc/grub/menu.lst
```

This is my section that defines my grub menu, I have openSuSE 10.2, Windows XP and Ubuntu Edgy on it (with several kernels). This is pretty much at the end of the file.

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		openSUSE 10.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 vga=0x317 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Failsafe -- openSUSE 10.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot

```

So then basically erase everything but the sections you actually need. Or comment them rather... This is what I would to where it my case:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		openSUSE 10.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 vga=0x317 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot

```

Further on, modify the titles, so there will be even less stuff to read

```

## ## End Default Options ##

title		Ubuntu
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		openSUSE
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 vga=0x317 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot

```


Now you got three options :)


#####################
2) For my second suggestion:
-first keyword you need to find is "default" it will most likely have a 0 on it, which means it will boot (automatically) the first entry in the list of OSs. if it has a 1 it will boot the second option, 2 third option and so on. So just pick what you like :)
-second keyword "timeout", mine says 10, which means that if I don't press any key it will go on and boot my default boot option. If you mostly only boot the default, lower this value, no less than 2 seconds cause less than that and you might not get a chance to choose another option.
-third keyword "hiddenmenu", so grub won't show your gf its ugly face, you would have to press esc to get the list of options. Together with a low timeout it will make grub hardly noticeable by her.

I hope this helps :) there's a bunch of other tweakings you can do to grub, mostly for security. This are barely the ones I mostly do on my fresh installs. Have fun

---

### Post by Staach on 2007-03-28
Great.. thx for the help..I´ll be right on it when I get back from work..Oh and regarding the noop thing..None taken :)

---

### Post by PaulFXH on 2007-03-28
> third keyword "hiddenmenu", so grub won't show your gf its ugly face
Actually, your Grub menu doesn't have to have an ugly face. You can use a splash image to really brighten it up. Check this [thread]("http://www.ubuntuforums.org/showthread.php?t=278396&highlight=grub+splash+image") for details.

---

### Post by NikoC on 2007-03-28
Well when you 're editing the menu.lst you might as well uncomment the line following #Pretty colors. Just remove the # following that line and you're grub will have a blue-ish background... not really much of an improvement but less scary than just text ;)

---

### Post by mcduck on 2007-03-28
When editing the menu.lst, keep in mind that everything between lines

```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
```
and
```

### END DEBIAN AUTOMAGIC KERNELS LIST
```
will be automatically rewritten when you get kernel updates, so don't put anything extra in there, you'll loose it sooner or later.

To edit the options you'll have in Grub you need to change the settings in the default options section of menu.lst. For example to get rid of the memtes option you should remove the entry, and also change the '# memtest86=true' to '# memtest86=false' in default options section. When the next kernel update comes this tells update-grub to not add the memtest option to menu.lst ;)

---

### Post by jtibau on 2007-03-29
> **PaulFXH]
Actually, your Grub menu doesn't have to have an ugly face. You can use a splash image to really brighten it up. Check this thread for details.
[/QUOTE]

I liked openSuSE 10.1 (i think) grub theme... It had a christmas air to it, with penguins walking around, it was very neat. Then in 10.2 they changed it to a plain, more professional  look i guess.

I don't really care about changing it's looks, my bro did it once and it was kinda neat. He spent too much time on it though, I'd do it if it was something like changing the wallpaper. It is a good suggestion if you want it to be more appealing though, maybe I'll try it someday myself.

*EDIT: I tried the thread that you mentioned... I liked it, I remember my bro said it was a bit harder, don't understand why now lol.

[QUOTE=mcduck said:**
> When editing the menu.lst, keep in mind that everything between lines

```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
```
and
```

### END DEBIAN AUTOMAGIC KERNELS LIST
```
will be automatically rewritten when you get kernel updates, so don't put anything extra in there, you'll loose it sooner or later.

To edit the options you'll have in Grub you need to change the settings in the default options section of menu.lst. For example to get rid of the memtes option you should remove the entry, and also change the '# memtest86=true' to '# memtest86=false' in default options section. When the next kernel update comes this tells update-grub to not add the memtest option to menu.lst ;)

I hadn't seen the memtest keyword, up until now, I erase what I didn't like, anyway, each release gets a top of 3 kernel updates (from what I've experienced, not a rule). I will start using the memtest as of right now.

lol that's why I like ubuntuforums, I thought I was contributing but I still got some info myself :D Great community, even if the distro wasn't so good I'd still keep using ubuntu for this sole cause.

---

### Post by mcduck on 2007-03-29
> **jtibau said:**
> I liked openSuSE 10.1 (i think) grub theme... It had a christmas air to it, with penguins walking around, it was very neat. Then in 10.2 they changed it to a plain, more professional  look i guess.

I don't really care about changing it's looks, my bro did it once and it was kinda neat. He spent too much time on it though, I'd do it if it was something like changing the wallpaper. It is a good suggestion if you want it to be more appealing though, maybe I'll try it someday myself.

*EDIT: I tried the thread that you mentioned... I liked it, I remember my bro said it was a bit harder, don't understand why now lol.



I hadn't seen the memtest keyword, up until now, I erase what I didn't like, anyway, each release gets a top of 3 kernel updates (from what I've experienced, not a rule). I will start using the memtest as of right now.

lol that's why I like ubuntuforums, I thought I was contributing but I still got some info myself :D Great community, even if the distro wasn't so good I'd still keep using ubuntu for this sole cause.
The menu.lst is very well commented and it's worth reading the file through. You can learn pretty much everything there is to learn about configuring grub menu just by reading the configuration file :D

---

### Post by merlyn on 2007-03-30
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot").

---

