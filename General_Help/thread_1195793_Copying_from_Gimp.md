---
title: "Copying from Gimp"
date: 2009-06-24
forum: General Help
---

### Post by Blue Wolf on 2009-06-24
Hey,

I'm using Gimp to make a selection from a large image (3872x2592), the selection is like 3000x100 pixels. I copy this and paste it into ImageJ for a profile analysis.

The problem I'm having is that it take around 35seconds for the selection to be pasted into ImageJ.
As I have a to repeat this for about 50 to 100 images its really slowing me down!

I've updated ImageJ to 1.42, I'm running Intrepid on a 2.13GHz intel dual core machine with 3Gb RAM.


Can anyone give me hand with this?

Cheers!

---

### Post by LoneWolfJack on 2009-06-24
can't really help you with the delay problem, but why not use imagemagick? it can do the cropping automagickally for all your images.

```
convert -crop 3000x100+0+0 file.jpg newfile.jpg
```

where +0+0 represents the offset. use mogrify instead of convert to perform the operation on all jpg files in a folder:

```
mogrify -crop 3000x100+0+0 *.jpg
```

note: the files will be overwritten when using mogrify.

---

### Post by Blue Wolf on 2009-06-24
Thanks LoneWolfJack, 

I'll give that a go, will obviously have to use gimp first to work out the range to select, then that should work great.

---

### Post by LoneWolfJack on 2009-06-24
you can also do something like this if it suits your purpose...

```
convert -crop 3000x100+0+0 -gravity center/northwest/nort/northeast/west/etc.
```

center will crop from the center of the image, nortwest from the left top, etc., but note that the offsets will still work so if you do +100+100 with gravity northwest, the image will be cropped at top left but offset by 100x100 pixels.

btw, having given it another thought, your problems may be due to low disk performance. happen to have a cheap drive?

---

### Post by Blue Wolf on 2009-06-24
Just had a go with some of my images, it works incredibly well :D

Thanks very much! AND because I can open them in ImageJ as a sequence there's no copy/paste delay issue :) 

Yeah, I'm a PhD student and this rig is one of the lab machines from Dell so I guess the HD is nothing special! Still its awesome my supervisor has let me run Ubuntu.

Thanks again mate

---

