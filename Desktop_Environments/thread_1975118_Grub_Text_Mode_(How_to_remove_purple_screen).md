---
title: "Grub Text Mode (How to remove purple screen?)"
date: 2012-05-06
forum: Desktop Environments
---

### Post by hp01 on 2012-05-06
I'm really hoping someone can help as I've been pulling my hair out for days trying to figure this out. I've removed quiet and splash from /etc/default/grub, run update-grub and update-initramfs -u as root, but for the life of me, I can't see the system text when the server boots.

It seems like the text is not visible, or perhaps a background is in front of the text. I just don't know.  When I shut down, it drops to text mode, but I really want to see the status of things as it boots up. I edited the plymouth script to change the startup background to grey, and I've even tried to hardcode the colors in 05_debian in /etc/grub.5 (I think). Has anyone got Ubuntu 12.04 to display a text startup?

thanks

---

### Post by oldfred on 2012-05-07
Welcome to the forums.

If you only have one system, grub does not show a menu. You can hold shift key from BIOS until menu appears if you want to see menu.

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by hp01 on 2012-05-07
Hi, Thanks for the reply!

I can display the menu, I've changed the /etc/default/grub so that the menu is displayed at boot. That's no problem. I see a purple screen and white text. I can choose whatever selection works.

It's just when I select the option, I don't get a standard black background with system text scrolling. I get a purple screen......and then the unity greeter.

I guess I could try GRUB_TERMINAL=console, however I recall reading somewhere that this disabled X from starting. I guess I'll try it and see.

I also set in grub (I'm recalling this from memory:

GRUB_CMDLINE_LINUX_DEFAULT="bootdegraded=true"
GRUB_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT=10

---

### Post by oldfred on 2012-05-07
If you want to see the boot process it is quiet splash on the linux/kernel line in grub menu or defaults in grub's config file.

/etc/default/grub

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
> GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


---

### Post by hp01 on 2012-05-07
> o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

Exactly, I'm trying to get a black screen with text, so I have removed quiet and splash from the command line:

GRUB_CMDLINE_LINUX_DEFAULT="bootdegraded=true"

And I don't get the black screen with text, just a purple blank screen (no ubuntu logo, just purple). I've gone in to see the actual boot parameters (by pressing e at the menu stage and c
confirming the kernel line) and still no good.

I've edited the /lib/plymouth/... grub theme to change the background color to grey.  This worked, so now I have a grey screen at bootup, but again no system text output, just a background.

I've been using red hat for over a decade, and this is my first time using ubuntu. So far very slick, but this one little nagging issue is problematic.

---

### Post by oldfred on 2012-05-07
After editing grub file did you run.
sudo update-grub

Or at grub menu is it still showing quiet splash. You can manually edit it out if it is. Use e at grub menu to see boot stanza.

---

### Post by hp01 on 2012-05-07
Yup, both update-grub and someone else suggested update-initramfs -u (both run as root).

Grub has been updated as now I have a grey screen since changing the background colors in the plymouth theme.

This should just work, it's very confusing why I don't see text. On my Fedora boxes, just removing 'quiet' from the kernel line gave all the text.

---

### Post by grahammechanical on 2012-05-07
Perhaps is it debug that you are looking for.

[http://www.gnu.org/software/grub/manual/grub.html#debug]("http://www.gnu.org/software/grub/manual/grub.html#debug")

Oh by the way, Grub is a GNU product not a Ubuntu product. Just so you know who are the correct people to moan at.

Regards.

---

### Post by hp01 on 2012-05-07
I've actually hardcoded these color_highlight and color_normal in the 05_debian file, and still no luck.  Very very confusing.

I've had more experience with grub1, this grub2 approach seems to have added a lot of complexity, and I don't know what ubunutu specific customizations might be there to theme it.  I actually think the graphical boot is very polished and slick -- I just want to see everything start up properly on a box that I will leave running 24x7 most of the time.

---

### Post by Myoldmopar on 2012-05-09
Uncomment #GRUB_TERMINAL=console from /etc/default/grub

---

### Post by hp01 on 2012-05-10
Hi, That provided me the startup text I was looking for, and the system booted to the unity greeter which I wanted.

It is still strange that I can't get a higher resolution text based output (which is what removing splash and quiet were supposed to do), but for not this is good enough.

thanks

---

### Post by memand on 2013-01-06
I think what you want to do is:

```
GRUB_CMDLINE_LINUX_DEFUALTS=""
GRUB_CMDLINE_LINUX=""
```

and have

```
GRUB_TERMINAL=console
```
uncommented

:)

---

### Post by marcb_ro on 2013-03-22
The [ubuntu plymouth wiki]("https://wiki.ubuntu.com/Plymouth") states:
> If you want to see the text-based boot messages (which use the Plymouth "details" plugin, press the ESCAPE key at any point when Plymouth is running. Note that the ESCAPE key acts as a toggle, so you can keep switching between graphical and text mode as required.
Therefore, why not use the "details" module?
Here's what I did to get some text displayed during boot through plymouth.

[LIST=1]
[*]It turns out there's already a "details" plymouth theme in ubuntu. Normally, it isn't listed among the alternative themes on your systems. You can check it out with the following command ```
sudo update-alternatives --list default.plymouth
```
If you see the line below among the output you can skip to step 3.```
/lib/plymouth/themes/details/details.plymouth
```

[*]Add the "details" theme to the plymouth alternatives:```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/details/details.plymouth 10
```
Go to step 1 and repeat the test, just to make sure the new them has been added.


[*]Switch to the new theme by running: ```
sudo update-alternatives --config default.plymouth
```Then ```
sudo update-initramfs -u
```

[*] Edit */etc/default/grub* and remove parameters "*quiet*" and "*splash*" from the line ```
GRUB_CMDLINE_LINUX_DEFAULT="...."
```
Update grub by running ```
sudo update-grub
```
[/LIST]
Reboot and you should now see a list of messages on boot.

**_OPTIONAL_**
If you're having video issues on boot (plymouth starts late, no graphics at all, etc.), and depending on your config, you may want to check the following out:
[LIST]
[*] the Debian plymouth *[Configuration]("http://wiki.debian.org/plymouth#Configuration")* wiki section
[*] running [plymouth in a framebuffer]("http://askubuntu.com/questions/79953/why-does-plymouth-start-so-late")
[/LIST]

---

