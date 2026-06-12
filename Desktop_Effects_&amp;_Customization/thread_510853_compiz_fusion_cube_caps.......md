---
title: "compiz fusion cube caps......"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by techno-mole on 2007-07-27
is there a way to change the default image on the top cube cap (compiz fusion) i did read some where that the bottom cube cap doesnt work at the moment.
anyway back to the top cube cap, the default is the ubuntu logo, ive tried changing the image using the settings and selecting another image, but nothing shows up, ive tried putting the image in the compiz folder (usr/share/compiz) but still nothing.
ive deleted the default cap image, but it still displays ? ive also tried editing the cube.xml file and telling it to use another image, but the default one still displays, so im guessing compiz is being told to use that image somewhere else (maybe another xml file)
what i dont understand is why it still displays if its not there anymore ?
any help will be appreciated.
cheers

---

### Post by Waappu on 2007-07-27
Hi

Sound very strange.

This isn't good solution and posibly not work, but try place new picture same folder and same name where default one is

---

### Post by buzzbo on 2008-01-22
I realize this is an old post, but I thought I'd respond, because I was able to get this to work with the following:

* Make sure Cube Caps is enabled
* Under behaviour, enable all (you can play around with these to see differences)
* Make sure the file type is enabled under Image Loading (jpeg / png / svg)
* Resize picture to less than or equal to screen resolution.
* Make sure the pictures are readable by all (i.e chmod 644 [filename])
* Make sure any parent directories are readable and executable (chmod 755 [dirname])
* Make sure /path/to/file is correct

Actually I'm not sure that the permissions is essential, but it is a step I took along the way.

Buzz

---

### Post by bharadwaj on 2008-01-22
of course you can after all how can GNU/Linux cant be called without it ;) very easy one.
Go to the Advanced Desktop effects enable cube caps under the sub menu of it there is the answer for your question. In the appearences tab now all you need to do is hang with some more bubble gums and move your butt for new backgrounds ;)

---

### Post by tk471 on 2008-05-08
Hello folks, I just updated files '/usr/share/compiz/compizcap.png' and '/usr/share/compiz/fusioncap.png' with new artwork (kept a backup of the originals), to update my cube caps.  I'm using Gnome 2.22.1 in Ubuntu Studio 8.04.  I think you can point to new images to use from 'Advanced Desktop Effects Settings' control panel as well (probably were Buzz went).
I tried to take a screenshot (didn't post, oh well).
Stormtrooper TK471


... duh, you can change the images right in the 'Advanced Desktop Effects Settings', it took me a bit to figure out that clicking on the icons brings up more configuration menus, including being able to choose your own cap images.

---

### Post by Herculis on 2008-06-08
Hey,
Cube Caps seems to have an issue with too large images. My images wouldn't show up, so I reduced their size from 2592*1944 to 1600*1200. Now they show up. I also changed them from jpg to png, but I don't think that makes a difference.
Hope this helps

---

### Post by OviloN on 2008-06-17
Hi folks,

I'm working on a Debian machine, but it should be same.
If "Cube Reflection and Transformation" is enabled changing the caps in section "Desktop Cube" won't work. You have to change it in "Cube Reflection and Transformation" in tab "Cube caps" under "Appearance". There you can change both caps.

I also noticed that there's written Debian on the cap itself while rotating, but when I switch to the cap itself it disappears.
Anyone has an idea how to change that text. I don't want to do that but I want to know how I could ;]

Greetz OviloN.

---

### Post by Sphirek on 2008-07-02
wrong post

---

