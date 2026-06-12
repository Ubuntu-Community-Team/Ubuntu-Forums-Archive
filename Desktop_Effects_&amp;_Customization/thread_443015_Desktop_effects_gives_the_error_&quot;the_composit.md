---
title: "Desktop effects gives the error &quot;the composite extension does not exist&quot;"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by na1sh on 2007-05-14
When I attempt to enable the "Desktop Effects" I get an error  "The Composite extension is not available". Is there something that you can do to help?

---

### Post by sethdotcom on 2007-05-14
i get that 2, did you install the restricted drivers?

and what is you graphics card?
your graphics card may not handle 3D rendering, espesially if it is a intregated card

---

### Post by na1sh on 2007-05-14
Yes I install the restricted drviers

I'm using ATI card
I can us 3D with it

---

### Post by sethdotcom on 2007-05-14
> **na1sh said:**
> Yes I install the restricted drviers

I'm using ATI card
I can us 3D with it

what is the model of your card?

---

### Post by krussell on 2007-05-14
Hello na1sh :-)
Did you include the extension section in /etc/X11/xorg.conf?

---

### Post by na1sh on 2007-05-14
sorry

I have All-In-Wonder 2006 PCI Express Card
it use Radeon X1300 Series Graphics processor
With 256MB GDDR3

---

### Post by na1sh on 2007-05-14
Xorg.conf

Section "Extensions"
	Option		"Composite"	"0"

I tray to change form "0" to "1"

but it give me a massage "Desktop effects could not be be enabled"

---

### Post by netsoul on 2007-05-14
The same thing with me - ATI Radeon 9500.  Voreover, OpenOffice failed to start with restricted drivers.  So I uninstalled them and everything works great now - both Beryl and Open Office.

---

### Post by na1sh on 2007-05-14
I want to enjoy the desktop Effects to see the deferent between ubuntu and Vista:-k 
but i thank that lunix need more years to follow Windows  #-o

---

### Post by weblordpepe on 2007-05-14
It's just vendor support that s lacking in linux. Uninstall the restricted drivers and stick to the open source ATI drivers like I do on my laptop.
Beryl beats the pants off of Vista. It has nice things like hardware-accelerated zoom. Its good for the rediculusly tiny letters in Firefox...but thats another thread :P

---

### Post by Krzysztof on 2007-05-14
I had this message and resolved the problem simply by installing xserver-xgl.
Now everything works just fine!

---

### Post by na1sh on 2007-05-14
form where and how can I install this file xserver-xgl.:-k

---

### Post by ericallen on 2007-05-14
> **Krzysztof said:**
> I had this message and resolved the problem simply by installing xserver-xgl.
Now everything works just fine!
cool thanks that fixed my problem also

> **na1sh said:**
> form where and how can I install this file xserver-xgl.:-k
synaptic package manager

---

### Post by hotrod6657 on 2007-10-31
yeah, how would one go about installing xserver-xgl?

This is pretty much my first Linux distro so i'm in the process of learning all the ins and outs.

Thanks in advance!

hotrod

---

