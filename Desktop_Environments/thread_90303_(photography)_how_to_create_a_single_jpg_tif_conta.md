---
title: "(photography) how to create a single jpg /tif contact sheet?"
date: 2005-11-14
forum: Desktop Environments
---

### Post by megamania on 2005-11-14
One thing that I really miss after having erased my Win hard disk is a program that allows me to create a *single* jpg or tiff picture with the thumbnails of a group of pictures.

This is very handy when I want to have a real (printed) contact sheet of a set of photographs.

Does anybody know of a program that has such a feature? I have been searching for a while, unfortunately with no results...

---

### Post by poptones on 2005-11-14
gqview will do this as will imagemagick. If you take many pictures you will find imagemagick very handy as it allows you to do things like color correct an entire folder of pictures from the command line.

for ALL in `ls -1`;do convert -channel red -gamma 0.9 -channel blue -gamma 1.1 -channel green -gamma 0.8 $ALL $ALL;done

That will replace every picture in a folder with a color corrected version. This is only one example.. basically, you can do anything with it. I've even used it for video NLE.

---

### Post by megamania on 2005-11-15
thank you very much for your suggestions.

actually, I found that gThumb quickly creates a jpg contact sheet. The problem is that you can't really set it up the way you like it (i.e. you can't change the position of each thumbnail), but it's already a good solution.

I'll try the two programs you suggested as soon as I can - meanwhile, since it looks like you use them, do you know if they are more flexible in the creation of such contact sheets?

thanks again!

---

### Post by poptones on 2005-11-15
LOL... yeah, imagemagick is definitely more flexible. Actually, I've never checked the source but I'd bet gthumb uses the imagemagick library to do what it does.

If you learn to use imagemagick, you will be able to do pretty much anything. You can do complete photoshop type operations - blur, composite, offset, color correct... all from the command line. It sounds hard, but you can watch the esults in real time just by making a test image and keeping it open with something like gthumb or gqview; every time you redo the command line it will refresh. When you get the commands you want applied to them all, just put it in a for loop like I showed you in the first response. It's easier than photoshop and much faster.

---

### Post by megamania on 2005-11-16
hmmm. I'll check it out, but it looks like that's one more small-world to discover (that's how I see my whole Linux experience at the moment). :)

thank you for you help!

---

