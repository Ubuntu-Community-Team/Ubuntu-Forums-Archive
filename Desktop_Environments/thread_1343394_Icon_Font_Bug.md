---
title: "Icon Font Bug"
date: 2009-12-01
forum: Desktop Environments
---

### Post by magusjonny42 on 2009-12-01
Ive been having this problem were the text under an Icon will blur when highlighted. Ive tried cleaning the fontconfig cache manually and with commands
```
sudo /etc/usr/fc-cache
/etc/usr/fc-cache
```but the problem still persists.

Any help is much appreciated.

Links are for images showing the bugged text.
Before: [http://img687.imageshack.us/img687/5082/beforeu.png](http://img687.imageshack.us/img687/5082/beforeu.png)
After: [http://img687.imageshack.us/img687/2489/afterhc.png](http://img687.imageshack.us/img687/2489/afterhc.png)

---

### Post by magusjonny42 on 2009-12-03
Bugged text goes away when I disable ¨anti-aliasing¨ in Settings > Appearance.

I would like to have it work with the setting on, my crappy laptop tends to render things torn with it off.

Is this a software or hardware problem? How do I narrow down what is wrong?

Cheers :)

---

### Post by WorLord on 2009-12-03
[QUOTE=magusjonny42;8423155]Ive been having this problem were the text under an Icon will blur when highlighted. Ive tried cleaning the fontconfig cache manually and with commands
```
sudo /etc/usr/fc-cache
/etc/usr/fc-cache
```but the problem still persists.

...I'm not sure this code actually does anything at all.  o.O

---

### Post by magusjonny42 on 2009-12-05
I believe its meant to run the fc-cache program, ran the program by clicking on it as well. It was suggested in another forum for a different problem and actually worked until I reformatted with Karmic. I am going to go back to Jaunty.

Also thinking of re-posting this problem.

---

### Post by kerry_s on 2009-12-06
> **magusjonny42 said:**
> I believe its meant to run the fc-cache program, ran the program by clicking on it as well. It was suggested in another forum for a different problem and actually worked until I reformatted with Karmic. I am going to go back to Jaunty.

Also thinking of re-posting this problem.

the command is: **sudo fc-cache -vf**

what fonts do you have set in the settings?

---

### Post by magusjonny42 on 2010-01-12
Tried using numerous differant fonts from Arial, Times New Roman, Sans, Serif, Century Schoolbook.

Oh and I should mention that the bug only happens on the desktop icons, others like the icons within my file manager are not affected it seems.

Lastly the same thing is happening within CrossOver, my cross platform app. Pics of those buged font effects are bellow.

---

