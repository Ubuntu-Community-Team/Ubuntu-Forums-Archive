---
title: "i think i broke something..."
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by quiksliver on 2007-07-16
I just installed compiz-fusion and i dont know whether my problem is related or not but I thought I should mention it anyway...

okay so as you can see in the attached picture, the top part of the window does not show up, the bar is not there, the one that can minizem, rezie, close the window etc.

it goes from the top bar directly to the file/edit/view bar..

[http://farm2.static.flickr.com/1184/834135130_92562168df_b.jpg](http://farm2.static.flickr.com/1184/834135130_92562168df_b.jpg)

---

### Post by SkiesOfAzel on 2007-07-17
The decorator is missing, just start compiz with this line :
```
compiz --replace -c emerald &
```
And next time please search a little before posting a question .

---

### Post by jgordon510 on 2007-07-17
If you're using an nvidia card try adding 

```
Option "AddARGBGLXVisuals" "true"
```

to the device section of your xorg.conf file.

---

