---
title: "Changing gamma on the desktop"
date: 2007-04-27
forum: Desktop Environments
---

### Post by boris357 on 2007-04-27
Hello. I have installed Ubuntu 7.04 Feisty Fawn and it works real well, so far. I have just one question. The white back ground on any app I open is so bright that I can hardly make out the borders of the apps or the fonts as I type. Is there any way to adjust the brightness or contrast on the desktop? I have tried with the monitor but that dosen't help much.

Thank you.

---

### Post by dentaku65 on 2007-04-27
> **boris357 said:**
> Hello. I have installed Ubuntu 7.04 Feisty Fawn and it works real well, so far. I have just one question. The white back ground on any app I open is so bright that I can hardly make out the borders of the apps or the fonts as I type. Is there any way to adjust the brightness or contrast on the desktop? I have tried with the monitor but that dosen't help much.

Thank you.

[http://gnomefiles.org/app.php/GAMMApage](http://gnomefiles.org/app.php/GAMMApage)

:)

---

### Post by Bashed on 2007-05-11
I'm trying to use that, but look at the ridiculous install instructions"

"Once the downloaded package is decompressed,
just put the file GAMMApage.py somewhere in your path."

This person speaks as if he expects every person to be a linux guru. 

How do I install this?

I ran xgamma -gamma 0.8 and then restored gnome, it reset back to 1.0

---

### Post by renzokuken on 2007-05-11
extract the file with right click, then copy GAMMApage.py to /usr/bin

i.e.

```
sudo cp /path/to/saved/GAMMApage.py /usr/bin
```

then to run the program simply type the following in a terminal

```
python GAMMApage.py
```

---

### Post by Bashed on 2007-05-11
Thanks. Even though I did that, it still resets to 1.0 after rebooting. If I choose "run output on system startup" it pops up this message

> Logon type cannot be determined,
therefore GAMMApage does not know
where to save the gamma-adjusting 
command to be run on X-startup.

The "Save" button will be disabled.
In its place, the "Exit" button will close the program but keep your gamma adjustments until your X-session ends.

See the "HELP" pages for further instructions.

When I close it, I see this in the terminal

> GAMMApage.py:740: Warning: gsignal.c:1741: instance `0x835b5b0' has no handler with id `59'
  self.save_btn.disconnect(self.saveid)


Also, how do I correct brightness and contrast?

---

