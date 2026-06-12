---
title: "Desktop Not effects cannot be enabled"
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by Xanturia on 2007-12-05
Righty-ho, I've lurked for quite some while to find a solution to my problem, and alas my searching has come up with no results :(

Basically what is happening is i'm dual booting ubuntu 7.10 gutsy gibbon with windows vista i think...

i go in to system > preferences > desktop effects

try to enable them, and it says "desktop effects could not be enabled"

i am running on a toshiba p200 satellite pro laptop out of the box.

Finnaly, whenever i try to change my screen resolution the picture messes up horribly, does anyone know why this is?

Thanks in advance.

---

### Post by krussell on 2007-12-05
hello :-)
have you tried installing the graphics card driver?

---

### Post by FuturePilot on 2007-12-05
What is your graphics card? Have you checked for a driver in the Restricted Driver Manager (System>Administration>Restricted Driver Manager) If you have already done that what happens when you enter
```
compiz --replace
```
in a terminal?

---

### Post by Xanturia on 2007-12-05
when i put this in the terminal i get this:

matt@matt-laptop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

don't forget, i am an utter newb.

How do i install the drivers?
as in, step by step please? :)

Thanks for your help so far however :KS

---

### Post by Ub1476 on 2007-12-05
Take a look at post 6 and 7 on this [thread]("http://ubuntuforums.org/showthread.php?t=608547").

I suppose your graphic card is ATI hd2400 right?

---

### Post by FuturePilot on 2007-12-05
> **Xanturia said:**
> when i put this in the terminal i get this:

matt@matt-laptop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

don't forget, i am an utter newb.

How do i install the drivers?
as in, step by step please? :)

Thanks for your help so far however :KS
System>Administration>Restricted Driver Manager. What card do you have though?

---

### Post by Xanturia on 2007-12-05
i have no idea what my graphics card is :( how do i find out?

---

### Post by Ub1476 on 2007-12-05
```
lspci | grep VGA
```

---

### Post by maharbA on 2007-12-05
> **Xanturia said:**
> i have no idea what my graphics card is :( how do i find out?

I found (on these forums) a pretty neat command that does a full hardware scan and makes an HTML file that's fairly easy to read. You can keep the file for future reference.

Just copy and paste this into a terminal (remember, in a terminal, ctrl+shift+v is paste -- not just ctrl+v):
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
Now you have a file called "hardware_info.html" in your home folder.
Check about 1/3 of the way down for something with the ID "display"

---

### Post by Xanturia on 2007-12-05
okeydokey, this is the results of "display"

id:	
display
description: 	VGA compatible controller
product: 	ATI Technologies Inc
vendor: 	ATI Technologies Inc
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pm pciexpress msi vga bus_master cap_list
configuration:	
latency	=	0


and this is the result of the other thing i did:
matt@matt-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581


Thanks for your help guys/gals.

---

### Post by darkangl494 on 2007-12-05
Hey. I have a brand new  TOSHIBA Satellite A205-S7458 NoteBook and am having the same problem. Every time I try to enable custom effects it says "Effects cannot be enabled" This is the information for Graphics listed under my laptop specifications: 
[CENTER]Graphics
GPU/VPU 	Intel GMA X3100
Graphic Type 	Integrated Card[/CENTER]
How can I get the custom effects to work?

---

### Post by maharbA on 2007-12-06
@Xanturia,

Clearly you have an ATI card. Bummer -- ATIs are currently not well supported. The good news is that they are getting better. For example, it used to be that you needed to run an XGL session to use Compiz/Desktop Effects. The newer ATI drivers now support AIGLX, which means no more XGL needed (yay!) -- I believe this is true for both OS and proprietary drivers, someone correct me if I'm wrong.

Anyway, for some reason we can't autodetect your exact card model. You should be able to look this up somewhere, though (Dell, for example, keeps system specs on their website). It's just a minor hurdle.

Assuming you can find/detect your card model, your options right now are:
1. Use open-source drivers that were auto-setup when you installed Ubuntu AND set up an XGL session (search the forums, there's a good how-to out there).
2. Use Restricted Hardware Manager to install Ubuntu-supported proprietary drivers AND set up XGL (probably better performance -- but not open-source).
3. Install the latest open-source driver with AIGLX support (probably a good how-to out there somewhere)
4. Install the latest proprietary driver with AIGLX support.

If you're gonna go with #4 (that's the setup I have, BTW) try a program called Envy by Alberto Milone ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ). It's designed to detect your card and install the latest driver. It's very easy to use, and Desktop effects worked for me immediately afterwards. (you can specify your card model if Envy can't detect it and you have found that info.)

Sorry for the long post, best of luck. :)

---

### Post by tollboy on 2008-01-12
hi friends 
i am using hp pavillion dv 2519
i am having the same problem.............
the out put of commands 
compiz --replace is```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
```
and for
lspci | grep vga is ```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```
i know my motherbored is black listed
is it mean that i cn not yake joy of any enhanced graphics stuffs such as desktop effects and various themes?????????
and also hw could i know that i have my driver for graphic card or not ???????
please help:confused:

---

### Post by giok13 on 2008-01-12
wait i thought the intel cards were black listed not the mother boards??

and u can get compiz but itll suck. ive been trying for days and ive goten it to work but the soon as i shutdown and reboot everything just gets messed up. it totaly destrous ubuntu. ive had to reinstall it 4 times already. in other words dont even bother unless u have a difrent intel card. and i just remembered i do :) hopefully its not Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

hmmm, actually i have 2 intel cards

---

### Post by Zibeb on 2008-01-12
I have a Toshiba Satellite A215, and I had to do this to get Compiz working. First, go to System -> Administration -> Restricted Drivers Manager and enable any video card drivers you find.

After this, open a terminal and type

```
sudo apt-get install xserver-xgl
```

After this, you may need to edit your xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

Go to the very bottom, and you may see this:

```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

If you do, change "0" to "1"

Hope that helps.

---

