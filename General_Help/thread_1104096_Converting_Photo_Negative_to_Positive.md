---
title: "Converting Photo Negative to Positive"
date: 2009-03-23
forum: General Help
---

### Post by measekite on 2009-03-23
I am looking for Linux software with a GUI frontend that can convert a negative (tiff, png, jpg) into a viewable positive photograph that can then be edited or printed.

Is there such a thing?

---

### Post by everytimeref on 2009-03-23
You just invert the image.

Gimp will do this easily enough (i'll check the shortcut when I get home). on photoshop it's CTRL+I, so I can't imagine Gimp being any different.

I'm starting a project on Wednesday photographing some early 1900s glass negatives. so I've checked that this works!

---

### Post by Rallg on 2009-03-23
Just inverting the image will not always suffice. That's because a photographic color negative is not simply a mathematical color inversion. On commercial systems (Windows and Mac) software for scanning negatives will have a number of lookup tables for proper color correction, if you know the film that was used.

However, I doubt if you need "industry standard" colors, just whatever looks good. So, using gimp, use Colors > Invert, then Colors > Auto > White Balance. From there, you should be able to make manual color adjustments to your taste. EDIT: This does not work as well as expected.

---

### Post by measekite on 2009-03-24
> **everytimeref said:**
> You just invert the image.

Gimp will do this easily enough (i'll check the shortcut when I get home). on photoshop it's CTRL+I, so I can't imagine Gimp being any different.

I'm starting a project on Wednesday photographing some early 1900s glass negatives. so I've checked that this works!

It did not work.  I scanned in the negative.  When I opened it in Gimp it was the characteristic orange color negative.  After invert it still looked like a negative but it was cyan looking.

---

### Post by Rallg on 2009-03-24
Indeed, inverting a standard color negative (which usually has orange mask) will result in a blue or cyan cast to the positive. Commerical scanning software (for Windows or mac) knows this, and corrects by film type. Old glass negatives may not use that technology.

Again, I suggest using auto white balance as a starting point.

---

### Post by measekite on 2009-03-24
> **Rallg said:**
> Indeed, inverting a standard color negative (which usually has orange mask) will result in a blue or cyan cast to the positive. Commerical scanning software (for Windows or mac) knows this, and corrects by film type. Old glass negatives may not use that technology.

Again, I suggest using auto white balance as a starting point.

Here is what I did and the result:

1.  Opened the orange negative in Gimp

2.  Color>Invert
      Got a cyan looking negative

3.  Did a Color>Auto>White Balance
      Nothing visual happened


I really do not know what to do.  Even if something worked it would not be practical to do this on a hundred scans when using the Windows Epson software works in this particular case.

While I do not favor Windows I am thinking about using virtualbox on a Linux host with Windows and scanning software as a Guest.

I think that this should be added to XSane and made that suggestion but who knows if it was heard.

---

### Post by JKyleOKC on 2009-03-24
My copy of xsane lists nine different types of negatives, including "standard," "agfa," and "kodak." Perhaps these are handled in the backend code rather than in xsane itself...

---

### Post by Rallg on 2009-03-24
If auto white balance did not help...

First, look at JKyleOKC's comment, above. That might be useful.

EDIT: If your browse the Internet, you will see that your question is often discussed (Window/Mac), with solutions using Photoshop for those who don't have scanner color correction. The various techniques used for Photoshop can also be done with Gimp.

Based on comments elsewhere, it seems that the best approach (if you don't have scanner color correction) is to apply auto levels to each color channel separately, then make final adjustments to the combined image.

---

### Post by unutbu on 2009-03-24
From [http://www.graphics-muse.org/artistsguide/?page_id=10:](http://www.graphics-muse.org/artistsguide/?page_id=10:)

> This question came up on the GIMP User mailing list and [sparked an interesting thread]("http://www.mail-archive.com/gimp-user%40lists.xcf.berkeley.edu/msg12289.html").  The summary:  turning the scan of color negative film into color positive is a function of the scanner software and not a function of the GIMP (at least not at the moment).  This is because all brands of film have different yellow and red masks that need to be removed.  XSane can handle this for most film types, as can other scanner software.

---

### Post by measekite on 2009-03-24
> **unutbu said:**
> From [http://www.graphics-muse.org/artistsguide/?page_id=10:](http://www.graphics-muse.org/artistsguide/?page_id=10:)

Much of what I read claimed that XSane should be able to automatically convert the negative to positive by making the correct choices in the drop down boxes.

I did do that and got the same (visually) result.  Apparently the Epson Windows Scanner Software does it and XSane does not.

---

### Post by measekite on 2009-03-26
> **Rallg said:**
> Just inverting the image will not always suffice. That's because a photographic color negative is not simply a mathematical color inversion. On commercial systems (Windows and Mac) software for scanning negatives will have a number of lookup tables for proper color correction, if you know the film that was used.

However, I doubt if you need "industry standard" colors, just whatever looks good. So, using gimp, use Colors > Invert, then Colors > Auto > White Balance. From there, you should be able to make manual color adjustments to your taste. EDIT: This does not work as well as expected.

[COLOR=Red]**THIS IS AN UPDATE**[/COLOR]

Based on responses to my original post I retested my approach and found the following to be true and accurate:

1.  I reexamined my negative and found it was Fuji and not Kodak so I changed the transparency type to Fuji negative.

2.  I scanned for preview and opened up the batch Window and selected only the negative I wanted.

3.  I found and clicked the negative button and then did the scan.  It was as bluish mask and not orange.

4.  I opened it up in Gimp and did Colors>Invert and I got a very poor looking very grainy result with extra poor white balance but it was a positive.

5.  I then did a Colors>Auto Equialize and there was some improvement but it still looked lousey.

6.  I then did a Filter Despecle and there was about a 60 to 70% reduction in grain but it was still a poor result.

7.  I then did a auto white balance and the result was greenish yellow and looked even worse so I did an undo.

8.  I then played with curves and staturation and got it as good as I know how.

Bottom line it was still very poor and not worth the time.

[SIZE=4]**[COLOR=Red]Unfortunately[/COLOR] I had to boot up [COLOR=RoyalBlue]Windows[/COLOR]**[/SIZE]

I booted up Windows and scanned the negative using Epson scanning sotware and it came out like a nice looking positive.  I did some editing in Photoshop as far as clearing out artifacts because PS has a healing brush and adjustment layers and some better tools but a horrible GUI.

I saved in PSD, rebooted Linux and opened it up in Gimp.  I did the finish work in Gimp and some more color correcting and printed in Gimp on Illford Classic Perl and the result was just strikingly great.

Thanks for all of your help and the links you helped me find.  It is too bad I still need Windows lurking on my computer.

---

### Post by Krupski on 2009-03-26
> **measekite said:**
> I am looking for Linux software with a GUI frontend that can convert a negative (tiff, png, jpg) into a viewable positive photograph that can then be edited or printed.

Is there such a thing?

If you are converting an image that was simply inverted, just invert it back.

If, however, you are trying to make positives out of scanned color negatives (with the orange mask), simply inverting will not work.

What you need to do is invert the image, AND adjust the "gain" and gamma of the 3 color channels.

To figure out how much adjustment to use, go to a Windows machine running Photoshop. Take a 50% gray box and apply the color negative correction to it. Then see what the R, G and B values became. That will tell you the gain for each channel.

Then, apply those same numbers to any Linux editing software. It will allow you to properly invert a color negative, then all you have to do is minor color balance touch up and you're done!

Another trick you can use is to correct an unexposed area of a negative to perfect gray - this tells you the color balance for that film.

If it's daylight film exposed in daylight or with xenon flash, it will be REALLY close and again only require minor touch-up.

The LAST trick is to simulate using a ground glass on an enlarger. Take the negative, apply a ton of Gaussian blur to it and then correct the "orange blob" to neutral gray. You will get almost perfect results... or require minor touch-up at most.

Good luck!

-- Roger

---

### Post by Krupski on 2009-03-26
> **measekite said:**
> It did not work.  I scanned in the negative.  When I opened it in Gimp it was the characteristic orange color negative.  After invert it still looked like a negative but it was cyan looking.

Of course. When you print a negative, you add magenta and yellow filters to the enlarger. What you are doing really is SUBTRACTING cyan.

-- Roger

---

### Post by mzuther on 2009-05-29
> **measekite said:**
> Unfortunately I had to boot up Windows.

You might want to try out VueScan ([http://www.hamrick.com/](http://www.hamrick.com/)) which mostly uses its own scanner drivers and runs fine under Linux.  It also scans better and much faster in Windows than when I use the original drivers and software for my Minolta film scanner, which really surprised me.

Just make sure that the demo runs fine, because the website states that there's no money back once you've bought the application!

Martin

---

### Post by Soul-Sing on 2009-05-29
Not sure but phatch does a lot.
: [http://photobatch.wikidot.com/getting-started](http://photobatch.wikidot.com/getting-started)
: [http://photobatch.wikidot.com/actions](http://photobatch.wikidot.com/actions)

---

