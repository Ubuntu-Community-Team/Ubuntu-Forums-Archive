---
title: "GIMP and images (compression)"
date: 2005-12-19
forum: Desktop Environments
---

### Post by duminas on 2005-12-19
**EDIT:** Fixed filesize of the master (5.2->5.5).

Am I missing some secret configuration directive, or is The GIMP as bad as it seems at compressing images, compared to some other programs I've used?

For instance, I've got a 240x240 image, and the following happens on two platforms--please note that the master we are working off of is 5.5 KB:

**Photoshop CS2 (2003)**
- Saved as an 8-bit PNG. Down to 4.48 KB.

**The GIMP (Breezy)**
- Saved as a JPG, quality 85. Up to ~14 KB.
- Saved as a PNG, compression 9, no extra options. Up to 11.0 KB.

Now, this isn't such an issue with files on my PC itself, but as I do web work, it becomes rather problematic when files are so massive. As a point of reference, for 1000 visitors, the difference between 4.48 KB and 11 KB--6.52 KB--is a little over 6.5 MB of bandwidth for the aformentioned 1000 visitors. Neglible on its own, but please consider that we have many images on this site I need to re-compress, and I cannot do this if The GIMP is doing this badly at compressing files.

[size=1]And for anyone still using dialup, even 1 KB of difference makes a rather large difference in speed.[/size]

Such being said, does anyone know what the cause for this may be or any other imaging applications which could do a better job of it?

Thanks.

---

### Post by poptones on 2005-12-19
If you don't post the images in question no one can look at them to see where things are going wrong for you.

---

### Post by duminas on 2005-12-19
As it happens with *any* image I try, even an image which is solidly one color, like white, I felt that was not necessary. But since you asked, see the attachment. Might I add it's only using ten colors?

NOTE: It's showing as 240x480 for some odd reason. Chop the bottom half off (240x240 block) and try it from there.

---

### Post by poptones on 2005-12-19
Ummm... it's kinda impossible to compare if you only post ONE image. 

I have gimp. I do not have photoshop because I do not use windows. If you will post a sample of each that you are talking about then I may be able to help.

Edit: it appears the problem you are having here is you are saving the images as 8 bit png when they are really only 8 color png. Just a sec...

---

### Post by duminas on 2005-12-19
How does it not help?
Perchance you could try doing what I mentioned and see what saving it as a PNG, with no options selected, does to the file? I know how that sounds, so.... ^^
I selected the top 240x240, made a new 240x240 image, and pasted what I chopped on top of this. Or, heck, even trying to save it as a JPEG (Optimized) should demonstrate my problem, though you could not have known this prior since I did not explain it.

Since you're asking, though, see below:

**rmcwbg1.png** Photoshopped (240x480 png8.)
**rmcwbg.png** GIMP'ed (240x240, PNG, no options selected, compression 9.)

---

### Post by poptones on 2005-12-19
Here is your original image (5.5kb) and the version I saved in the proper 8 color mode. There is exactly 0% difference between the two - ecept for filesize, mine being only 3.9kb.

I also have posted two screencaps. One shows the settings I used to convert the RGB24 version of the image you posted back to indexed color and the other shows the difference in palettes between your version of the image and the one I posted (which, I suspect, you will find looks very much like the version photoshop creates).

When you convert to indexed mode make sure you set the number of colors you wish to use. If you just convert to "optimized palette" but leave everything at default you will still create a 256 color image. That is what eats bandwwidth.

---

### Post by duminas on 2005-12-19
I haven't got a clue what that window is in the third image you attached. I've never seen that before, nor can I find it anywhere in the menus by that name. And yes, the fourth one looks very similar, as you suspected.

---

### Post by poptones on 2005-12-19
Here's the second image you posted. From your 10kb, 24 bit color image it has become a 2.9kb 16 color image - with no color or palette loss.

*I haven't got a clue what that window is in the third image you attached.*

Image > Mode > (RGB,Greyscale,Indexed)

The dialog is for conversion from RGB to indexed color.

---

### Post by poptones on 2005-12-19
BTW, if I am understanding things correctly we now have an image thta is nearly 50% smaller than the one you were making in Photoshop. It still has ten colors, and those colors are essentially identical.

You can send me a check for the difference...

---

### Post by duminas on 2005-12-19
Actually, you're quite right in that--a further check would be unnecessary.
Thanks for the help--that's a handy little dialog window.

One last question, though. Can The GIMP (or any program, for that matter) count the number of colours within an image? Unless I'm missing something, The GIMP only goes so far as to show you the palette, but not a number of colours.

---

### Post by poptones on 2005-12-19
With 24 bit color there can be "thousands" of colors - it really doesn't matter how many are there until you begin quantizing color. And you can't tell how many colors are in an image that is quantized until it's been quantized. 

While you can get a good look at overall distributin with the histogram, it's more meaningful just to look at the palette after doing a quantization to 256 colors. If there are lots of similar looking colors try another copy quantized to something less and compare the two. Here's an example of a screencap from Letterman (yes, I have a "thing" for Grinder Girl) at 24 bit color and quantized to 64 color and 16 color, both with floyd-steinberg dithering. Of course, there would be a pretty big difference in filesize between the three. Athough in images like this you can do far more with jpeg compression and by adding more blur to the image, it serves as a decent illustration of comparing quantized image quality.

---

### Post by duminas on 2005-12-19
What I was actually meaning is if any program can give me a textual representation of how many unique colors are within an image--beit something like 4 or 9618. The main reason I wonder about this is to see how many colors an image is using on its own (such as navigation buttons for a certain site--some use 20ish, others upwards of 100), so I'd be able to use that handy window to say how many I wanted (matching the image itself, of course).

If I understand you correctly, you are saying that it is impossible for programs to be able to tell how many unique colors are in an image at the time until you set a limit to the image (such as forcing it down to 8 bit)? Sorry--I'm not much of an image manipulation person, so a lot of this is foreign to me.

[size=1]Grinder Girl's awesome. So is 'Will It Float?'[/size]

---

### Post by poptones on 2005-12-19
It's not impossible, it's just not meaningful. Photoshop will "count colors used" but what difference does it make if it uses 3000 colors or 300 colors unless you know what those colors are? Just show the palette and do a quantization down to 256 colors (the most oyou can have anyway) and see how similar the entries look. More meaningul than that, just quantize the image to a target (16 colors, 32 colors, 128 colors, etc) and see how it looks.

Keep in mind there is no benefit to quantizing colors to something other than a power of two. If you quantize to 50 colors you are still going to need six bits to represent each entry so you might as well quantize to 64 colors.

---

### Post by duminas on 2005-12-19
[QUOTE=poptones]It's not impossible, it's just not meaningful. Photoshop will "count colors used" but what difference does it make if it uses 3000 colors or 300 colors unless you know what those colors are? Just show the palette and do a quantization down to 256 colors (the most oyou can have anyway) and see how similar the entries look. More meaningul than that, just quantize the image to a target (16 colors, 32 colors, 128 colors, etc) and see how it looks.[/quote]True enough.
> Keep in mind there is no benefit to quantizing colors to something other than a power of two. If you quantize to 50 colors you are still going to need six bits to represent each entry so you might as well quantize to 64 colors.I take it this is why when I smashed something down to 10 colors, it was so much larger than something using 8, then.

Thanks for all your help.

---

### Post by poptones on 2005-12-19
> I take it this is why when I smashed something down to 10 colors, it was so much larger than something using 8, then.

The way you were doing it was not optimal. If you do not set the palette before saving as an indexed png you are going to make a 256 color image. That means each pixel gets 8 bits whether it needs it or not, so it's going to be larger.

---

### Post by duminas on 2005-12-19
I meant after you pointed out the dialog to me.
I tried with that 240x480 source, indexing it to 10, then another copy to 8. The one that had 10 colors was significantly larger (just under 4 KB compared to the 2.9 otherwise). This is to what I was speaking.

Ah, well.
I'm glad to know how to do this right, now.

---

