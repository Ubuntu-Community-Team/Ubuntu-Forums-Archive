---
title: "[SOLVED] keyboard back light"
date: 2009-01-03
forum: General Help
---

### Post by dmatthys on 2009-01-03
I left my original posts below for reference however i have isolated the exact step i took to correct the problem and it is

Note: mod3 may not be the one that is available on your machine this option can very to find which one is available in terminal type
> xmodmap -pm

then follow below

> create a file in /etc/X11 called Xmodmap.  So start up Gedit or your favorite text editor

gksudo gedit /etc/X11/Xmodmap

Now add this to the file

add mod3 = Scroll_Lock

Then reboot and your ready to go!!

ok unique problem i have a logisys multimedia keyboard that lights up using the sccroll lock key thats not the unique part found tons of posts on it the one that got my keyboard lit up says use the command xset led on which worked and xset led off turns if off a little extra work but i dont shutdown that often the unique part is when i run xset led on not only does the keyboard light up a volume control thing pops up over and over and over again any ideas on whats going on and how to correct it

I apologize this information is not gonna be of any use because im not exactly sure what i did i was messing around in synaptic package manager and ran an update and now i have full functionality of the scroll lock key

---

### Post by dmatthys on 2009-01-03
anybody??

---

### Post by dmatthys on 2009-01-04
these are the only two sites i could find scince my original post that were even close to relevant 


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231022](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231022)

this site seems to suggest that the scroll lock key should work in intrepid however its not or if it is the led does not come on so my back light wont come on

[http://blogaites.com/en/](http://blogaites.com/en/)

did not work as the file does not exist in ubuntu 8.10

im still looking any ideas from anyone are definatly welcome

---

### Post by nuc on 2009-02-24
Beforehand, I'm sorry for my english.. :mad:
As for me, keyboard back light lights up by scroll lock key too, and it's enough for me to give a command "xset led 3", after that nothing else happened.

I wrote this script to enable and disable the light with a single click on the icon
```
#! /bin/bash
#num - 0, caps - 0, scroll - 0	LED mask:  00000000
#num - 0, caps - 1, scroll - 0	LED mask:  00001001
#num - 1, caps - 0, scroll - 0	LED mask:  00000002
#num - 1, caps - 1, scroll - 0	LED mask:  00001003
#num - 0, caps - 0, scroll - 1	LED mask:  00000004
#num - 0, caps - 1, scroll - 1	LED mask:  00001005
#num - 1, caps - 0, scroll - 1	LED mask:  00000006
#num - 1, caps - 1, scroll - 1	LED mask:  00001007
leds=`xset q | grep LED | cut -c66`
case $leds in
0 | 1 | 2 | 3 )
xset led 3 ;;
4 | 5 | 6 | 7 )
xset -led 3 ;;
esac

```

---

### Post by go_beep_yourself on 2009-06-13
Didn't work for me. None of the xset commands I've tried have turned on or off my keyboard LEDs. Why not?

---

### Post by Rabid8264 on 2011-02-26
> **nuc said:**
> Beforehand, I'm sorry for my english.. :mad:
As for me, keyboard back light lights up by scroll lock key too, and it's enough for me to give a command "xset led 3", after that nothing else happened.

I wrote this script to enable and disable the light with a single click on the icon
```
#! /bin/bash
#num - 0, caps - 0, scroll - 0    LED mask:  00000000
#num - 0, caps - 1, scroll - 0    LED mask:  00001001
#num - 1, caps - 0, scroll - 0    LED mask:  00000002
#num - 1, caps - 1, scroll - 0    LED mask:  00001003
#num - 0, caps - 0, scroll - 1    LED mask:  00000004
#num - 0, caps - 1, scroll - 1    LED mask:  00001005
#num - 1, caps - 0, scroll - 1    LED mask:  00000006
#num - 1, caps - 1, scroll - 1    LED mask:  00001007
leds=`xset q | grep LED | cut -c66`
case $leds in
0 | 1 | 2 | 3 )
xset led 3 ;;
4 | 5 | 6 | 7 )
xset -led 3 ;;
esac

```

Thanks!!!!
I was having the same problem...not anymore!!!:D

---

