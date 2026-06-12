---
title: "i don't get the full screen on my compaq 1700"
date: 2005-12-11
forum: Desktop Environments
---

### Post by pilotcp on 2005-12-11
**Whoops! sorry folks, i thought that i'd repost this in the laptop forum, and i was going to delete this one, and i posted the question in the laptop forums, but i then realized that i don't know how to delete my post!  Sorry!**

Hello all!
so i have had version 5.10 on my compaq armada 1700 and i notice that i don't get the full screen on my monitor...it looks like ther is a 2 inch border of unused monitor space on my computer. kinda like this

|-------------------------------|
|...Black, Empty, Unused  Space..|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|...Black, Empty unused space....|
--------------------------------|

granted, the example above isn't spaced correctly, as everything shows up in a rectangle right in the center of the screen, with equal distance on all sides...

so as you can see, not all my monitor space is being used!
I remember i used to have screen resolution problems before with version 4 ubuntu and i was told to check out a file in /etc/X11/Xf86config-4 to change the screen resolution, so i thought maybe a similar setting was the cause of the problem, but i don't have that file to look in. 
does anybody know how i can strech the screen to use all of the viewable space on the monitor?
or is this maybe a hardware problem? i know that on a normal desktop monitor, there are setting for this kinda thing, but my laptop doesn't seem to have that feature, as it only have brightness and contrast, and a monitor selection button, if you wanted to switch a desktop monitor and the laptop monitor...
oh, and btw, i did try plugging in a desktop monitor, and it worked just fine...

any ideas? opinions? rude remarks ;) ?

also i apoligize to any ascii artists here, you are very good, i am not!

Thanks, Charlie

---

### Post by soulestream on 2005-12-11
its in /etc/X11/xorg.conf

look under "Screen"

you will need to set it to the correct resolution of your monitor.

soule

---

### Post by pilotcp on 2005-12-11
thanks, i'll try that out!

---

### Post by pilotcp on 2005-12-12
ok, so changing the resolution didn't fix the problem...any other suggestions?

---

### Post by M3ta7h3ad on 2005-12-12
in the bios there may be an option concerning "resolution expansion" If you set the resolution to a lower one than a native screen res (most commonly on laptops) then it can expand it to fill the screen, otherwise it just allows it to be centered on the screen which results in what you describe.

---

### Post by pilotcp on 2005-12-13
i'll give that a try...btw, anyone know how to get into the BIOS on my laptop?

---

### Post by arthur_kalm on 2005-12-13
It's very dependent on the laptop. You have to look for some text that will say something about setup when the laptop boots. It will tell you which key to press.

On my HP nc4200 I have to press F11... Try Del, F11 or F12, or just look for the text :P

---

### Post by pilotcp on 2005-12-14
thanks arthur, 
i just found out that on Compaq laptops they put the BIOS in a special partition on the hard drive. 
To access the BIOS i was told that F10 is the button to press, but i wonder if i can get to it, since i had to repartition the hard drive with ubuntu...
hmmm...does anybody know how i can get the BIOS back on my computer?

---

### Post by arthur_kalm on 2005-12-14
[QUOTE=pilotcp]thanks arthur, 
i just found out that on Compaq laptops they put the BIOS in a special partition on the hard drive.[/QUOTE]

I think that the extra partition that you are referring to is the one that stores a backup of Windows in case something goes wrong and you need to re-install Windows. My friend's IBM Think Pad has a specific button to activate this feature, but I believe they put this special partition on most laptops.

As for the BIOS, the BIOS is stored on a ([special ROM (flash memory)]("http://en.wikipedia.org/wiki/Bios")) on your motherboard and is not tied to your hard drive in any way.

So you can just press F10 and you should be allowed into the BIOS with no problem.

---

### Post by pilotcp on 2005-12-15
arthur, i just read that it is an actual partition on the hard drive (which is a bit weird) (check out [http://brezza.iuav.it/~giovan/doc/linux-compaq-armada-1700.html](http://brezza.iuav.it/~giovan/doc/linux-compaq-armada-1700.html))
anyways, i fixed my problem, and i feel like a dope...i had to go into my xorg.conf file and change default depth to 16...d'oh!

---

### Post by Blown Interceptor on 2006-01-01
[QUOTE=pilotcp]arthur, i just read that it is an actual partition on the hard drive (which is a bit weird) (check out [http://brezza.iuav.it/~giovan/doc/linux-compaq-armada-1700.html](http://brezza.iuav.it/~giovan/doc/linux-compaq-armada-1700.html))
anyways, i fixed my problem, and i feel like a dope...i had to go into my xorg.conf file and change default depth to 16...d'oh![/QUOTE]



I am having the same problem with my 1573DM Laptop. I just put Win98 on it and I cannot get a full screen. I looked for that file you mentioned xorg.conf, but could not find it. I have tried installing new drivers, nothing. I can't even reset pixels. They are stuck at 640x480. 

An ideas?:confused: :confused: 


Thanks,
Jason

---

