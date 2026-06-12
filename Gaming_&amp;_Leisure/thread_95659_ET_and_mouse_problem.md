---
title: "ET and mouse problem"
date: 2005-11-27
forum: Gaming &amp; Leisure
---

### Post by ivanhoe on 2005-11-27
My mouse is working fine till i connect to the server and then it goes mad. Can't see cursor and i allways look down. Must say that i am new in linux so be patient.

---

### Post by endy on 2005-11-27
In the console see what "in_dgamouse" is set to, if it's set to 1 or 2 try setting it to 0 and restart ET.

You may need to run it from the command line like so:

```
et +set in_dgamouse 0
``` 
If this works, I'd look into getting DGA working because IMHO it's better. You could add the following to your xorg.conf file and restart X then try ET with "in_dgamouse 2" and see what you think, you'll probably have to reset your sensitivity.

```
gedit /etc/X11/xorg.conf
``` and paste the following lines within the "Module" section near the top:
```
    SubSection  "extmod"
        Option    "xfree86-dga"
    EndSubSection
``` 
For example, my module section looks like this:
```
Section "Module"
    Load    "GLcore"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
#    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"

    SubSection  "extmod"
        Option    "xfree86-dga"
    EndSubSection

EndSection
```

---

### Post by ivanhoe on 2005-11-27
THX, it was set to 0, and then i tried with 2 and it worked. So i played for a while and after about 5-10 min ET freze so i had to hard restart. I think thats something about sound so i'll check to see if there are some posts about it. Thanks again. Do you happen to know how to make this permanently, not to type "et +set in_dgamouse 2" all the time?

---

### Post by endy on 2005-11-28
Yep, you can save the setting in an autoexec.cfg file:

```
echo "seta in_dgamouse 2" >> ~/.etwolf/etmain/autoexec.cfg
```

---

