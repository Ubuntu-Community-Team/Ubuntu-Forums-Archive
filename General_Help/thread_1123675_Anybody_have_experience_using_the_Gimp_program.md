---
title: "Anybody have experience using the Gimp program?"
date: 2009-04-12
forum: General Help
---

### Post by Camilia on 2009-04-12
Anybody have experience using the Gimp program?

I have been trying to use it to copy and paste parts of a picture onto my picture. The pictures pasted become very small. Is there a way to enlarge them?

---

### Post by Bucky Ball on 2009-04-12
[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)

[http://gimp-tutorials.net/](http://gimp-tutorials.net/)

---

### Post by blackened on 2009-04-12
It's probably a difference between the default zoom levels of the images. GIMP will often set the default zoom for large images at 1:2 or 1:3. Make sure both images zoom levels are set to 1:1 before you cut and paste.

If, after getting the zoom issue sorted, you find that the difference in image resolution is still a problem, then you may have to shrink the larger of the two before you cut and paste.

---

### Post by Camilia on 2009-04-13
> **blackened said:**
> It's probably a difference between the default zoom levels of the images. GIMP will often set the default zoom for large images at 1:2 or 1:3. Make sure both images zoom levels are set to 1:1 before you cut and paste.

If, after getting the zoom issue sorted, you find that the difference in image resolution is still a problem, then you may have to shrink the larger of the two before you cut and paste.

I found a video explaining it!

Well I found the zoom but don't see where to change the ratio.

---

### Post by blackened on 2009-04-13
> **Camilia said:**
> ...Well I found the zoom but don't see where to change the ratio.

Right-click on the image, select "View" and then "Zoom", then choose the correct zoom level.

---

### Post by Camilia on 2009-04-13
> **blackened said:**
> Right-click on the image, select "View" and then "Zoom", then choose the correct zoom level.

Did that yet still picture I cut and paste into mine is very small. Guess 1 day will have to practice with gimp tutorials.

---

### Post by aaronp on 2009-04-14
Work out the pixel ratio in your main picture (usually at the top of the window)

Do a selection box in the area where you want to paste something and determine how many pixels this area is (this will be in the status bar)

Then go to your other picture and do a selection on the part that you want to paste. Look at how many pixels this is (again in the status bar)

You might find that one of your pictures is a different pixels-per-inch than the other one.

example - Say you have two images - 1 is 72ppi and the other is 300ppi.
A 1 inch square in 72ppi = 72x72 = 5184 pixels
A 1 inch square in 300ppi = 300 x 300 = 90000 pixels

Therefore if you copy/paste 1 inch from the lower res image to the higher res image it will occupy far less than 1 inch of space.

Best thing to do would be to scale down the picture with the higher resolution until you can get the copy/pasted selection to look the right size in comparison.

hth
Aaron

---

### Post by aaronp on 2009-04-14
a bit more...

you might find that the scaling process means one of your pictures will be too small to use for what you need. Unfortunately this will not be something you can fix unless you can get a higher resolution version of the image (i.e. the image that has lower-res)

---

### Post by Camilia on 2009-04-14
> **aaronp said:**
> Work out the pixel ratio in your main picture (usually at the top of the window)


Went to image - print size and made the width, height, and resolution the same in both pictures. Still the pasted pictures is very small.

---

### Post by 3rdalbum on 2009-04-14
When you paste the small picture in but BEFORE you click anywhere else, go to the Layer menu and choose "Scale Layer". This will allow you to scale the floating selection.

You could also create a new layer before pasting the new image in, then pressing Enter to attach the new image to the new layer. Then you can scale the layer at your leisure.

---

### Post by Camilia on 2009-04-14
> **3rdalbum said:**
> When you paste the small picture in but BEFORE you click anywhere else, go to the Layer menu and choose "Scale Layer". This will allow you to scale the floating selection.

You could also create a new layer before pasting the new image in, then pressing Enter to attach the new image to the new layer. Then you can scale the layer at your leisure.

Can't get the 1st option to work.

Could you give me the steps to the second option?

I am a beginner I only know how to cut and paste. I know what a pixel is but don't know what I need to get it to look right.

---

### Post by aaronp on 2009-04-14
Can you tell me what size (inches or mm) both your images are and what the resolution of both your images are? (before you changed them)

Then tell me how big the selection is that you want to cut and paste.

---

### Post by tamas305 on 2009-04-14
Does GIMP have a patch tool (like in Photoshop)? Personally I like GIMP better than Photoshop and other Adobe crap, they are extremely slow and filled up to the top with a bunch of crap you'll never use. Appropriately, Adobe charges a gazillion dollars for the master collection. Brilliant.

-tamas305

**********************************************************
java + eclipse = happiness

---

### Post by aaronp on 2009-04-14
The clone and heal tools are very similar to patch but not exactly the same.
There are some great tutorials around on how to retouch with GIMP and I've achived some great results in the past. Unfortunately I haven't got any bookmarked so I'll suggest you google it and if I come across the ones I have used I'll post a url for you.

---

### Post by Camilia on 2009-04-14
> **aaronp said:**
> Can you tell me what size (inches or mm) both your images are and what the resolution of both your images are? (before you changed them)

Then tell me how big the selection is that you want to cut and paste.

Cutting and pasting plant 2 x 6 inches onto picture of my aquarium. 

One of the pictures copying from is in inches:
3.27 w x 1.32 h. Resolution pixels 2.8

Main picture for pictures to pasted into is in inches;
w28.4 x h 21 pixels. Resolution pixels 72

I have changed the pixels and size to match still only get a small picture pasted.

Main picture
[IMG]http://farm4.static.flickr.com/3412/3442406659_71827613f5.jpg[/IMG]

Picture copying from
[IMG]http://farm4.static.flickr.com/3578/3418912995_955e84ae12.jpg[/IMG]

---

### Post by aaronp on 2009-04-14
The first picture is only 2.8 ppi?
This doesn't seem right as there would be only a handful of pixels in that image, it would just look like a few squares.

Is it 28ppi?

You can go to Image menu and then Image Propoerties at the bottom to get this info.

---

### Post by jacobam on 2009-04-14
Well the issue you are most likely having is the part you have selected is of a lower resolution and when you put it into the other image it small due to your image being higher resolution. Your best option is to scale the image but you will lose a lot in the way of quality. If you have any other questions fell free to ask me as I deal with desktop publishing every day (gimp, scribus,inkscape, photoshop,in-design, etc)

---

### Post by Camilia on 2009-04-14
> **aaronp said:**
> The first picture is only 2.8 ppi?
This doesn't seem right as there would be only a handful of pixels in that image, it would just look like a few squares.

Is it 28ppi?

You can go to Image menu and then Image Propoerties at the bottom to get this info.

oops that was 2.8 per mm it is 71 per inch. The main picture is 72

---

### Post by Camilia on 2009-04-14
> **jacobam said:**
> part you have selected is of a lower resolution and when you put it into the other image it small due to your image being higher resolution. 

No they are close. Main has 72 per inch. Other has 71 per inch.

I find the icons to scale but uncertain how to get it how I want it. What do I increase?

---

### Post by aaronp on 2009-04-14
ok so the resolutions are almost the same which is good.
the problem now is that the photo you want to paste is only a few inches wide and high, whereas the other one is 20+ inches high and wide.

this means you need to scale down the big image and/or scale up the small image.

issues:
scaling down the big image means your final image size will be small. if you are looking to print it or have it as a desktop background etc. it may be too small. if it is just for a smallish picture on a website then this will be ok

scaling up the small image will degrade its quality quite badly. this is probably not really an option.

open both the images, then on the view menu zoom them both to 100% and you will see the difference. you can then scale the larger on down until you are happy with the sizes between them and do your copy/paste.
if this ends up with a picture that is big enough for what you need it for then it's a good result. if not, you may be out of luck or if possible need to take another picture of the one you want to paste, at a higher resolution or image size

hth
Aaron

---

### Post by Camilia on 2009-04-15
> **aaronp said:**
> 
Open both the images, zoom them both to 100% and you will see the difference. You can then scale the larger one down.
Aaron

I did this and it worked!!=D> 

Thanks Aaron!!

I am just doing to get an idea where I want my plants, thus the quality of the image isn't important.

---

### Post by aaronp on 2009-04-15
cool, happy to help.
Gimp is a pretty powerful tool for a free app, but a fairly steep learning curve.

---

### Post by blackened on 2009-04-15
> **aaronp said:**
> cool, happy to help.
Gimp is a pretty powerful tool for a free app, but a fairly steep learning curve.

Ya' know, I hear people say that all the time, but I just disagree. I think that once you understand the fundamentals of computer graphics then the program you use becomes alot less important. The skills you learn in GIMP translate very easily into all of the other programs I've used, including Inkscape and Illustrator to some extent.

By understanding how and why things work, you gain a greater understanding of how best to manipulate those things to achieve a desired result. You absolutely cannot beat fundamental granular knowledge and control.

---

### Post by aaronp on 2009-04-15
> **blackened said:**
> Ya' know, I hear people say that all the time, but I just disagree. I think that once you understand the fundamentals of computer graphics then the program you use becomes alot less important. The skills you learn in GIMP translate very easily into all of the other programs I've used, including Inkscape and Illustrator to some extent.

By understanding how and why things work, you gain a greater understanding of how best to manipulate those things to achieve a desired result. You absolutely cannot beat fundamental granular knowledge and control.

You're spot on there. I think the learning curve comes from people who learn the other packages first and then try to learn GIMP next.
Starting with GIMP in uni before I started using any other graphics apps was fantastic because I'd already learnt the fundamentals by using GIMP first. These were then easily applied to the other apps.

---

