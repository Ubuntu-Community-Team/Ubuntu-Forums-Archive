---
title: "xorg.conf for 1920x1080 on jaunty"
date: 2009-04-25
forum: Desktop Environments
---

### Post by mdurkin on 2009-04-25
Hi All,
I'm running ubuntu 9.04 Jaunty.
I can get my monitor working properly by doing the following:
xrandr --newmode "1920x1080" 148.5 1920 2008 2052 2200 1080 1089 1095 1125 +hsync +vsync
xrandr --addmode VGA 1920x1080
xrandr --output VGA --mode 1920x1080

However, it's lost after reboot. I don't seem to be able to get things to stick by editing my xorg.conf, and the file seemed to have very little in by default. Here's the default file:

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 1360 768
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection


Any suggestions on what my Xorg.conf should look like. I've spent a while trying different configurations, including adding a Monitor section like this:

Section "Monitor"
        Identifier      "Configured Monitor Device"
        VendorName      "Unknown"
        DisplaySize 1920 1080
        ModeLine "1920x1080" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +Hsync +Vsync
EndSection

but it didn't work.

I would appreciate advice!
Thanks,
Matt

---

### Post by andrea000 on 2009-04-25
is this a nvidia or ati card?why cant you set the it from 
system>preference>screen resolution i know sometimes it does
not save have you tried that then just save that back to your
x config.

---

### Post by mdurkin on 2009-04-25
Hi There,
No this is the Intel 945 chipset supporting an atom 330 board:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I can't use the gnome-diplay-settings gui as the 1920x1080 resolution doesn't appear in there, although it does after running the xrandr commands I mentioned. I think it's not detecting the monitor correctly, and so just gives me a minimal resolution selection.
I suspect I just need something in the xorg.conf, but I really don't know what this should look like.
Thanks,
Matt

---

### Post by andrea000 on 2009-04-25
the Intel 945 chipset is/was blacklisted at least as far up as 8.10
that's what i have but i am not running it but compiz still see's it 
and shuts down so i had to do some editing and tell it i wasn't using it.
I think something like that is going on with your resolution.do you have 
proprietary drivers installed?

---

### Post by mdurkin on 2009-04-26
I'm on 9.04 (jaunty) so I'm not sure about blacklisting here. I don't have proprietary drivers installed and compiz is running as expected. xrandr switches into the right resolution without a problem - I just need to work out how to get a working xorg.conf (I think).
Any ideas?

---

### Post by PatrickVogeli on 2009-04-26
I believe you have a problem with the virtual line in your xorg.conf. Try to put Virtual 1920 1080 instead of what you have and reboot.

**EDIT:** better, remove this from the file:

SubSection "Display"
Virtual 1360 768
EndSubSection

save and reboot

---

### Post by mdurkin on 2009-04-26
Hi,
I had already edited the "Virtual" line to 1920 1080. In fact I just tried removing it and the xrandr commands then fail. I've also found that if I boot with the monitor not attached (I have a KVM, so sometimes it isn't), X comes up with some message about using a low resolution and asking me what I want to do. What I actually want is to simply hard-code it to only load at 1920x1080 as that's the native resolution of my screen.
I've attached my current xorg.conf below.
Still looking for ideas!!
Thanks,
Matt


Section "Monitor"
	Identifier	"Configured Monitor Device"
	VendorName	"Unknown"
	DisplaySize 1920 1080
	ModeLine "1920x1080" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +Hsync +Vsync
EndSection

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	1920 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by method on 2009-04-26
I think PatrickVogeli is right. I couldn't see the higher resolutions in the Display Settings application until I removed the hardcoded setting that Display Settings had previously saved to my xorg.conf. I think that Display Settings is storing the user's display preferences somewhere in gconf now and the xorg.conf isn't really meant to be configured, even though Display Settings will sometimes offer to hardcode values for you. 

Section "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
EndSection

Section "Device"
  Identifier  "Configured Video Device"
EndSection

---

### Post by mdurkin on 2009-04-27
sounds interesting - so where's the new config file?
I have the following ~/.config/monitors.xml

<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="TV-1">
      </output>
      <output name="VGA">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
</monitors>

It also only has the 1920 x 1080 definition, but I'm really not sure how this file is used and how it fits in with xorg.conf.
Anyone?

---

### Post by mdurkin on 2009-05-02
bump. anyone?

---

### Post by dest on 2009-05-14
I have the same problem and I have an ATI X850.

I've always configured the file xorg.conf until Ubuntu 8.10 but now with 9.04 it doesn't work.

My screen resolution doesn't even appear in xrandr. I have to set it manually with the commands given above.

And when you restart, same old, same old.

Dest.

---

### Post by days_of_ruin on 2009-05-14
> **dest said:**
> I have the same problem and I have an ATI X850.

I've always configured the file xorg.conf until Ubuntu 8.10 but now with 9.04 it doesn't work.

My screen resolution doesn't even appear in xrandr. I have to set it manually with the commands given above.

And when you restart, same old, same old.

Dest.

Not the best solution but what about writing a script to run those commands
and add it to the Startup Applications?

If you don't know how to do that I'll write one.

---

### Post by dest on 2009-05-15
I know how to do it.

I haven't given up yet, I'll try again when I'll be back home so it can work properly and preferably with xorg.conf.

Dammit Xorg ! I'm fed up of it.

---

### Post by gare on 2009-05-16
Hello,

I had same problem.

This helped me learn about Xrandr


[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

which shows how to persist the xrandr settings after reboot:

> 
Setting xrandr changes persistently

There are several ways to make xrandr customizations permanent from session to session: a) .xprofile, b) kdm/gdm, c) xorg.conf. Each of these mechanisms will be discussed in turn.

Setting xrandr commands in .xprofile

A user's ~/.xprofile file is executed on Xorg startup if it exists and is executable. You can copy and paste xrandr command line strings into this file so they're executed when you log in. For example:

  $ xrandr --output VGA-0 --mode 800x600

There are two disadvantages to using .xprofile for xrandr settings. First, it occurs fairly late in the startup process, so you'll see some resolution resizing during the initial screen draw; in some cases panel windows may resize improperly as a result. Second, as this is a per-user setting, it won't affect the resolutions of other users, nor will it alter the resolution on the login screen.

Setting xrandr commands in kdm/gdm startup scripts

Both KDM and GDM have startup scripts that are executed when X is initiated. For GDM, these are in /etc/gdm/, while for KDM this is done at /etc/kde4/kdm/Xsetup. In either case, you can paste in an xrandr command line string into one of these scripts.

This process requires root access and mucking around in system config files, but will take effect earlier in the startup process than using .xprofile, and will apply to all users including the login screen.

Setting resolution changes in xorg.conf


hth

---

### Post by Nicksha on 2009-06-11
@mdurkin:
Thanks for the ~/.config/monitors.xml tip! I had the same problem as you did (resolution is forgotten on restart) and I've changed the values in ~/.config/monitors.xml and now I get the correct resolution on startup. 

Also before that, I had changed some values in gconf-editor (in desktop->gnome->screen->default->0). Hope it helps to those who havn't fixed this yet!

---

