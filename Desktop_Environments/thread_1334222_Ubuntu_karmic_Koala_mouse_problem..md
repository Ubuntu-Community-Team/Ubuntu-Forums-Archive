---
title: "Ubuntu karmic Koala mouse problem."
date: 2009-11-22
forum: Desktop Environments
---

### Post by tnvkrishna on 2009-11-22
hi all,
It's been a time since i have installed ubuntu 9.10 (it was beta at that time
and i am still using the same version).It has been a pleasant experience 
throughout except a hiccup throughout ;)

I have the problem that mouse suddenly stops selecting anything
by left-clicking (but the mouse pointer "does move" when ever needed).
I had to arbitrarily right-click some where else like in the task bar or
right-click in some other window  etc. to make the mouse left -click work again.
If every of these arbitrary  right-click fails i need to logout and relogin  
or else reboot.

Let me tell you I could not find some thing that triggers this kind of
mouse behavior.

Could you plz help me resolve this issue?
please let me know if you need more information.
Is using the beta version problem?(but have done every update available.)

regards,
krishna.

---

### Post by UNME on 2009-11-22
Hi,

This could be caused because of many reasons but first check:

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Also, do check resolution, wallpaper (if u download wallpaper which are bigger in size this could cause problem), check the software's you installed.

Also go to system -> preference -> mouse test your mouse also configure mouse click and wheel scroll.

check drivers for your mouse.

Thanks
Unme

---

### Post by UNME on 2009-11-22
And Hey update to final release of ubuntu karmic koala, cannot blame someone for problems in beta ...

---

### Post by jlcd on 2009-11-22
i have exactly the same problem (and using the updated version).
suddenly the mouse left click stop working. today i also got 'alt+tab' not working!

i did what tnvkrishna said and my clicks works again.

please take a look!


(using default koala's background)

note: the MOUSE click stops working, but the touchpad still works.

---

### Post by tnvkrishna on 2009-11-22
hi unme,

you said to check my mouse drivers.
could you also post the necessary commands?
I'll use one of the default karmic wallpapers and see if i get this 
problem again.

thank you.

---

### Post by UNME on 2009-11-22
I know only following commands:

lsusb - usb devices
lspci - pci device and drivers
hwinfo - this is not installed by default, you can install it using sudo apt-get install hwinfo
lshw - again need to install it.

check man for more information on these command:

$man lsusb

Note using verbose (-v or -vv) can give more information about drivers.

---

### Post by solaria on 2009-11-22
Yes, same problem here too:

Left mouse button stopped working in most windows.  Found that a right-click somewhere else brought back the left-click functionality (that's how I got here to post this...), but now left-click only works in FireFox, and right-click doesn't work anywhere.  ALT-Tab stopped working too.

Just started doing this yesterday. Maybe that last batch of updates?

Wait... it just changed again.  Now as able to right-click in FireFox, but left-click stopped... no, it's back again...

Looks like I'm getting various combinations of left-click right-click working, on the taskbar or in an application. Multiple desktops seem to complicate the problem too:  if FireFox is working on desktop #1 and I shift to desktop #2, (CTRL-ALT-Right), nothing works on Desktop #2, left- or right-click until I return to Desktop #1 and right-click in the special spot...

Reboot helps, for a while... but it fails again fairly quickly.

---

### Post by tnvkrishna on 2009-11-23
hi all,
mouse seem to working normally again ..
i do not know the reason ..
may be because i am now using the wallpapers with resolution matching
my computer's.And i installed all the packages starting with ibus
from ubuntu repositories,that could also be a reason(i don't know!)

thank you.

---

### Post by tnvkrishna on 2009-11-24
the problem persists..
i think there are fair good number of people
having this problem.
hope ubuntu fixes this with an update..

---

### Post by gerwulf on 2009-11-27
I do have the same problem here: sometimes, mouse left clicking stops working, but the touchpad keys still work. Logging off an on fixes the problem for some time. I'm using multiple monitors by defining a virtual resolution in xorg.conf, running on ATI's fglrx driver. My Karmic is up to date.

---

### Post by jeromio on 2009-12-09
Same problem here. To clarify, this is a laptop touchpad problem with 9.10. I have a desktop also w/ KDE and Karmic and have no problems w/ the mouse or buttons.

It's rather random. Sometimes I can go hours with no issues, then the left mouse button will just stop working and alt-tab stops and also switching virtual desktops stops working. I have not been able to do anything to get things working again except for logging out.

---

### Post by turbozmike on 2009-12-26
same problem here to.

---

### Post by Mark Tomlinson on 2009-12-30
And here as well.  Desktop machine running xubuntu 9.10.  Same symptoms as above; works after reboot, but after a while left click stops working.  I have an additional symptom that x11vnc stops responding at the same time.  Can anyone else confirm or deny that it is related?

---

### Post by krunge on 2009-12-30
Are there any messages being reported in /var/log/Xorg.0.log and/or /var/log/Xorg.0.log.old that seem related to the problems you are having?

---

### Post by Hyperion_1984 on 2010-01-06
I have the same problem with my Dell laptop but not with my older Acer laptop. What should I look for in the Xorg.0.log and the Xorg.0.log.old files?

---

### Post by mart1n on 2010-01-11
I have the same problem on Karmic, using a Logitech wireless optical mouse or a Dell wire mouse. disconnect and reconnect (unplug/re-plug) the mouse re-enables the mouse function.
Ps. I have no mouse problems on any older version of Ubuntu.

---

### Post by dik23 on 2010-01-11
Ok - same thing has happened to me on two laptops I have just upgraded from Jaunty

Second time it happened I used the touchpad to left click. This brought the usb mouse back to life.

---

### Post by NKK on 2010-01-17
Same problem. 9.10, fluxbox, logitech wireless mouse. Left click stops working shortly after boot. Restarting fluxbox helps for a while...

---

### Post by lanierbrian on 2010-01-19
Hi,

I'm having the same problem.  Mouse click seems to not work with application windows, when it's acting up I can still click the menu items at the top.  I also get an error when I try to update my system using the GNOME update mangager:  "Could Not Grab Your Mouse..."  I updated using apt-get with success.

bl

---

### Post by Zeerots on 2010-01-20
I also couldn't click on my Dell Inspiron, but after the automatic update this morning the mouse works well.

---

### Post by lanierbrian on 2010-01-22
UPDATE:

My issue is resolved **at the moment**, but several things changed at once so I don't know which affected the issue:

(1) I took the Logitech wireless mouse receiver out of the KVM switch and plugged another wireless mouse (an older Microsoft) directly into the PC.  I had previously tried using the Logitech with the receiver plugged directly into the PC with same behavior, so I don't think the KVM was the issue.

(2) I installed a bunch of updates using apt-get update and apt-get upgrade (this was yesterday, 1/21/10 about 3pm EST).  I had previously downloaded upadates 24-48 hours earlier.

I'm not sure if this is the end of this or if I'm being lulled a feeling of relief only to have my hopes crushed tomorrow, but we'll see!

bl

---

### Post by crazyhorse54 on 2010-02-06
The problem went away when I shut down AWN but just returned.

The whole thing started after my last update.

Here is the list of packages:
[INDENT]Commit Log for Sun Feb  7 00:15:59 2010


Upgraded the following packages:
devicekit-power (011-1ubuntu1) to 011-1ubuntu2
gnome-power-manager (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.3
gtk2-engines-pixbuf (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libdevkit-power-gobject1 (011-1ubuntu1) to 011-1ubuntu2
libgail-common (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgail18 (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-0 (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-bin (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-common (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-dev (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
linux-generic (2.6.31.17.30) to 2.6.31.19.32
linux-headers-generic (2.6.31.17.30) to 2.6.31.19.32
linux-image-generic (2.6.31.17.30) to 2.6.31.19.32
linux-libc-dev (2.6.31-17.54) to 2.6.31-19.56
python-ubuntuone-client (1.0.2-0ubuntu2) to 1.0.3-0ubuntu1
python-ubuntuone-storageprotocol (1.0.0-0ubuntu1) to 1.0.1-0ubuntu1
ubuntuone-client (1.0.2-0ubuntu2) to 1.0.3-0ubuntu1
ubuntuone-client-gnome (1.0.2-0ubuntu2) to 1.0.3-0ubuntu1

Installed the following packages:
linux-headers-2.6.31-19 (2.6.31-19.56)
linux-headers-2.6.31-19-generic (2.6.31-19.56)
linux-image-2.6.31-19-generic (2.6.31-19.56)

[/INDENT]

---

### Post by gkid on 2010-02-06
ok i just instaled this ubuntu 9.10 karmica i think latest and i had this mouse problem and i found somthing strange, on how to fix the problem:
Each time you reboot your ubuntu login your user
Open Terminal
type mousetweaks [Hit Enter}
you will recive an error or somthing that will require you to log out to eneble 
Select log out.
log back in your user, and pwawawauf you wont have problems anymore:P
well that works for me.

---

### Post by widda on 2010-03-14
Hullo,
I have a variant on the mouse behaviour.
After upgrade to 9.10, mouse (touchpad) leftclick does nothing UNTIL I move it from the clicked object, then it goes ahead and obeys.
It's hard to get used to. Click, wait, doh, yeh, move the arrow off, bingo.
Can't find this behaviour mentioned anywhere, but this thread is closest so far.
It's across Gnome and xfce.
I'll try some of the suggestions here, meantime..happy to hear from anyone..thanks

---

### Post by R0bb0b on 2010-03-22
Having the same issue.  I just got a new mouse, switching from a MS mouse to Logitech.  My new mouse is an LX6 cordless: [http://www.logitech.com/index.cfm/428/3879&hub=1&cl=us,en?WT.z_sp=Image](http://www.logitech.com/index.cfm/428/3879&hub=1&cl=us,en?WT.z_sp=Image).

I installed it on 9.04 and had the same issue and was hoping that an upgrade to 9.10 would solve the problem but it is exactly the same.  I haven't noticed that it is specific to any application but about 15 seconds after I start using the mouse, the left click just stops working.  I then have to switch back to my old mouse which sucks because it double clicks accidentally all the time.

I have tested my new mouse in Windows, as I have a dual boot system, and it works fine.  I am currently running about 250M of updates, I will keep you posted.

---

### Post by R0bb0b on 2010-03-22
The problem persists.

When I was doing some research for 9.04 I ran into this thread which is much like this one but for an earlier version.  Someone on there said something about adding the command "noapic acpi=off" a file called "/boot/grub/menu.lst" which I couldn't find.

The only *.lst files that I found in that dir were:
command.lst
fs.lst
handler.lst
moddep.lst
partmap.lst
parttool.lst

When trying it, several people claimed that this solved their problem.  Is there an equivalent modification that can be made to 9.10?  This certainly isn't going to kill me, but I would rather not go with another Microsoft mouse.  It's funny that my lame Microsoft mouse works better in Ubuntu then my new Logitech.

---

### Post by GenghisKhan on 2010-03-25
I have a similar problem.
I'm using 9.10 on an Acer laptop. The left button on my wireless Logitech mouse randomly stops working. It starts working again after I click the left button on my touchpad.

---

### Post by sforces on 2010-03-30
Think this just fixed it for me too! I've been using 9.10 since it's release in Oct `09 but only started having issues yesterday after a reboot. I suspect one of the packages that got updated did it. Tried going to previous kernel, killing various updated packages running in memory but it wasn't until I tried mousetweaks that it resolved the issue.

Thanks!

> **gkid said:**
> ok i just instaled this ubuntu 9.10 karmica i think latest and i had this mouse problem and i found somthing strange, on how to fix the problem:
Each time you reboot your ubuntu login your user
Open Terminal
type mousetweaks [Hit Enter}
you will recive an error or somthing that will require you to log out to eneble 
Select log out.
log back in your user, and pwawawauf you wont have problems anymore:P
well that works for me.

---

### Post by M@se on 2010-04-01
just installed Ubuntu 9.10 on an almost brand new 64 bit HP desktop machine and am having the same problems with mouse. It just hangs there and the only way to unlock it is to power down the computer manually (which sucks). Found this site using Google, but sadly, no one seems to have a definitive answer yet. It's quite a shame since I've heard soooo many good things about Linux. Seems I will have to stick with what works until someone figures this out

---

### Post by mrquick on 2010-04-01
I had exact same problem.  mousetweaks worked for a bit, but left and came back a few hours later and the problem is back again.  I ran mousetweaks again, to no avail.  really really frustrating.

---

### Post by azurplex on 2010-04-03
I have a similar problem but only in a Firefox browser on a site that heavily uses Flash. everywhere else is normal.
sometimes the right click trick works, sometimes when I hold the left button down it will work on release.
Something else I notice is that with the left button depressed, rollover targets think the mouse cursor is gone.

From reading it sounds like the type of mouse isn't the issue since we all seem to have different brands.

My Xorg.0.log has the following mentioning mice.
Could it be the Mac emulation?

(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.


Could it be the Mac emulation?

---

### Post by highno on 2010-04-09
I have similar problems: neither usb mouse nor mousepad accepts left clicks right after booting. Sometimes they work but will give up later on during my X session.
I can switch over to another virtual console, do a "sudo service gdm restart" and most likely it will work then but only for a limited but random time.

I am using Ubuntu 9.10 here with all updates and proposed too.

While investigating I tried to use older kernels and found the 2.6.28 series working flawlessly. All newer kernels showed the same problem.

---

### Post by M@se on 2010-04-10
is there any way to downgrade to earlier versions that seems to work?? The way I am reading this, you can do some serious damage to your harddrive and I don't want to chance that

---

### Post by aprilus on 2010-04-22
i have the same problem! my is notebook also. but i installed 9.10 newly, not upgrade.

does anyone can solve the problem? someone said to read the file: /var/log/Xorg.0.log, but i do not know how to read it.:(

---

### Post by carthmen on 2010-04-25
I just got this exact same problem.  I have been running 9.10 since release with no problems.

I have not changed anything on the system for a long time.  It started after a reboot it seemed so maybe the last bunch of updates.  

Hope a fix comes down the pipe soon.

Any one have any luck finding a work around.

---

### Post by sforces on 2010-05-04
Has anyone with this problem tried upgrading to Ubuntu 10.04 yet? I'm curious to know if it's been addressed there or if I'll be dealing with the same issue all over again. Also, as other folks have stated, mousetweaks works for a while but then it stops. :( ](*,)

---

### Post by miannuzzi on 2010-05-08
Hi, sadly this is still happening. It happened to me on Karmic and now for my surprise is happening again in Lucid with my Logitech USB. Is very frustating since I can not use my computer due this bug. And I looked everywhere for a fix but is doesn't exist! the only thing that seems to work is the mouse tweeks. I hope the guy from canonical put a huge emphasis on solving this bug. They can not expect that the people turns to Ubuntu from Windows for a common user if hey can not use their mouse. At the first time that happens that user is going to quickly give up and come back to Windows. And probably never come back. The worst thing is that he will have a big and worthy reason to do so.

---

### Post by sforces on 2010-05-25
Sadly this issue still exists in Ubuntu 10.04 Lucid Lynx. I upgraded last week and it's been happening consistently. :(

> **sforces said:**
> Has anyone with this problem tried upgrading to Ubuntu 10.04 yet? I'm curious to know if it's been addressed there or if I'll be dealing with the same issue all over again. Also, as other folks have stated, mousetweaks works for a while but then it stops. :( ](*,)

---

### Post by Bruce S on 2010-06-10
> **miannuzzi said:**
> Hi, sadly this is still happening. It happened to me on Karmic and now for my surprise is happening again in Lucid with my Logitech USB. Is very frustating since I can not use my computer due this bug. And I looked everywhere for a fix but is doesn't exist! the only thing that seems to work is the mouse tweeks. I hope the guy from canonical put a huge emphasis on solving this bug. They can not expect that the people turns to Ubuntu from Windows for a common user if hey can not use their mouse. At the first time that happens that user is going to quickly give up and come back to Windows. And probably never come back. The worst thing is that he will have a big and worthy reason to do so.

My solution to my rather old Logitech Cordless Mouse becoming deceased on me , may help.

 I got an old (still working) Mouse on a string connection , and it works well, and is keeping things going until my replacement mouse arrives.

---

### Post by sashby on 2010-07-06
Here's something you can try.  This assumes the underlying problem is  actually with your settings that affect how your system handles window  focus and focus stealing.

I am using XFCE - if you aren't using XFCE it could still be a similar  problem, but the settings would be found  elsewhere.

1) "Applications" Menu / Settings / XFCE 4 Settings Manager
2) Uncheck "Activate focus stealing prevention"
3) Uncheck "Honor standard ICCCM focus hint"

I've been having the same problems with left-clicks not being detected, and needing to right-click all over the place until I get a response before using the mouse again.  I had it fixed with a non-standard (test version) kernel.  Probably that kernel just was compiled such that it didn't treat these focus options in the usual way.  Anyway last week a software update cause the problem to reappear, along with the "COULDN'T GRAB YOUR MOUSE" error talked about elsewhere.

Changing BOTH of these options (must be both) has solved the all of these problems for me.

---

### Post by king minger on 2010-07-12
I have been experiencing this problem since 9.04 beta on a Dell d600 laptop. it's the touchpad driver seemingly, as there is no problem when i use a logitech vx nano wireless mouse, however, when using the touchpad, the left button click will quite often get stuck down (the button up notification gets lost or ignored) I can only assume this is in the synaptics driver as the problem is not there in Win XP. it is also not a purely a ubuntu issue, as I have also tried the latest fedora FC13 live disc and the issue remains there too.

over the past year i have seen a lot of posts regarding this issue, and no clear solutions... I do hope this can be resolved as it's a fairly major inconvenience that this laptop can't really be used with linux anymore without an external mouse, and once XP is not supported with security updates, i doubt it will run Win 7 very well....

---

