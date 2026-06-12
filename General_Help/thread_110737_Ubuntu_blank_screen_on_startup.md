---
title: "Ubuntu blank screen on startup"
date: 2005-12-31
forum: General Help
---

### Post by dkbg on 2005-12-31
Okay, first of all, I'm a completely new Linux user and pretty unfamiliar with the command line so any step by step help would be the most useful.

I've just recently installed Breezy 5.10, I'm dual booting with Windows XP on my Toshiba M70 laptop, but I'm having some trouble. When I choose the Ubuntu OS in the Grub bootloader, everything seems to go pretty well, the Ubuntu logo appears along with various status messages which scroll underneath. The status bar reaches full and then the system just stops on a totally blank black screen after briefly displaying a blinking cursor in the top left. Nothing happens. I can use ctrl+alt+f# to reach a login, but I have no idea what to do from there.

I must also mention that I did not configure the network during Ubuntu's installation, and the status messages display a message stating that a connection to ntp.ubuntulinux.org has failed.

Thank you for any help you can offer! I would really like to get this working soon.

---

### Post by apparition on 2005-12-31
If you can use ctrl+alt+f# to reach a login, try logging in and entering 'startx' at the prompt.  That may either work and load Gnome, or display the errors it encounters while trying to load Gnome.

Not configuring the network during Ubuntu's installation should not interfere.  I have a DSL connection, so I set it up using pppoeconf after Ubuntu was installed.  The status messages displaying ntp.ubuntulinux.org has failed just means your machine was not connected to the Internet and thus could not synchronize your system clock.  You can either ignore that or disable it in a boot-up manager later if you don't care for synchronizing your system clock.  There are decent guides/hints on here you can pull from to use pppoeconf and bum (boot-up manager) to achieve these latter points.

---

### Post by tmahmood on 2005-12-31
do you use a NVIDIA graphics card? then it maybe a Graphics card issue. Updating the Driver might help.

---

### Post by dkbg on 2005-12-31
Okay, I reinstalled clean and I'm having the same problem. This time I logged in and used startx and this is what I got:

x auth: creating new authority file /home/<username>/.serverauth.29876
x auth: creating new authority file /home/<username>/.Xauthority
x auth: creating new authority file /home/<username>/.Xauthority

Fatal server error:
server is already active for display 0
If this server is no longer running, remove /tmp/.XO-lock and start again

Please consult...bla bla bla

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT.MAGIC-COOKIE-1 key
giving up.
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error

Then I get a cursor.

And no, my video card is an ATI Radeon X700.

---

### Post by dcstar on 2005-12-31
[QUOTE=dkbg]Okay, first of all, I'm a completely new Linux user and pretty unfamiliar with the command line so any step by step help would be the most useful.

I've just recently installed Breezy 5.10, I'm dual booting with Windows XP on my Toshiba M70 laptop, but I'm having some trouble. When I choose the Ubuntu OS in the Grub bootloader, everything seems to go pretty well, the Ubuntu logo appears along with various status messages which scroll underneath. The status bar reaches full and then the system just stops on a totally blank black screen after briefly displaying a blinking cursor in the top left. Nothing happens. I can use ctrl+alt+f# to reach a login, but I have no idea what to do from there.
........[/QUOTE]
Log in with your username and password at the prompt, then enter:

**sudo dpkg-reconfigure xserver-xorg**

to reconfigure the graphics card setting.

If you don't have the right video driver installed, try a basic VESA configuration to at least get the desktop going.

If it doesn't work, just repeat the process until you get somewhere (or give up....)

---

### Post by dkbg on 2006-01-01
Yes! I've gotten it to work finally. I had to use the VESA option you suggested, as selecting the ATI option didn't seem to work for some reason...The desktop appears after some weird mangled stuff happens on screen, and everything looks fine.

The max resolution I can use is only 1024x768 though, is that caused by the usage of the VESA settings? My LCD's native resolution is 1280x800.

Thanks for the help, its greatly appreciated.

---

### Post by ChaoticMind on 2007-10-03
two years later, i'm having the same problem. 
I get the msg unable to allocate memory on startup, and after the ubuntu load screen, i get a black screen. (i can still login and operate the machinne fine, but the screen is entirely black - I know that because of the sound). 

I tried putting the VESA drivers in dpkg-reconfigure xserver-xorg, it worked fine, but obviously there is no acceleration. I can't access the ctrl+alt+Fx terminals myself, so i had to do it fromt he recovery console. It might be worth mentioning that in the prompt that asks how memory to allocate to the video card, it's defaulting to zero, not sure if it's not supposed to. 

My video card is an Nvidia 8700M GT 256mb dedicated, which is a fairly new card. I tried dling nvidia-glx-new, but nothing happened: it stayed on VESA, and when i tried re-select nv, same problem occured. I really am not sure what I'm supposed to do to enable the proper nvidia drivers! 

Any help would be greatly appreciated :) 

I might be way off, but I think I read somewhere that gutsy has new drivers? should I attempt an update?

---

### Post by dabl on 2007-10-03
MMmmmmmm -- I'm not sure whether you've entangled 3 or 4 different problems together into a nice hairball here -- let's see if it can be sorted.  :)

1. You get a black screen after a new install.

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

2. You'd rather run a driver that offers 3D acceleration:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

3. You found the NEXT to newest Nvidia driver in nvidia-glx-new, which isn't so great for the 8700.  Use Envy, as mentioned in 2 above, but

4. Envy requires a tweak for Gutsy before you run it -- check out the 29 July "Mini How-To" post here. I followed it and Envy installed the newest driver on my Gutsy system:

[http://albertomilone.com/wordpress/?m=200707](http://albertomilone.com/wordpress/?m=200707)

5. Your 8700 gags on the Gutsy splash screen.  Answer is to add the boot option "nosplash=y" to the end of the kernel line in /boot/grub/menu.lst, so it looks approximately like this:

kernel /boot/vmlinuz-2.6.22-12-rt root=UUID=6b0fa2a3-53da-4059-bffa-24fe8360c245 ro quiet nosplash=y

(Thanks to amplogik for that one)

How's that for a cleaned up hairball?  :guitar:

---

