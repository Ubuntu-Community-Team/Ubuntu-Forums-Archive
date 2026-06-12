---
title: "Sceenshot as JPEG?"
date: 2010-01-23
forum: Desktop Environments
---

### Post by kahumba on 2010-01-23
Hi,
Is it possible to change **the default screen shot app** from  Ubuntu to produce JPEG images instead of PNG?
The problem: it produces too large PNG images, close to 1MB (ridiculous!), when I convert it to JPEG I get an image of about 90KB (that's huge! saving 10x space, it also opens faster!) **with no visible difference from the PNG one**.

so, is it possible?

---

### Post by sportfreak2020 on 2010-01-23
well while you save the screenshot and it suggests you to just enter a name with a .PNG extension, change it to a .jpeg extension..

and voila...you have an .jpeg extension image file

i have noticed that it saves a larger file for the jpeg as well i guess you need to look into more in that area..

will explore more on that one..

---

### Post by howefield on 2010-01-23
A workaround would be to use the convert command after taking you png screenshot, (part of the imagemagick suite).

In a terminal type

```
convert nameoffile.png nameoffile.jpg
```

Quick and easy.

---

### Post by chewearn on 2010-01-23
> **sportfreak2020 said:**
> well while you save the screenshot and it suggests you to just enter a name with a .PNG extension, change it to a .jpeg extension..

and voila...you have an .jpeg extension image file

i have noticed that it saves a larger file for the jpeg as well i guess you need to look into more in that area..

will explore more on that one..

You could change ".png" to ".jpg" but it will still spit out a png file.  Generally, the extension is irrelevant w.r.t. file type in Linux.

---

### Post by sportfreak2020 on 2010-01-23
hmm dats strange coz i just did a screenshot on my ubuntu 9.10 machine.i did the thing where i change the .png to .jpg and it did save a file..

and now after i right click that image file namely "screenshot.jpg"

and select properties it gives me 

Type: JPEG image (image/jpeg)

does it still mean ita .png file???:confused:

---

### Post by kahumba on 2010-01-23
No, changing the extension is not even a solution cause it still is a PNG image with a JPEG extension.
Looks like I have to replace the application itself.
Unfortunately this cant be filed under "paper cuts" cause it's not a one liner fix.

---

### Post by howefield on 2010-01-23
Just trying out another way, using the command line and the imagemagick suite of apps.

From a terminal type

```
import screenshot.jpg
```

and then click and drag your left mouse button over the area you want for the screenshot.  

You'll find the jpg in your home folder.

---

### Post by stinkeye on 2010-01-23
Just install [[COLOR="DarkRed"]_**shutter**_[/COLOR]]("http://shutter-project.org/downloads/") and change the save format in preferences.

---

### Post by phillychease on 2010-01-23
or put it GIMP and save as jpeg

---

### Post by tomdkat on 2010-01-23
Or, take the screenshot WITH GIMP.  I do that frequently.

Peace...

---

### Post by chewearn on 2010-01-24
> **sportfreak2020 said:**
> hmm dats strange coz i just did a screenshot on my ubuntu 9.10 machine.i did the thing where i change the .png to .jpg and it did save a file..

and now after i right click that image file namely "screenshot.jpg"

and select properties it gives me 

Type: JPEG image (image/jpeg)

does it still mean ita .png file???:confused:


Mmm.  That seems to be a Nautilus bug.  Under Properties > Basic tab, the "Type" mentioned there followed the file extension.  But Properties > Image tab gave the actual file type detected by mime magic.

---

### Post by Ginsu543 on 2010-01-24
You can also use Scrot, which is a command-line program available in the repositories to take screenshots. You select whether you want the screenshot to be taken as a jpg or png format by simply changing the extension in the name. For example, "scrot -d 5 -c image.jpg" will take the screenshot with a five second delay (with a countdown) and save it in jpg format with the name "image.jpg." On the other hand, "scrot -d t -c image.png" will do the same but save it in png format.

---

