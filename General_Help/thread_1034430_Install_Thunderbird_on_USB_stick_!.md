---
title: "Install Thunderbird on USB stick !"
date: 2009-01-08
forum: General Help
---

### Post by Dutch on 2009-01-08
Hi tried to install mailclient Thunderbird on a USB stick.
First I downloaded the program through [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/) on the USB stick in file Thunderbird.

Then did tar -zxvf thunderbird-2.0.0.19.tar.gz
and cd thunderbird and then ./configure  but the reaction is"
"bash: ./configure: unknown file"

When I selected the shellscript Thunderbird in the Thunderbird file
the program started. But NOT on the USB stick.

The Thunderbird programm is installed on the main HD !
And it works perfect.

How can I move everything to my USB Stick ?(media/BRIEVEN_USB)


Peace,

Dutch.

---

### Post by bodhi.zazen on 2009-01-08
I do not know the answer to your question, but may I suggest portable apps :

[http://portableapps.com/](http://portableapps.com/)

They run in wine on Linux (at least the ones I have tested so far) as well as Windows.

---

### Post by bodhi.zazen on 2009-01-08
I do not know the answer to your question, but may I suggest portable apps :

[http://portableapps.com/](http://portableapps.com/)

They run in wine on Linux (at least the ones I have tested so far) as well as Windows.

---

### Post by jgoguen on 2009-01-08
You could also create a script to force Thunderbird to use a profile that's on your USB key.  This script should do it (assuming you run it from the USB key of course):
```
#!/bin/bash
exec ./thunderbird -profile ./myprofile/
```Copy that to the same directory as the thunderbird script, create a directory named **myprofile** in that directory, and that should work.  I haven't fully tested this though, so if you have any problems please let us know so we can fix them up for you :)

Alternatively, Bodhi's idea would work as well.  Sometimes the fonts are a little funky, but it works great and lets you use the same USB stick sharing the same program and profile data on both Linux and Windows systems.

EDIT: Regardless of how you do it, when running from a USB stick you should [compact your folders](http://kb.mozillazine.org/Thunderbird_:_Tips_:_Compacting_Folders) regularly.

---

### Post by dcstar on 2009-01-08
> **jgoguen said:**
> 
.........
EDIT: Regardless of how you do it, when running from a USB stick you should [compact your folders](http://kb.mozillazine.org/Thunderbird_:_Tips_:_Compacting_Folders) regularly.

USB sticks have a finite lifetime which is shortened by the amount of write cycles, so I would contend that the last thing you want to do is perform more write cycles by regularly compacting folders on it.

---

