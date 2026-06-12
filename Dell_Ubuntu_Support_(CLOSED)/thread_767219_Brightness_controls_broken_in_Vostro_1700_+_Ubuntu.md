---
title: "Brightness controls broken in Vostro 1700 + Ubuntu 8.04"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joeybutterface on 2008-04-25
Somebody please help me!!!

Upgraded to Ubuntu 8.04 this afternoon and now I'm stuck with two brightness settings:

Maximum brightness
Very Dim brightness
Or minimal brigtness

Hitting Function + Brightness key only moves the brightness control between those three levels. Whereas in 7.10 I could control 8 or 9 distinct levels.

Any ideas how to solve this? 'm getting a headache trying to work at this brightness level.

---

### Post by Amranu on 2008-04-25
Have the same problem on an m1330.

It is possible to use a brightness control by right clicking on a panel and clicking 'add to panel' and then choosing the brightness control. This works for the other settings, but it is still annoying not being able to use the keyboard shortcuts.

---

### Post by joeybutterface on 2008-04-25
Thank you! Thank you! Thank you! :)

Yeah it's annoying but at least I can take control of it with the applet until there's a fix. Now I need to go buy pills for the headache...

---

### Post by pormogo on 2008-04-26
My m1330n is having the same problem. I noticed that the panel for power settings has changed as well and no longer includes a percentage bar to set the backlick but a tick box.

---

### Post by CorruptNoob on 2008-04-26
Same with my M1330

---

### Post by neptho on 2008-04-26
This is probably the ugliest hack in the world, but bourne can't do arrays, and I didn't feel like making it better.  I've had to do this with my 1400 since Feisty.

Open a terminal and become root, using whatever shell you like:

```
$sudo $SHELL
```

Now, move the old ACPI support files that don't work out of the way:

```
#mv /etc/acpi/video_brightnessdown.sh  /etc/acpi/videobrightnessdown_bak.sh
#mv /etc/acpi/video_brightnessup.sh  /etc/acpi/videobrightnessup_bak.sh
```

Replace the files with these.

/etc/acpi/video_brighnessdown.sh:
```

#!/bin/sh
DEVICE=/proc/acpi/video/VID1/LCD/brightness
#. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_BRIGHTNESSDOWN
CURRENTLEVEL=`grep 'current:' $DEVICE | awk '{print $2}'`
if [ "x"$CURRENTLEVEL = "x0" ]; then
  CURRENTLEVEL=100
fi
SORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g' | sort
 -n | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
REVERSESORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g'
 | sort -n -r | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
for levels in `echo $SORTEDLEVELS | sed 's,\n,\ ,g'`
do
    if [ $CURRENTLEVEL = $levels ]; then
      echo -n $LASTLEVEL > $DEVICE
      break
    fi
    LASTLEVEL=$levels
done
```

and /etc/acpi/video_brightnessup.sh:

```
#!/bin/sh
#Yeah, I got kind of lazy.  Arrays in Bourne SUCK.
#. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_BRIGHTNESSUP
DEVICE=/proc/acpi/video/VID1/LCD/brightness
CURRENTLEVEL=`grep 'current:' $DEVICE | awk '{print $2}'`
if [ "x"$CURRENTLEVEL = "x0" || "x"$CURRENTLEVEL = "" ]; then
  CURRENTLEVEL=100
fi
SORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g' | sort
 -n | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
REVERSESORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g'
 | sort -n -r | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
for levels in `echo $REVERSESORTEDLEVELS | sed 's,\n,\ ,g'`
do
    if [ $CURRENTLEVEL = $levels ]; then
      echo -n $LASTLEVEL > $DEVICE
      break;
    fi
    LASTLEVEL=$levels
done
```

Save both files and chmod them 755:

```
#chmod 755 /etc/acpi/video_brightnessup.sh
#chmod 755 /etc/acpi/video_brightnessdown.sh
```

One more thing; we want to make sure you have the same device that I do.  It may not be.  Run the following as root, still, and notice the light levels changing.  As the backlight changes, note that device.

```
#for n in /proc/acpi/video/**/LCD/brightness; do \
   echo "Trying $n..."; for fade in `seq 1 100`; do sleep \
   0.01s; echo -n "$fade" > $n; done; done
Trying **/proc/acpi/video/VID/LCD/brightness**...
Trying **/proc/acpi/video/VID1/LCD/brightness**...

```

In my case, it was 'VID1'.

Now go back in and edit the files and change the DEVICE= line, as which is appropriate for your machine:

If it worked on 'VID':
```
DEVICE=/proc/acpi/video/VID/LCD/brightness
```

If it worked on 'VID1':
```
DEVICE=/proc/acpi/video/VID1/LCD/brightness
```

If it worked for something else, you get the idea.  Save both files as above 
with the proper DEVICE= line.  Remember to chown back to root:

```
#chown root.root /etc/acpi/video_brightnessup.sh
#chown root.root /etc/acpi/video_brightnessdown.sh
```

Exit, close terminal.
```
#exit
$logout
```

You've got your backlight back!

---

### Post by pormogo on 2008-04-26
I've also noticed that since support for vide on the 965GMA was added anytime I gpo to play a video it automatically turns the backlight all the way up and begins to singe my eyes. I'll try the above fix a little later to get my buttons working once more but does anyone know why watching video causes the backlight to torch up?

EDIT: Well I tried editing the 2 shell scripts in that area I also tried a slightly different version of this fix that I found in the general desktop forum and that did not work either :(

---

### Post by qhaz on 2008-04-28
Unfortunately this didn't work for me.  HP Pavilion dv2000 running Hardy.
But, this did . . . 

[http://ubuntuforums.org/showthread.php?t=673946](http://ubuntuforums.org/showthread.php?t=673946)

---

### Post by neptho on 2008-04-28
Interesting.  The only functional differences between that script and mine are the device, and that mine looks for what the LCD supports, rather than 'randomly try lower until it works'.

Glad it works for ya!

---

### Post by sureinlux on 2008-05-02
Hi Neptho,
 Thanks a lot. My LCD brightness adjustment worked afte I tried out your method. Just that my video device was:> DEVICE=/proc/acpi/video/**VGA**/LCD/brightness


---

### Post by Keyper7 on 2008-05-02
I think this deserves an entry in launchpad, does anyone know if there's one already?

---

### Post by pormogo on 2008-05-02
I concur there should be something in launchpad. I'm still trying to figure out if any other m1330 users are having the same issue. I want to know if the issue is perhaps BIOS specific. 

I have tried both of the interfaces in /proc both in VID1 and VID neither one of them appear to be adjusting correctly :(

---

### Post by Rubis on 2008-05-03
I tried this and 
```
#for n in /proc/acpi/video/**/LCD/brightness; do \
   echo "Trying $n..."; for fade in `seq 1 100`; do sleep \
   0.01s; echo -n "$fade" > $n; done; done
Trying /proc/acpi/video/VID/LCD/brightness...
Trying /proc/acpi/video/VID1/LCD/brightness...
```
worked, but when I try the brightness buttons, it is exactly the same.

When I run /etc/acpi/video_brightnessdown.sh I get the folowing output:
```
/etc/acpi/video_brightnessdown.sh: 10: -n: not found
/etc/acpi/video_brightnessdown.sh: 2: Syntax error: "|" unexpected
```

When I run /etc/acpi/video_brightnessup.sh I get:

```
[: 9: missing ]
/etc/acpi/video_brightnessup.sh: 9: x100: not found
/etc/acpi/video_brightnessup.sh: 11: -n: not found
/etc/acpi/video_brightnessup.sh: 2: Syntax error: "|" unexpected
```

---

### Post by mperroud on 2008-05-04
Hi

I tried the scripts on a Vostro 1500 and using the comand line they work fine with 7 level of brightness but when i use the fn+up or fn+down butons i still get the original 3 leves of the bug.

I checked on the /var/log/acpid log and the script ejecuted are ok. Any idea??

Here i copy part of the log

[Sun May  4 19:26:02 2008] received event "video LCD 00000087 00000000"
[Sun May  4 19:26:02 2008] notifying client 6227[107:116]
[Sun May  4 19:26:02 2008] notifying client 9526[0:0]
[Sun May  4 19:26:02 2008] notifying client 9526[0:0]
[Sun May  4 19:26:02 2008] executing action "/etc/acpi/video_brightnessdown.sh"
[Sun May  4 19:26:02 2008] BEGIN HANDLER MESSAGES
[Sun May  4 19:26:02 2008] END HANDLER MESSAGES
[Sun May  4 19:26:02 2008] action exited with status 0
[Sun May  4 19:26:02 2008] completed event "video LCD 00000087 00000000"
[Sun May  4 19:26:02 2008] received event "video LCD 00000087 00000000"
[Sun May  4 19:26:02 2008] notifying client 6227[107:116]
[Sun May  4 19:26:02 2008] notifying client 9526[0:0]
[Sun May  4 19:26:02 2008] notifying client 9526[0:0]
[Sun May  4 19:26:02 2008] executing action "/etc/acpi/video_brightnessdown.sh"
[Sun May  4 19:26:02 2008] BEGIN HANDLER MESSAGES
[Sun May  4 19:26:02 2008] END HANDLER MESSAGES
[Sun May  4 19:26:02 2008] action exited with status 0
[Sun May  4 19:26:02 2008] completed event "video LCD 00000087 00000000"


Regards

Martin

---

### Post by caro on 2008-05-05
> **Amranu said:**
> Have the same problem on an m1330.

It is possible to use a brightness control by right clicking on a panel and clicking 'add to panel' and then choosing the brightness control. This works for the other settings, but it is still annoying not being able to use the keyboard shortcuts.

Thanks for the hint.  I have a Dell e1505 and am experiencing the same problem.  

In 7.10, Power Management had a slider control where you could make your settings.  I don't know why this wasn't included in 8.04.  I couldn't find anything about it in Launchpad.

---

### Post by Gooler on 2008-05-05
Same problem here on an XPS 1330 with A09 BIOS revision & a Kubuntu box

I can set 7 different brightness levels via Power Manager sliders but only 3 with keyboard shortcuts.

---

### Post by RangerDanger on 2008-05-06
Here do this with original files.  Add "blacklist video" in /etc/modprobe.d/blacklist

Then restart.

---

### Post by pormogo on 2008-05-06
> **RangerDanger said:**
> Here do this with original files.  Add "blacklist video" in /etc/modprobe.d/blacklist

Then restart.

I reverted back to the original /etc/acpi files and then blacklisted this module and now all is well and I have my 7 video levels back. What exactly does the video module do?

---

### Post by atlas95 on 2008-05-06
This is working but this do another "bug" when you backlist video, try to plug unplug ac... brightness doesn't automaticaly change ...:(

---

### Post by pormogo on 2008-05-06
> **atlas95 said:**
> This is working but this do another "bug" when you backlist video, try to plug unplug ac... brightness doesn't automaticaly change ...:(

That would be unfortunate but at least then I could manually alter it back to the suitable level.

EDIT: I just got back home and plugged my laptop back in and it does appear to be automatically adjusting brightness levels without any issue.

---

### Post by Gooler on 2008-05-06
Just like pormogo here. Blacklisted video and backlight changes his level when AC is connected/disconnected.
The workaround works for me.

---

### Post by Tolaris on 2008-05-17
Blacklisting the video module completely resolved my problems with screen brightness on my Dell Vostro 1500 with Intel video:

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Under gutsy, I had to write my own backlight script which fetched screen brightness from dbus, and then called that script from /etc/acpi/video-brightness(up|down).sh.  The acpi_fakekey $KEY_BRIGHTNESSDOWN lines did nothing.  Under hardy, these worked, but the new video module caused the backlight to jump 3-4 steps each time I pressed a key.  Further, every time I used SDL (starting kscreensaver, running mplayer, starting a VirtualBox virtual machine), the brightness would adjust!

Now, everything works fine, the brightness moves one step at a time, the Fn+Up/Down keys work, and guidance power manager even shows the correct settings as I adjust them with the keys!

Thanks so much!

---

### Post by Keyper7 on 2008-05-17
Anyone confirmed a side effect of blacklisting the video module?

The problem that brightness does not change when AC is unplugged apparently is happening just to a few people...

---

### Post by Tolaris on 2008-05-17
Keyper7, the only side effect I have found is that my keyboard and mouse now appear to hang for 1-2 seconds when changing power state.  The input is not queued and sent later; it just doesn't arrive.

This isn't much of an issue for me, because the delay happens as I'm plugging in the power cable.  Thus I'm not typing, and don't care.

---

### Post by drdanield@gmail.com on 2008-06-08
Gateway M-6319 has similar problem. Brightness doesn't work by either function keys nor brightness applet.  The function keys work following similar "hacks" on /etc/apci/video_brightnessup.sh and video_brightnessdown.sh as described on following forum threads:
[http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374)
[http://ubuntuforums.org/showthread.php?t=673946](http://ubuntuforums.org/showthread.php?t=673946)
[http://ubuntuforums.org/showthread.php?t=767219](http://ubuntuforums.org/showthread.php?t=767219)

But applet still doesn't work. I think whatever is called by acpi_fakekey 224 and 225 is not working correctly.  Running Hardy 8.04 on
<code>
$ sudo dmidecode -s system-manufacturer
Gateway
$ sudo dmidecode -s system-version
3409361R
$ sudo dmidecode -s system-product-name
M-6319
</code>
xev output for function keys brightness up (key code 212) and down (101):
<code>
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
</code>


I would really appreciate it if this can be fixed fundamentally by an update from main Ubutnu repository.  It's an important problem for laptops running on battery.

---

### Post by empty_tank on 2008-06-25
> **RangerDanger said:**
> Here do this with original files.  Add "blacklist video" in /etc/modprobe.d/blacklist

Then restart.

Thank you.  This worked for Vostro 1400 with hardy.

Now trying to solve the hibernate issue. (cannot resume from hibernate)... Suspend works... but this belongs to another thread :)

---

### Post by growingneeds on 2008-08-03
I managed a workaround by following the tips in this thread. Thanks to all.

1. Fine-tune the LCD brightness to a greater degree by adding the 'Brightness Applet' to the Gnome Panel.
2. To achieve 7 adjustable levels of brightness on the function keys (instead of the usual 3), and to keep the LCD brightness from being set at the maximum after every reboot: Add a new line &#8220;blacklist video&#8221; to the file &#8220;/etc/modprobe.d/blacklist&#8221;, and reboot.

I own the Dell Inspiron 640m.

---

### Post by mrynit on 2008-08-03
confirmed problem on inspiron 1420 (1420n pre-installed ubuntu) 8.04

when I press the brightness up|down key it looks like there is 9 cells then a little bit of one more

when i go up from the lowest level it jumps by 5and a little more(really a half the total bightness bar), second up press goes to max. when at half pressing down goes all the way to the lowest brightness. when at max brightness pressing down drops the brightess to four cells. one more down press takes to lowest.

I am supprised no one has mentioned what kernel they are using. I have this problem in all my 2.6.24-XX-generic kernels.**This problem does not happen in 2.6.22-14-generic**. I have not tried any kernels between 2.6.22-14-generic to 2.6.24-16-generic. Obviously this whole problem with the brightness keyboard key is a kernel issue. It would be nice if someone would go though all the different kernels to find the exact kernel that introduced this problem. That a correct fix could be made and hopefully be released as a patch.

> **RangerDanger said:**
> Here do this with original files.  Add "blacklist video" in /etc/modprobe.d/blacklist

Then restart.

confirmed fix. i have 7 steps. I if hold the key combo it does not automaticly adcance to the next level. I have to manualy step to each level. One problem I have seen is that the brightness applet does not match the level of brightness bar that pops up. For example if I hover over the applet icon it give a tooltip show 0% when I am at 100% birghtness from pressing the Fn key combo.

I am going to remove the "blacklist video" and boot into 2.6.22-14 to see if there is any difference  with the currenet state.[edit] In the old kernel there were 10 steps to the brightness and all the above behaviour was the same.

This is a good fix but still it is a kernel issue that should be looked into.

---

### Post by wellybelly on 2008-09-04
Yep I have the same issue with my 1420.

Also the dim brightness slider in the power management thing. I liked the 7.10 version.
Anybody know whether these are being fixed/can be fixed?

---

### Post by futuroimperfetto on 2008-09-30
Hello,

I've bought a Dell XPS m1330 this summer. It came with Gutsy preloaded and function keys were working fine (other things would not, like mic detection).

I upgraded to Hardy and solved some problems, but I see have no control over anything related to function keys. Fn + anything does not work.

I'm not a skilled Ubuntu user, so before I try all the aforementioned scripts, I'd like to get some confirm that it's going to work (or maybe that it's being considered on launchpad).

Thanks!

---

### Post by dahlheim on 2008-10-15
adding
blacklist video
to /etc/modprobe.d/blacklist
fixed this for my dell xps m1210.  changing power modes still changes the backlight appropriately, and i get no keyboard or trackpad delay.
thanks!

---

### Post by MedellinManDem on 2008-10-15
I have a Vostro 1500 and experience most of the problems noted here. It's ridiculous.

---

### Post by Tolaris on 2008-10-16
I have a Vostro 1500, and had these problems too.  Just blacklist video as the instructions say, and the buttons will work fine.

I no longer have a delay when I push a brightness button.  It was resolved in an upgrade 4 months ago.

---

### Post by davy78x on 2008-11-14
this doesnt work in ibex. once you use the functions keys to adjust brightness, compiz stops working followed by the keyboard and then the mouse.

---

### Post by sexandcyanide on 2008-12-11
davy78x:

I noticed that. I put blacklist video in /etc/modprobe.d/blacklist, restarted. And Compiz failed. And then Gnome failed. I couldn't click anything NOT on the desktop.

Is there a bug in LaunchPad for this (in Intrepid)?

---

