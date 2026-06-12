---
title: "Make background image in Terminal non-transparent"
date: 2011-06-06
forum: Desktop Environments
---

### Post by nzjethro on 2011-06-06
Does anyone know how to set the background of a terminal to be an image, and not have it slightly transparent? I've set an image as my Terminal background, but now when I open a terminal over other applications I can see those applications through my Terminal background. Is there any way to stop this from happening?

---

### Post by nzjethro on 2011-06-08
Anyone?? Haha. :D

---

### Post by Copper Bezel on 2011-06-09
I'm not seeing what you're seeing. If the image doesn't have an alpha channel and the shading is set to none, I just see the image exactly as the image file looks. Nothing shows through from underneath.

Personally, I like to use an image that has an alpha channel, so that there is transparency, but only the transparency I put in.

---

### Post by nzjethro on 2011-06-10
What is an alpha channel? I have tried .png and .jpg, but both are semi transparent.

---

### Post by Elline on 2011-06-10
Gnome-terminal?
Disable the transparency? There is bar for this.
Maybe disable it first and then selecting an image?

---

### Post by Frogs Hair on 2011-06-10
Gnome Terminal > Edit > Profile Preferences > Back Ground  Disable transparency and add your image from there.

---

### Post by nzjethro on 2011-06-10
Cheers for the replies guys. I've tried disabling transparency, but it remains transparent. Well, I've slid the slider all the way to both ends, and it either makes my image washed out (looks like super low saturation), or completely black. I've attached a couple of screen shots showing what it looks like with the slider at either end and then in the middle, so hopefully I'm being an idiot and missing something simple you guys could help with. Haha.

---

### Post by Elline on 2011-06-11
Wow, that looks glitchy.
Does the original transparency (without and Image) works?

---

### Post by nzjethro on 2011-06-11
Yup, I have (or had at least before I upgraded to Natty) a fully transparent terminal set as a desktop background. Any ideas what might be making it transparent?

---

### Post by Elline on 2011-06-12
Don't really know.

Looks like when you make it fully opaque it shades the text in terminal too, is it? And it doesn't displays background image that way. Really buggy behavior.

---

### Post by nzjethro on 2011-06-12
Yeah it's a bit of a head scratcher. I've given up on it now, and set it to full transparency, and undecorated with devilspie. Good look. I'll leave this thread open in case anyone knows, and someone down the line is looking!

---

### Post by Stanley_00 on 2011-12-23
Hi, I have just found a solution to this. First you have to set your image as transparent with GIMP, 80%-90% is good in my case, save it as png image. Then in gnome-terminal profile, set the transparent to none. Hope this help.

---

### Post by MCJavaMonkey on 2012-02-25
I just recently re-installed Ubuntu 11.10 clean on a new machine and am having this issue. I am using the Ambiance theme, but was using it on my last rig and didnt see this issue. To be clear, the issue I am seeing is that when using a background image in my gnome-terminal, the image itself is not completely opaque. It used to be and the slider on the background tab in profile preferences would shade the image properly. Now sliding will shade, but the image remains semi-transparent. Anyone else? Solution that doesnt involve editing my image?

---

