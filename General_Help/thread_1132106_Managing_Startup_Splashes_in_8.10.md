---
title: "Managing Startup Splashes in 8.10"
date: 2009-04-21
forum: General Help
---

### Post by Dngrsone on 2009-04-21
I'm afraid I've made a mess for myself.

I have 8.10 installed on an HP Pavilion dv2000 series (specifically dv2214us), which has a 1280x800 display and NVidia graphics engine.

What I tried to do was install a new grub background and a new splash screen.

My /etc/usplash.conf file is as follows:

```
# Usplash configuration file
xres=1280
yres=800
```

I tried using Startup manager, but that didn't end well-- my grub wallpaper is there, but it appears to be in 8-bit color and the grub text and highlight text is the same:  black background with white text, so I can't tell what is selected.  I've uninstalled Startup Manager.

My splash is some strange looking video test pattern that's offset a bit down and to the right (expected, considering my resolution).

Changing the resolution parameter in the /boot/grub/menu.lst doesn't seem to have any effect on the problem.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color light-green/black green/light-gray

#A splash image for the menu
splashimage=/boot/grub/splashimages/usplash-blue.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=789

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a
kernel		/boot/memtest86+.bin
quiet

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

```

Can anyone help me at least reset the splashes back to normal?

---

### Post by fooman on 2009-04-21
not at all sure,  but have you tried just commenting out the "pretty colors" & "splashimage" lines?  so that they look like:

```
# Pretty colours
#color light-green/black green/light-gray

#A splash image for the menu
#splashimage=/boot/grub/splashimages/usplash-blue.xpm.gz
```
  ...i would also try setting the usplash config to a standard size that will fit on your screen...maybe try xres=1024 x yres=768?

see if that helps.

---

### Post by ajgreeny on 2009-04-21
Firstly the grub splash and the usplash are quite different things, and I have no clue about changing the usplash screen, other than using a different ready available one, eg kubuntu-splash or xubuntu-splash.  Grub however is easy to change, but there are several requirements of the artwork you choose that are needed for it to work.  See this info below:-
Get splash from net or produce your own picture
 [1] The image needs to be in xpm format.
[2] The image needs to be 640x480 in size.
[3] The image must have only 14 colors.

The xpm file can be left as is or gzipped; grub seems to load gzipped images a bit faster. The thinking on this is that grub can load a gzipped image and decompress it faster than it can load the full size image, due to hard drive access times.

You can still change the foreground and background colors of grub's menu if you're using a splash image, but the image itself won't be affected, only the menu overlay.

Here are a couple ways to get an image in the format you want it:

The quick way: (using convert from imagemagick)

convert -resize 640x480 -colors 14 whatever.xpm newwhatever.xpm && gzip newwhatever.xpm

The slow way: (using the gimp)

Open the image you want to use in the gimp, click the "Image" menu, then "Mode", then "Indexed". Select "Generate Optimum Palette:" and enter 14 for the maximum number of colors. It's also recommended that you check the "No Color Dithering" option.
After the conversion, save the file as whatever.xpm. The gimp should automatically create the correct format when it saves the file.

After you've gotten the image into the correct format and gzipped it (or not, your choice), all you need to do is add it to your grub config file, menu.lst

Look for :-
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
splashimage (hd0,1)/boot/grub/splashimages/splash.xpm.gz

The bottom line is the one relating to you new splashimage and the partition in brackets is the same as in the line 
#groot=(hdx,x)

For some reason I have never got the imagemagick route to work, but I have no idea why that is so.  However the gimp works its magic well.
I notice in your grub menu.lst file you have the line 
```
splashimage=/boot/grub/splashimages/usplash-blue.xpm.gz
```and whilst that would be correct if added by update-grub, I think you should remove the = sign for the line to work and also add the partition pathway, eg (hd0,1), much as shown above 
Finally if you call your image splash.xpm.gz and after editing grub menu.lst as I show you then run update grub, the splash image will be there even after the next kernel update, which would otherwise remove the splash image from grub.  You will also note that the line excatly like your incorrect one, except for the name (splash) will appear just above the list of OSs at the bottom of the menu.lst file.
Sorry this is such a long winded answer to at least half of your question, but I hope it helps.

---

### Post by Dngrsone on 2009-04-21
> **ajgreeny said:**
> 
After you've gotten the image into the correct format and gzipped it (or not, your choice), all you need to do is add it to your grub config file, menu.lst

Look for :-
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
splashimage (hd0,1)/boot/grub/splashimages/splash.xpm.gz

The bottom line is the one relating to you new splashimage and the partition in brackets is the same as in the line 
#groot=(hdx,x)

For some reason I have never got the imagemagick route to work, but I have no idea why that is so.  However the gimp works its magic well.
I notice in your grub menu.lst file you have the line 
```
splashimage=/boot/grub/splashimages/usplash-blue.xpm.gz
```and whilst that would be correct if added by update-grub, I think you should remove the = sign for the line to work and also add the partition pathway, eg (hd0,1), much as shown above 
Finally if you call your image splash.xpm.gz and after editing grub menu.lst as I show you then run update grub, the splash image will be there even after the next kernel update, which would otherwise remove the splash image from grub.  You will also note that the line excatly like your incorrect one, except for the name (splash) will appear just above the list of OSs at the bottom of the menu.lst file.
Sorry this is such a long winded answer to at least half of your question, but I hope it helps.

So, how do I determine what the hard drive number should be?  I know Win XP is on (hd0,0) which is /dev/sda1 and my Ubuntu root is /dev/sda7... I can't remember if /boot is on a separate partition or not.

BTW, my planned grub splash is [this one](http://www.gnome-look.org/content/show.php/Blue+Ubuntu+GRUB?content=35814).

---

### Post by ajgreeny on 2009-04-21
Just try out the partitions one by one until you get the right one,  How can you not remember if you made a separate /boot partition?  I would think that is a fundamental part of the install that you would not forget, but what do I know?
However, sda7 is hd0,6 in grub-speak.
And here's my grub splash for you to compare, renamed splash.xpm.gz in the /boot/grub folder.

---

### Post by Dngrsone on 2009-04-21
> **ajgreeny said:**
> Just try out the partitions one by one until you get the right one,  How can you not remember if you made a separate /boot partition?  I would think that is a fundamental part of the install that you would not forget, but what do I know?
However, sda7 is hd0,6 in grub-speak.
And here's my grub splash for you to compare, renamed splash.xpm.gz in the /boot/grub folder.


I have nine computers in my home at the moment ranging from the incredibly ancient to middle-of-the-line laptops and featuring operating systems ranging from DSL to Slackware, to Win XP and Vista.  There are even a couple hard rives bouncing around with Win 9x on them.

Each machine is configured to immediate needs, and therefore I do not have a standardized partition set.  Chances are I did include a separate /boot partition, because I like to have that, but I just can't recall whether I did so on this last go-round.

I don't relish the thought of throwing a random number into my grub menu and hoping for the best-- I was hoping there would be a simple command-line call that would enable me to determine the current partition configuration of my machine.

Pardon me if I am coming across a tad rude, but it's difficult enough for an oldster like me to remember to take his lunch with him to work, let alone the finer details of the eightieth OS install he's done.

---

### Post by ajgreeny on 2009-04-22
OK, fair point.  I only have a single machine and know just about every file on it, but I see your problem.

To move one step further along the road to success you can run ```
sudo fdisk -l
```which will give output with an asterisk against the boot partition which may contain the image if it is a separate boot partition.  You can then try a reboot, but at the grub menu, hit "e" rather than enter and you can edit the line with the partition number in it by going to that line and hitting "e" again.  Change the partition info then hit enter, then "b" to boot and see if it is correct.  If not, repeat until you get the correct partition.  This way you do not have to keep rebooting, but just edit the grub menu on the fly until it is right.  Once you have the right partition you can edit the menu.lst with gedit as root.

Sorry if I was a bit short with you as well, but it was not meant to be rude.
Good luck.

---

### Post by Dngrsone on 2009-04-22
Okay, it looks like this machine does not have a separate boot partition.  The first partition is the bootable, and it is NTFS (Win XP).  So, my /boot directory, I assume, will either be (hd0,0) or (hd0,6).  Correct?

---

### Post by ajgreeny on 2009-04-23
OK, run sudo blkid to find which partition is 
**2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a**[B]
[/B]which is how it appears in the groot= line of your menu.lst file.  You will, I think, need to add that partition shown as the (hd#,#) part of the splashimage line in the menu.lst file format that I showed in post #3.  If that does not work, then I am out of my depth, I'm afraid.

---

### Post by Dngrsone on 2009-04-23
> **ajgreeny said:**
> OK, run sudo blkid to find which partition is 
**2ba09d44-a7c1-4a1b-a80e-ac39e466dd1a**[B]
[/B]which is how it appears in the groot= line of your menu.lst file.  You will, I think, need to add that partition shown as the (hd#,#) part of the splashimage line in the menu.lst file format that I showed in post #3.  If that does not work, then I am out of my depth, I'm afraid.

So, the location is on (hd0,6)...

Meh, still doing the same thing.  If I remove the splash pointer, then I get my colors back.  With it, regardless of whether it was my way or yours, the text is transparent background with white letters (highlight black/white) and the image is messed up-- it should show (in the initial case) a blue version of the Ubuntu standard splash, and instead it's a pixelated half-image with reds, whites, yellows, etc. like it's using the wrong palette or pushing a 16-bit image through an 8-bit filter.

---

### Post by ajgreeny on 2009-04-24
Did you make sure the image you used to get the 640x480 final was in 14 colours only?  Or at least reduce the colours to 14 at the end of the process.  It sounds as if grub is attempting to display some graphic but that the graphic is not showing right.  Just out of interest try with my splash image that I will attach as the gzipped final version.  I know that works properly so if you can't get it to show then something else must be wrong.

---

### Post by Dngrsone on 2009-04-24
[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]  Yours worked... the font colors are still not right, though.

Okay, ditched the splash images I was trying to use; got one that appears decent.  Now I need to figure out why the color scheme is off (highlight black background/white text doesn't work well when the splash is mostly black), and then fix the boot splash.

Thanks for all your help, AJGreeny!

---

### Post by Dngrsone on 2009-04-26
Okay, resolved the menu issue:

After the splash pointer, you need to use the commands foreground and background to change the colors, as follows:

```
splashimage (hd0,6)/boot/grub/splashimages/usplash.xpm.gz
foreground 99ffff
background 333333

```

In this case, I have cyan text (99ffff) and dark gray highlighting (333333).  The background of the text itself is transparent to allow the image through.


So, menu splash issue resolved, now all I have to do is figure out how to fix the bootsplash.

---

