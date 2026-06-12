---
title: "Fixing Kubuntu deficiencies"
date: 2005-06-09
forum: Desktop Environments
---

### Post by RyaninZion on 2005-06-09
I installed KDE on my Ubuntu install the other day because I find Kate, Kontact, Konqueror, and Quanta superior to their GNOME counterparts, and find KDE overall a more polished and slick environment.

However, there are a few things in KDE that don't "just work" like they did in Ubuntu GNOME.

1. I was able to use the Keyboard Shortcuts settings in GNOME to find and make use of my HP nx5000 laptop's volume and mute buttons located on the outer casing of the computer.  (they were found as 0xa0, 0xae and 0xb0)  In KDE, the Hotkeys setup does not notice if I hit these buttons.  Is there a way to set these buttons up in KDE?

2. There seems to be a problem with Ksysguard on Centrino laptops (I found a bug filed on this issue).  I suppose I can use a karamba applet to monitor my cpu and memory usage, but is there an alternative to Ksysguard for viewing a list of running processes and killing bad ones?

3. Speaking of karamba - does it have the same tendency to eat up memory like gDesklets?

4. I want to use Gaim, as I find certain aspects of it superior to Kopete.  But, in KDE I cannot get any of Gaim's sounds to work.  Is there a way to fix this?

Thank you for any help anyone is able to provide  :)   And I hope I can return the favor one day.

---

### Post by RyaninZion on 2005-06-09
OK, I think I found a solution for #2.  Seems the GNOME System Monitor works just fine in KDE.

---

### Post by geearf on 2005-06-09
for 1- i used this topic : 
[http://www.linuxquestions.org/questions/history/125333](http://www.linuxquestions.org/questions/history/125333)

It is not your keyboard, but it could help you a bit.

---

### Post by dejitarob on 2005-06-09
[QUOTE=RyaninZion]2. There seems to be a problem with Ksysguard on Centrino laptops (I found a bug filed on this issue).  I suppose I can use a karamba applet to monitor my cpu and memory usage, but is there an alternative to Ksysguard for viewing a list of running processes and killing bad ones?[/QUOTE]Works fine on my Dell Inspiron 9300 with a 1.6GHz P4-M. What's the exact problem you are having with it?

---

### Post by sinbad782 on 2005-06-09
For #1 you could try going into KDE control cetner - regional and accessibility -> keyboard layouts and seting the key mapping for one of the HP layouts there. 

I've got a Logitech Cordless Desktop MX and the mapping isn't there, but the Internet Navigator keyboard is pretty close. I've put in a bug on xorg's bugzilla  about this already.

---

### Post by sb73542 on 2005-06-09
Sound in gaim-  make sure that you have a sane time-out for Arts, which will lock your sound devices.  I usually put it at 1 second, after which it will free up the device.  Actually, lately I have simply disabled Arts altogether, it is slow and buggy.  I configure the KDE sound notifications to pipe all sounds through an external program, aplay, which you will have to download from somewhere.

---

### Post by shakin on 2005-06-09
I'd be happy if it could remember window placement. I'm not sure what the 'Smart' placement setting is, but I had assumed it meant it would remember where I put a window and it doesn't do this.

---

