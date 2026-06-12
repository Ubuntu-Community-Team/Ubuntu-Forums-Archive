---
title: "R/X11 plotting error"
date: 2007-01-16
forum: Education &amp; Science
---

### Post by WebDrake on 2007-01-16
Hello all,

I'm trying to teach myself how to use R, which I've installed on my Edgy-running Dell laptop.  Unfortunately the plot command does not work.  If I type,
```
plot(x,y)
```
I get an error message,
```
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct
```

Google didn't come up with much help, so does anyone have any suggestions for how to solve the problem?  I don't think I've done anything to modify xorg.conf from the default.

Thanks in advance,

    -- Joe

---

### Post by akniss on 2007-01-16
The problem is due to R looking in the wrong place for fonts.  See the post below:

[http://www.ubuntuforums.org/showpost.php?p=1683538&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1683538&postcount=14)

---

### Post by WebDrake on 2007-01-16
> **akniss said:**
> The problem is due to R looking in the wrong place for fonts.  See the post below:

[http://www.ubuntuforums.org/showpost.php?p=1683538&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1683538&postcount=14)

Thanks!  I did search the fora, but must have missed that one.... has anyone reported this as a bug that should be fixed?

---

### Post by akniss on 2007-01-16
> **WebDrake said:**
> Thanks!  I did search the fora, but must have missed that one.... has anyone reported this as a bug that should be fixed?

Perfectly understandable that a forum search didn't help in this case.  It is quite difficult for all of us R users to figure out what exactly we should use as search terms!  I'm not sure if this has been reported as a bug or not... I know it has been discussed at least twice on these forums, as well as in the R lists.  I guess I'm not sure where the problem originated... with R? Xorg? Edgy?  Maybe LaserJock can figure out who should be notified, He seems to stay on top of things like this.

---

### Post by WebDrake on 2007-01-16
> **akniss said:**
> I guess I'm not sure where the problem originated... with R? Xorg? Edgy?  Maybe LaserJock can figure out who should be notified, He seems to stay on top of things like this.
Well, as far as I can see, the error was in xorg.conf, which contained wrong path names for font locations.

While we've got a moment, since I'm a novice R user, can you suggest any useful resources for learning/becoming proficient with R, besides the main website's documentation?

Thanks again,

     -- Joe

---

### Post by akniss on 2007-01-16
There are some good links here:
[http://www.ubuntuforums.org/showthread.php?p=717367#post717367](http://www.ubuntuforums.org/showthread.php?p=717367#post717367)

If you are willing to buy a book to learn R, I *HIGHLY* recommend Modern Applied Statistics with S by Venables and Ripley.

---

### Post by WebDrake on 2007-01-17
> **akniss said:**
> There are some good links here:
[http://www.ubuntuforums.org/showthread.php?p=717367#post717367](http://www.ubuntuforums.org/showthread.php?p=717367#post717367)

If you are willing to buy a book to learn R, I *HIGHLY* recommend Modern Applied Statistics with S by Venables and Ripley.
Fantastic!  Thank you very much. :KS

---

