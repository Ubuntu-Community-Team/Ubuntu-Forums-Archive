---
title: "Brightness FN keys not working in Vostro 1000, Ubuntu 7.04 64 bits"
date: 2007-09-27
forum: Dell  Ubuntu Support
---

### Post by leonelag on 2007-09-27
Hi,

I just bought a Dell Vostro 1000 notebook, and installed 7.04 Feisty Fawn 64 bits no it. Now it dual boots with Windows XP.

The Fn keys for brightness are not working. Other Fn keys combos, such as volume up/down/mute and cdrom-tray ejecting are working fine.

Whenever I use the brightness keys, the brightness is set to its full. I have to reboot the machine to return the brightness to some value that won't give me headaches.

The brightness keys work fine in Windows XP and at boot time, when the GRUB options are displayed. As soon as I log into Gnome, they stop working and behave as I described earlier.

I believe that Gnome takes control of the volume keys, because they have no effect when in a terminal, and when used under Gnome, a small picture is displayed, which has Gnome-ish traits.

Also, the Gnome brightness applet displays a message: "Cannot get the laptop brightness".

Has any user of a Vostro 1000 experienced the same problems ?
How do I fix this ?

[]'s
Leonel

---

### Post by sikavica on 2007-10-12
I've just install Gutsy RC and I have the same problem with the brightness fn keys...

---

### Post by theichibun on 2007-10-26
I would like an answer to this too, it's getting anoying.

---

### Post by Mlehliw on 2007-11-03
You could try blacklisting the video module.

To do this open /etc/modprobe.d/blacklist

and append

blacklist video

---

### Post by knowledge_is_power on 2007-11-03
I have the same issue on my Inspiron 1501
and i tried Mlehliw's suggestion, but to no avail. (nothing changed at all... )

---

### Post by Zerd on 2007-12-02
```
sudo apt-get install xbacklight
xbacklight -set 50
```
Should set your backlight to 50%

---

### Post by sikavica on 2007-12-02
> **Zerd said:**
> ```
sudo apt-get install xbacklight
xbacklight -set 50
```
Should set your backlight to 50%
That's one of the first things I've tried. Still it doesn't solve the issue, nothing is happening with the brightness. It only gives: ```
No outputs have backlight property
```

---

### Post by Orion2000za on 2007-12-05
I got a Vostro 1400 and same problem. However, if I click on the Powermanager and in that use the slider to change the brightness for "Mains Powered" that works perfect... 

Sinclair

---

### Post by sikavica on 2007-12-05
> **Orion2000za said:**
> I got a Vostro 1400 and same problem. However, if I click on the Powermanager and in that use the slider to change the brightness for "Mains Powered" that works perfect... 

Sinclair
Are you talking about Gnome's Power Manager? Because, I don't have anything like that here...

---

### Post by Orion2000za on 2007-12-05
> **sikavica said:**
> Are you talking about Gnome's Power Manager? Because, I don't have anything like that here...

Sorry I am in KDE - Kubuntu. But surely Gnome has settings for what happens if you go on Battery, ie CPU Policy and Brightness? In Kubuntu  Powermanager you can use "sliders" to set these values for brightness both for "on mains" and "on battery". And those works though the keyboard buttons dont.

Sinclair

---

### Post by Orion2000za on 2007-12-05
> **Orion2000za said:**
> Sorry I am in KDE - Kubuntu. But surely Gnome has settings for what happens if you go on Battery, ie CPU Policy and Brightness? In Kubuntu  Powermanager you can use "sliders" to set these values for brightness both for "on mains" and "on battery". And those works though the keyboard buttons dont.


I checked a bit and you likely have to open "Preferences", for me they come up when I "restore" K Powermanager

Sinclair

---

### Post by sikavica on 2007-12-05
> **Orion2000za said:**
> Sorry I am in KDE - Kubuntu. But surely Gnome has settings for what happens if you go on Battery, ie CPU Policy and Brightness? In Kubuntu  Powermanager you can use "sliders" to set these values for brightness both for "on mains" and "on battery". And those works though the keyboard buttons dont.

Sinclair
I only know about Power Management Preferences in Gnome, and I don't see any settings about the brightness. I might try KDE powermanager though...

---

### Post by aelius on 2007-12-23
I have a Dell Vostro 1000 laptop with Ubuntu 7.10 Gutsy Gibbon (64-bit edition).
There is already a bug report for this annoying issue.

check it out:

[https://bugs.launchpad.net/ubuntu/+bug/159255](https://bugs.launchpad.net/ubuntu/+bug/159255)

A temporary solution to get brightness levels working :

in a terminal  type this as root:

$ echo -n VALUE > /proc/acpi/video/VGA/LCD/brightness

where VALUE can be one of these (100=full brightness)

12 25 37 50 62 75 87 100

---

### Post by geekgod on 2007-12-28
ok so there are two scripts called by the brightness keys which hit acpi_fakekey (doesnt work)
Below are a couple quick and dirty replacements that work on dell vostro 1000

these replace :
/etc/acpi/video_brightnessup.sh
[http://www.pastebin.ca/834518](http://www.pastebin.ca/834518)
/etc/acpi/video_brightnessdown.sh
[http://www.pastebin.ca/834514](http://www.pastebin.ca/834514)

Backup any originals

---

### Post by aelius on 2007-12-28
scripts provided by Geekgod work like a charm!
Thanx Geekgod!

---

### Post by questron on 2007-12-31
works great, thank you! (on 7.10)

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by pestilence4hr on 2008-02-09
> **Mlehliw said:**
> You could try blacklisting the video module.

To do this open /etc/modprobe.d/blacklist

and append

blacklist video

Thanks!  Blacklisting video fixed the brightness keys on my Vostro 1400 with nvidia 8400m video card.

---

### Post by himynameiskevin on 2008-02-11
> **geekgod said:**
> ok so there are two scripts called by the brightness keys which hit acpi_fakekey (doesnt work)
Below are a couple quick and dirty replacements that work on dell vostro 1000

these replace :
/etc/acpi/video_brightnessup.sh
[http://www.pastebin.ca/834518](http://www.pastebin.ca/834518)
/etc/acpi/video_brightnessdown.sh
[http://www.pastebin.ca/834514](http://www.pastebin.ca/834514)

Backup any originals

so far this is working just fine for me on a vostro 1000 with ati xpress 1150 video..

---

### Post by reynaldo666 on 2008-04-15
Hi,
I have a vostro 1000 working on openSUSE 10.3 64bits and the referred script don't works to me cause the brightness variable, like in /proc/acpi/video/brightness, don't exist here. Any suggestions??
Anybody knows how to 'create' the brightness variable?

Some facts:
1) Fn+UP and Fn+DOWN works in the grub screen and keep the brightness after boot.
2) If acpi=off option is used the brightness keys works, but the cpu frequency policy don't works.

Anybody thinks it's a IRQ conflict?

Thanks for ideas. Sorry my poor english.
Reynaldo

---

