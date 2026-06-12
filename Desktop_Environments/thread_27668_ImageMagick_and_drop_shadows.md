---
title: "ImageMagick and drop shadows?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by marcadams on 2005-04-17
Hi;

I have been searching the web for an example how to add a drop shadow to an image - to make images look nicer when I email them.

However, I have been unable to find any examples on how to use the shadow command in ImageMagick.

I was hoping someone has already done this, and could post the command line.

Many thanks
Marc

---

### Post by Stormy Eyes on 2005-04-17
Couldn't you use the GIMP instead? It has drop-shadow plugins.

---

### Post by smoon on 2005-04-17
I once put this together for my FVWM configuration:
```
convert -depth 8 -threshold 0 -negate <input.png> -bordercolor 'rgba(255,255,255,255)' -border 20x20 -gaussian 0x7 -shave 15x15 - | composite -geometry +2+2 -gravity northwest <input.ext> - <output.ext>
```
Just fiddle with the values to fit your needs.

---

### Post by marcadams on 2005-04-18
Hi Stormy Eyes;

The reason I want to use imageMagick, is I wanted to:
1) convert a directory of images
2) I want to resize and reduce the quality of each image
3) Add a drop shadow to each image

It initially looked like this sort of batch processing would be easier with ImageMagick - rather than learning how to script with GIMP


Hi smoon; 

I tried your script, but could not get it to work  :-| 
I replaced the <file names>, with one in the same directory, but no joy.
I will try again, tomorrow.


Cheers
Marc

---

