---
title: "GIMP &gt; How can I change the resolution of image without quality loss?"
date: 2009-05-22
forum: General Help
---

### Post by YMS_1975 on 2009-05-22
Hey folks,

Running Ubuntu 9.04 and using GIMP 2.6. I'm not that experienced with GIMP, so please be gentle.

I've been playing around with images and how to change their resolution, so that I may use the new altered images as wallpapers. Anyhoo...here's what I've been doing : 

1) Open up the original file
2) Go to "Image"
3) Go to "Canvas Size"
4) Change the Width & Height (1680=W & H=1050)
5) Then click the resize button.

When I do this, the image does seem to resize in shape. I verify this when I save & exit the file, and then reopen it and view it in full screen mode. The only problem I'm hitting though is that the quality of the image is somewhat distorted, or pixelated (if that makes sense).

Is this normal for an image that has had it's resolution changed? Does it matter how drastic a change in resolution has been made? Is there a way to correct this?

Anybody?

---

### Post by coffeecat on 2009-05-22
Try Image > Scale Image. Adjust your image size and then under 'Interpolation' select either 'Cubic' or 'Sinc'. See which works better for you.

---

### Post by Minsky on 2009-05-22
Try using **Image > Scale Image...**   I think that should get the result you're looking for.

---

### Post by YMS_1975 on 2009-05-22
> **Minsky said:**
> Try using **Image > Scale Image...**   I think that should get the result you're looking for.

Hey Minsky,

I tried your suggestion, but got the same results. Look at my questions right at the end of my first post. Do you have answers to those questions?

I think that changing resolution might have an effect on the quality of images. In the meantime...I'll just keep trying different images.

---

### Post by michy99 on 2009-05-22
Are you making the images larger or smaller? If you are enlarging them, then there will be some pixelation since the original image does not contain enough information for a bigger image. To get the best results for a wallpaper, use an image that is as least as big as your desktop to start with.

---

### Post by YMS_1975 on 2009-05-22
> **michy99 said:**
> Are you making the images larger or smaller? If you are enlarging them, then there will be some pixelation since the original image does not contain enough information for a bigger image. To get the best results for a wallpaper, use an image that is as least as big as your desktop to start with.

I think that's what the problem was....I am in fact enlarging the images, and these are smaller pictures. I don't think I'd have the same problem making them smaller.

I just thought that making it larger, it would somehow at least maintain the quality. Oh well, live and learn I guess.  :p

---

### Post by Minsky on 2009-05-23
> **YMS_1975 said:**
> Hey Minsky,<br>
<br>
I tried your suggestion, but got the same results. Look at my questions right at the end of my first post. Do you have answers to those questions?<br>
<br>
I think that changing resolution might have an effect on the quality of images. In the meantime...I'll just keep trying different images.<br>
<br>
My apologies YMS, looking back at your first post it does become obvious that you were trying to enlarge an image. Try this and see if it works for you:

Open the wallpaper in GIMP and go to **Image > Scale Image...** In the window that appears, click on the selection box next to the **Width** and **Height** settings (**Pixels** is shown as default), and select **Percent**. Click on the UP arrow next to either the **Width** or **Height** settings (it doesn't matter which), as many times as required until a value close to 110% is displayed. Make sure that **Cubic** is displayed in the **Interpolation** selection box, and click on **Scale** at the bottom of the window. Repeat the process - scaling up by 110% - until your image reaches the required size. If the image goes above the required size, you can always scale back down using absolute values.

Repeatedly increasing the image by 10% of its previous size seems to preserve most of its quality. You can also try using the other Interpolation settings to see which works best for you. I hope this does the trick for you.

---

### Post by MickS on 2009-05-23
Do what Minsky said, I have used that trick quite a few times It's surprising what you can achieve, don't forget to try a bit of sharpening at the last stage, I like the refocus plugin for this.


Mick

---

