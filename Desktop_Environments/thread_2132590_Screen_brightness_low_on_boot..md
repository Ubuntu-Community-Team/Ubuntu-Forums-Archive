---
title: "Screen brightness low on boot."
date: 2013-04-05
forum: Desktop Environments
---

### Post by veganrailpunk on 2013-04-05
Hi

I have just installed Lubuntu 12.10 on my new Acer Aspire One d270 after many years with Kubuntu which I now find to be too chunky and buggy for my little machine. Anyway, when I boot up I get no splash screen and the screen brightness is set to the lowest. If I login then logout again the screen brightness goes back to normal on the login screen and all is fine. Also if I press ctrl-alt F7 then ctrl-alt F1 as the screen brightness goes low (where I'm guessing the splash should start) I get normal brightness from the login screen.

After a bit of research it seems that it might be that lightdm is starting before my graphics driver. Is there any way of forcing the graphics driver to start earlier or for lightdm to wait?

Cheers, Pete

---

### Post by matt_symes on 2013-04-05
Hi

> After a bit of research it seems that it might be that lightdm is  starting before my graphics driver. Is there any way of forcing the  graphics driver to start earlier or for lightdm to wait?

You can get lightdm to start later by editing the file

```
/etc/init/lightdm.conf
```

Look for the line that says

```
exec lightdm
```

and add a sleep statement before it so it looks like this

```

sleep **n**
exec lightdm
```

where n above is a number in seconds.

I'm interested if this fixes the problem for you, as per your research.

If it does not fix the problem...

Open a terminal and type these two commands

```
sudo apt-get install pastebinit
dmesg | pastebinit
```

Post back the link it displays here so we can check.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Hi

Thanks for your help, delaying lightdm has not sorted it, even with a 10 second wait. The screen goes dim before the delay kicks in.

Here is the link: [http://paste.ubuntu.com/5680208/](http://paste.ubuntu.com/5680208/)

Thanks again

---

### Post by matt_symes on 2013-04-05
Hi

> Thanks for your help, delaying lightdm has not sorted it, even with a 10  second wait. The screen goes dim before the delay kicks in.

I did wonder.

While i look at dmesg, can you post the output of

```
ls /sys/class/backlight
```

and 

```
cat /sys/class/backlight/*/{brightness,max_brightness}
```

Run the second command when the backlight is both dim and when it's bright and post back all the results.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Okay

ls /sys/class/backlight
acpi_video0  psb-bl

when bright:
cat /sys/class/backlight/*/{brightness,max_brightness}
5
100
9
100

when dim:
cat /sys/class/backlight/*/{brightness,max_brightness}
5
0
9
100

Also, my keyboard's function keys cannot change the brightness although when I try a box with a changing bar comes up suggesting to me that Lubuntu knows what the buttons should do but doesn't actually do it (if that makes sense!)

---

### Post by matt_symes on 2013-04-05
Hi

```
acpi_video0 psb-bl
```

You have two drivers loaded for the backlight. The acpi and the vendor one. 

I wonder if this is the cause of the problem.

> cat /sys/class/backlight/*/{brightness,max_brightness}
5
**0**
9
100

Is this max_brightness that is set to zero ? can you check, when the screen is dark, with

```
cat /sys/class/backlight/acpi_video0/max_brightness
```

Please post the output of

```
cat /proc/cmdline
```

When the backlight is dark, from the terminal type

```
echo 100 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

Does this command make it brighter ?

After that. When dark run this command.

```
echo 100 | sudo tee /sys/class/backlight/psb-bl/brightness
```

Does that make it brighter ?

From the terminal again, does this return an error ?

```
sudo modprobe -r video
```

and finally post the output of this command (capital A).

```
lspci -nnk | grep -iA3 vga
```

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Right then

```
cat /sys/class/backlight/acpi_video0/max_brightness
9
```

cat /proc/cmdline:
```
BOOT_IMAGE=/vmlinuz-3.5.0-26-generic root=UUID=9dd48707-4fed-4809-be84-7bb55bbe6d3f ro quiet splash vt.handoff=7
```

```
echo 100 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
gave an invalid argument response

but
```
echo 100 | sudo tee /sys/class/backlight/psb-bl/brightness
```
made the screen up to full brightness and putting different values in worked

```
sudo modprobe -r video
```
returned:
```
FATAL: Module video is in use
```

and finally
lspci -nnk | grep -iA3 vga:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
	Subsystem: Acer Incorporated [ALI] Device [1025:061f]
	Kernel driver in use: gma500
	Kernel modules: gma500_gfx
```

I'm guessing that I shouldn't have two drivers loaded? Should the acpi one be removed?

---

### Post by matt_symes on 2013-04-05
Hi

> **veganrailpunk said:**
> I'm guessing that I shouldn't have two drivers loaded? Should the acpi one be removed?

It's beginning to look like that. It seems to me that acpi backlight driver is getting in the way; especially as psb-bl seems to be controlling the backlight.

> 
```
sudo modprobe -r video
```
returned:
```
FATAL: Module video is in use
```

This is interesting. Can you post the output of

```
lsmod | grep video
```

For another quick test can you boot with the kernel  option

```
acpi=off
```

and see if you still get the dim screen on boot. (this is not a real solution as it will disable all acpi).

Can you then check that acpi_video0 is gone from

```
ls /sys/class/backlight
```

Post back on results.

I'll check on your graphics card.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
lsmod | grep video

```
uvcvideo               71278  0 
videobuf2_core       32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc  12757  1 uvcvideo
videobuf2_memops 13213  1 videobuf2_vmalloc
video                    18895  2 acer_wmi,gma500_gfx
```


Can you explain how to boot with the kernel option

acpi=off

thanks

---

### Post by veganrailpunk on 2013-04-05
No worries I booted with acpi off and it was still dim though acpi is gone from /sys/class/backlight

---

### Post by matt_symes on 2013-04-05
Hi

> **veganrailpunk said:**
> 

lsmod | grep video

```
uvcvideo               71278  0
videobuf2_core       32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc  12757  1 uvcvideo
videobuf2_memops 13213  1 videobuf2_vmalloc
**video                    18895  2 acer_wmi,gma500_gfx**
```

That is why the modprobe command you typed earlier did not unload the video (creating the file acpi_video0) module then.

Can you post the output of

```
lsmod | egrep "acer_wmi|gma500_gfx"
```

> 
Can you explain how to boot with the kernel option

acpi=off

thanks

At the grub command prompt where you get to choose the kernel, press e to edit the kernel command line. 

Look for the line that contains

```
BOOT_IMAGE=/vmlinuz-3.5.0-26-generic root=UUID=9dd48707-4fed-4809-be84-7bb55bbe6d3f ro quiet splash vt.handoff=7
```

navigate the cursor until it's after vt.handoff=7 and add acpi=off.

Press ctl + x or F10 to continue booting 
(It should say at the bottom of the screen the exact keys to type to continue booting as i forget)

when booted up is it dimmed ?

Can you also then post the output of

```
cat /proc/cmdline
```

I think we may be getting closer to nailing down the problem. After that we can look for a solution.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Thanks

lsmod | egrep "acer_wmi|gma500_gfx"

```
acer_wmi               27587  0 
sparse_keymap          13659  1 acer_wmi
wmi                    18591  1 acer_wmi
gma500_gfx            187766  2 
drm_kms_helper         47304  1 gma500_gfx
drm                   238811  3 gma500_gfx,drm_kms_helper
i2c_algo_bit           13198  1 gma500_gfx
video                  18895  2 acer_wmi,gma500_gfx
```


The screen is still dim when booting with acpi=off. Acpi is gone from /sys/class/backlight.


cat /proc/cmdline

```
BOOT_IMAGE=/vmlinuz-3.5.0-26-generic root=UUID=9dd48707-4fed-4809-be84-7bb55bbe6d3f ro quiet splash vt.handoff=7 acpi=off
```

---

### Post by matt_symes on 2013-04-05
Hi

We cross posting. 

I think this may be a known issue and i am doing some reading up. 

I'll post back a bit later.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Brilliant, thank you very very much.

Sorry about the cross post.

---

### Post by matt_symes on 2013-04-05
Hi

Yep. 

This is a known issue and most having been using scripts from what i have read and echo'ing values into the psb-bl file using scripts.

Let's try something. 

Edit the file

```
/etc/init/lightdm.conf
```

Where you added the sleep statement before, replace it with this.

```
echo 100 > /sys/class/backlight/psb-bl/brightness
```

Save the file and reboot.

What happens ? I don't have the same card as you so i can't really check on any of this.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Yep, that's worked! Still goes dim where I think the splash would be but is bright when lightdm starts up.

I guess it's not a complete fix but I can change the brightness using

```
echo ***n*** | sudo tee /sys/class/backlight/psb-bl/brightness
```

Thank you so much for your help :)

---

### Post by matt_symes on 2013-04-05
Hi

A partial fix then :)

I'm wondering if you would be able to fix it earlier by creating a new upstart script that starts really early (much earlier than lightdm).

It may even be possible to fix it in initramfs (not 100% sure about this though)

If you want to check these possibilities then post back to say so.

We would be looking at exploring these possibilities tomorrow though.

It may be possible to fix the brightness keys by calling into a script when they are pressed as well.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
To be honest, this is great for me. I have been using Kubuntu 12.04 for half a year on this machine and never realised I couldn't change the brightness so I guess I don't particularly need it working fully. I'll be happy to look into it further if you think it will help with Ubuntu development, though.

Thanks very much again :)

---

### Post by matt_symes on 2013-04-05
Hi

If you're happy then i'm happy :D

I just wanted to double check you are not booting with the acpi=off option.

You do not need it and, as we were cross posting, i not 100% sure what you did you enable it that kernel option.

If you still have it then remove it.

Enjoy Lubuntu. It's a great distro.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
I am happy :)

I'm not booting with acpi off, I did the same as you said to do to boot with it off so it was only that one time. Just so I fully understand - I don't want acpi=off in the kernel command, I want acpi to be loaded? Is that correct?

I might try fix the function keys with scripts at some point but my real problem has been fixed.

Once more, thank you :)

---

### Post by matt_symes on 2013-04-05
Hi

> **veganrailpunk said:**
> I'm not booting with acpi off, I did the same as you said to do to boot with it off so it was only that one time. Just so I fully understand - I don't want acpi=off in the kernel command, I want acpi to be loaded? Is that correct?

Yep. You don't need the acpi=off option so you are fine as you are. You want to use ACPI. 

There are some ACPI errors in your dmesg output, however if your laptop is working alright then use ACPI.

Kind regards

---

### Post by veganrailpunk on 2013-04-05
Ace, ta. I shall mark this as solved :)

---

### Post by matt_symes on 2013-04-06
Hi

I was given this link by long time forum member mikewhatever.

There may be a better workaround for the gma500 chip now.

You may want to give it a try.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Brightness_hotkeys](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Brightness_hotkeys)

My thanks to Mike. I was not aware of that page :D

Kind regards

---

### Post by veganrailpunk on 2013-04-07
Nice one, that worked a treat.

The hot keys work and the acpi isn't showing up in /sys/class/backlight.
It still needs the "echo 80 > /sys/class/backlight/psb-bl/brightness" line in lightdm.conf but all is working fine.

Thanks yet again and thanks to mikewhatever :)

---

