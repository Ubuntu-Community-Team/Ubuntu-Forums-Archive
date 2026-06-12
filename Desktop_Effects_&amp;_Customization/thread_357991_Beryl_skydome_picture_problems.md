---
title: "Beryl skydome picture problems"
date: 2007-02-10
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-02-10
I finally managed to get Beryl functioning on this old Dell with a GeForce4 MX 420 card.
Almost everything works fine apart from the fact that I can't get a photograph to show on the skydome.
Note that I DO have the skydome checkbox checked in Desktop Cube>Skydome AND the photo is in png format.
The first picture I tried was big (6.5 MB). When that didn't show in skydome I thought it may be due to its excessive size.
However, the second one at only 87 KB equally does not show.
I see that the image dimension must be a power of two (presumably this means an integer power of two).
But what does this mean?  Does it refer to the KB size of the image or what?

Would be grateful for any attempts to enlighten me as to what will ensure an image is acceptable for appearnce on skydome.

---

### Post by Happy_Man on 2007-02-10
Yes! SOMEBODY else has this problem like me! I have tried everything also, and nothing works! I suppose the graphics card is the problem...anyone out there who can help us poor two souls?

---

### Post by Zzl1xndd on 2007-02-10
Im in the same boat as well. I dont get it I can place images on the top and Bottom of the Cube but not the Skydome.

---

### Post by PaulFXH on 2007-02-10
I managed to get a picture on the skydome after I read that the image must have a width:height ratio of 2 and also that the number of pixels in both the width and height must be an integer power of two.

So I used Photoimpression to edit one of my photos to 2048 pixels (width) x 1024 (height) in PNG format and this worked perfectly.

Good luck!

---

### Post by Wicca on 2007-02-10
In addition to Pauls discovery: The picture size may not exceed the maximum texture size your graphic card is capable of. You can find the max. texture size this way:
```
xvinfo | grep max
```
So if the answer is 1024 you need to resize a picture of 2048x1024 to 1024x512 in order to use it as a skydome picture.

---

### Post by Rhubarb on 2007-02-10
A picture (png) whose resolution is 4192 (width) x 1024 (height) also works perfectly too.
I found some nice skyboxes here:
[http://www.quadropolis.us/flexinode/list/3](http://www.quadropolis.us/flexinode/list/3)
You'll need to use a program like GIMP to stitch the front, right, back, and left photos together.

---

### Post by PaulFXH on 2007-02-10
That's strange!
So the width:height does NOT have to be exactly 2? Yours is more than 4.

Also, 4192 is NOT an integer power of two. 

So, where does that leave us wrt what can or cannot be loaded onto skydome?

---

### Post by ronmarley1 on 2007-02-11
> **PaulFXH said:**
> That's strange!
So the width:height does NOT have to be exactly 2? Yours is more than 4.

Also, 4192 is NOT an integer power of two. 

So, where does that leave us wrt what can or cannot be loaded onto skydome?

I think what is meant is factor of 2, not power of 2 (1024 X 512, 1024 X 1024, etc...).

---

### Post by PaulFXH on 2007-02-11
Not sure...if you mouse over the skydome image box in Beryl Settings Manager it clearly says that image dimensions must be a **power** of two.
In trying to figure out why some images are accepted for incorporation in skydome and many more not, I attempted to put together some rules that must be obeyed by the images.

Thus far I had come up with the following:
1) Dimensions in pixels must be an integer power of two
2) Width:Height ratio must be exactly two (saw this somewhere on googling but can't remember where)
3) Image must be in PNG format.

Rhubarb's post contradicted the first and second of these rules.
Therefore, I'd be interested to hear from others which, if any, of  these rules are valid.

---

### Post by Wicca on 2007-02-11
I've some pictures of 2048x512 doing very well as the skydome, which has a ratio of 4:1.
To me 'power of 2' means a sequence of 1,2,4,8,16,32,64,128,256,512,1024,2048 and so on. Both width and height need to be one of those numbers.


Some examples:
2048x2048 OK
2048x1024 OK
2048x512 OK 
256X128 OK
1024x1024 OK
1024x256 OK
1600x1600 NOT OK
1600x800 NOT OK

---

### Post by PaulFXH on 2007-02-11
Thanks for this.
Basically you're saying that the Width:Height ratio DOES NOT have to be two.
OK, so rule #2 in my list can be deleted and the comment you made in an earlier post about the maximum permissible texture size included.

Yet another mystery of the universe unravelled.!
Paul

---

### Post by Rhubarb on 2007-02-13
Huzzah!  :)

---

### Post by Horrendus01 on 2007-03-02
The image also does not have to be in .png format, as I have mine set with a .jpg image and it works quite well.

---

### Post by hikaricore on 2007-03-02
Little offtopic, but some beautiful beryl skydomes live here:

[http://goberylgo.blogspot.com/2007/01/indice-de-imagenes-para-el-skydome.html](http://goberylgo.blogspot.com/2007/01/indice-de-imagenes-para-el-skydome.html)

These may help give you an idea about possible sizes for your own.

This has to be one of my absolute favorites:

[IMG]http://bp2.blogger.com/_tG9UeHxks34/Raz2v08Nz3I/AAAAAAAAAOo/gfEz_vQ77DU/s400/fabrica360_1024.jpg[/IMG]

Most of these are made to be set as animated skydomes which means when they're wrapped they give cube rotation an insane panoramic feel.

---

### Post by rainwalker on 2007-03-02
So this wouldn't work?
[http://upload.wikimedia.org/wikipedia/commons/b/b8/An_Teallach_panorama.jpg](http://upload.wikimedia.org/wikipedia/commons/b/b8/An_Teallach_panorama.jpg)

---

### Post by hikaricore on 2007-03-03
You would need to resize it to fit the correct dimensions :)  but it could work with a little cropping and resizing.  Check your card's max texture size for better info on this as noted in this thread.

---

### Post by PaulFXH on 2007-03-06
From my perspective, the "rules" for what can or cannot be used as a Skydome picture are as follows:

1. Picture must be in .png format
2. Both dimensions of the picture must be an integral power of two (i.e. 256, 512, 1024, 2048 or 4096 pixels)
3. Must not exceed graphic card maximum texture size as indicated by:
```
xvinfo | grep max
```

Despite what has been posted above by Horrendus01, .jpg format just does not work for me on Skydome. I have tried a test where I formatted the exact same shot in both .jpg and .png formats.
While the .png picture was readily accepted by Skydome, trying to load the .jpg shot actually led to Beryl shutting down. I could only get Beryl to start again by taking out the .jpg and replacing it with the .png picture (or with nothing)

---

### Post by Detonate on 2007-03-06
I am using a jpg file for the skydome, it works.  But I can't get the caps to show anything but the Beryl default png.  Any ideas?

---

### Post by rainwalker on 2007-03-06
Open up the Beryl Settings Manager, go to Desktop -> Desktop Cube -> "Caps" Tab and click "Browse", go to whatever image you want to use, and click "Open". In the "Image Files On Top" box, click on the image you just chose and click the arrow to move it to the top of the list. That's always worked for me.

---

### Post by Detonate on 2007-03-07
I should have said in my first post that I have already tried to change the image through the menu, but it doesn't change.  Don't worry about it, I will just keep trying until I figure out what's wrong.

---

### Post by Detonate on 2007-03-07
OK, I figured it out.  When you add the image to the list that beryl should show as the top or bottom of the cube, you need to delete the entry for the bery default png or it won't work.  Just highlight it and click on the "minus" button.

---

### Post by dukem72 on 2007-03-10
For several days I was trying to get the Skydome to work for me with no luck, until I found this thread the other day. 

To make a long story short, what worked for me is to have whatever image I wanted to use to have the height and width to be the same i.e. 1024 x1024  

In other words the image is going to look squashed but once it displays in the Skydome it looks fine. Perhaps not the best or elegant method of making it work, but is the only one that did allow my laptop to display the image. 

And for whatever is worth I was saving the images as png's from Photoshop with the Save for Web and selecting PNG 8 not the 24 and that is it. 

Also something worth mentioning is that when using images that were for example 2048 x 1024 something strange happened that when rotating the cube the dominant color of the picture say green for a nature shot would show as the background but not the detail of the picture like the trees and water fall, etc.

---

### Post by PaulFXH on 2007-03-10
Did you check this as suggested in post #5 of this thread?
>   The picture size may not exceed the maximum texture size your graphic card is capable of. You can find the max. texture size this way:
```

xvinfo | grep max

```
So if the answer is 1024 you need to resize a picture of 2048x1024 to 1024x512 in order to use it as a skydome picture.

---

### Post by dbarbour on 2007-03-15
On my widescreen laptop (native res of 1280x800) I get
```
maximum XvImage size: 1920 x 1080
maximum XvImage size: 2048 x 2048
```This means what as far as sizing my skydome image is concerned?

---

### Post by SentientFluid on 2007-03-20
First off, thanks for the post!  I was wondering why it wasn't working properly!

> **dbarbour said:**
> On my widescreen laptop (native res of 1280x800) I get
```
maximum XvImage size: 1920 x 1080
maximum XvImage size: 2048 x 2048
```This means what as far as sizing my skydome image is concerned?

Mine just shows:

```
    maximum XvImage size: 2048 x 2048    
```

I'm guessing you'll want to go with 2048 for your max.

Edit:

As stated above, my max is supposed to be 2048 but I am successfully using an image that is 4096x1024.  So perhaps its not the 2048 that is the requirement but rather the product of the resolution (ie 2,048 x 2,480 = max pic resolution)

2,048 x 2,048 = 4,194,304 = 4,096 x 1,024

---

### Post by herbster on 2007-03-27
> **Wicca said:**
> I've some pictures of 2048x512 doing very well as the skydome, which has a ratio of 4:1.
To me 'power of 2' means a sequence of 1,2,4,8,16,32,64,128,256,512,1024,2048 and so on. Both width and height need to be one of those numbers.


Some examples:
2048x2048 OK
2048x1024 OK
2048x512 OK 
256X128 OK
1024x1024 OK
1024x256 OK
1600x1600 NOT OK
1600x800 NOT OK

Unbelievable. Using Beryl for over a month, could NOT get the skydome to work and whaddaya know, the xvinfo command and the reference you have posted here, I am resizing a few images and the skydome works!!!!! :) Thanks!!

---

### Post by c-breakdown on 2007-04-03
I've tried everything to get skydome to work and I can't.  I've resized images in all kinds of ways to no avail.

```
charlie@Alexis:~$ xvinfo | grep max
    maximum XvImage size: 2046 x 2046
    maximum XvImage size: 2046 x 2046

```

EDIT:  Okay I can get it to work now but it's all blurry, what kind of image size do i need to have for it not to be poor quality?

---

### Post by PaulFXH on 2007-04-04
What size image (in pixels) did you try that's blurry?

I've just set up Beryl on a new HP Pavilion dv1000 laptop with an Intel 945GM card. When I ran
```
xvinfo | grep max
```
I got 
>  maximum XvImage size: 1920 x 1080
    maximum XvImage size: 2048 x 2048
I then used Photofiltre to resize a .jpg image to 2048x1024 pixels and saved it as a .png image.
When I saved this in the Skydome box, it gave me a perfectly clear Skydome image.

So what did you do different from this?

---

### Post by c-breakdown on 2007-04-04
Okay well if I have animations off the picture is perfect, but with them on the image becomes stretched in strange ways and the image comes out pixelated.

---

### Post by PaulFXH on 2007-04-04
When you say "animations on", do you mean you have a checkmark in the box marked "animations" in Beryl Settings Manager>Visual Effects?

Well, I have this box checked and animations work, but the Skydome image is still absolutely perfect.

It might be interesting if you were to post some details such as
1) what graphics card?
2) what size image you put in Skydome
3) what format (.jpg, .png or other)?

---

### Post by c-breakdown on 2007-04-04
> **PaulFXH said:**
> 
It might be interesting if you were to post some details such as
1) what graphics card?
2) what size image you put in Skydome
3) what format (.jpg, .png or other)?

1) Nvidia (I'll need the terminal command for any more details)
2) 2048x1024, 2048x512, 1024x256
3) .png

[Click Here For Screenshot Without Animation Checked]("http://i17.photobucket.com/albums/b66/hoo1igan/NoAnimation.png")

[Click Here For Screenshot With Animation Checked]("http://i17.photobucket.com/albums/b66/hoo1igan/Animation.png")

---

### Post by iamtherealwoody on 2007-04-04
OK, sounds really stupid, and Im a newb, but I couldnt use the sky dome either and I found out why.  The image was saved as "image" in .png format.  Once I named it "image.png" everything worked perfect.
Maybe that will help someone else like me.

matt

---

### Post by PaulFXH on 2007-04-05
@c-breakdown
Well, doesn't seem to be anything obviously wrong with your picture dimensions or format.
As you didn't say WHICH nVidia card it's hard to comment on that.
However, I had no problems with Beryl on an old nVidia GeForce4 MX420 card and I bet your card is more modern than this.
A possibility is your graphics card driver although the fact that evrything else about your Beryl seems to be fine would make this a remote possibility.
You could try to renew your card driver using Alberto Milone's ENVY script which will install exactly the correct nVidia driver as well as adding the right stuff in your /etc/X11/xorg.conf.
However, you might be taking a risk here if this is the only thing wrong with your Beryl performance, so be warned.
As a respectful suggestion, it may be better to start a new thread specifically about your problem rather than bury your request for help in an old thread that, at this stage, will only attract other people looking to see how to solve their own problem rather than more experienced people likely to be able to help you.

Good luck
Paul

---

### Post by teaker1s on 2007-04-05
to print screen you need beryl rotate cube settings and enable **initiate sticky**[IMG]http://photos1.blogger.com/x/blogger/1418/818/320/189413/Screenshot-1.png[/IMG]

---

### Post by herbster on 2007-04-05
I think c-breakdown is talking about "Animate Skydome" in the Skydome options, whereby if you check it the illusion of the cube spinning in the environment of the skydome image (ie., clouds/space/whatever) is created, and if it's not checked the image is still and just a background to the cube.

If you check Animate Skydome, the image will definitely become "stretched" and may appear a bit blurry or not as great as it being viewed in its regular dimensions, because it's being stretched to fill every part of the screen no matter how many times/which way you rotate the cube.

Of course I might be way off but that's what I've experienced in fiddling with the Skydome after a month of the sucker not working :)

---

### Post by PaulFXH on 2007-04-05
You could be right, herbster.
However, it's strange that c-breakdown didn't notice (or at least didn't mention) that the skydome picture is not only blurry but actually moving when animations is on.
Anyway, only he can confirm or deny this possibility.

---

### Post by jollemeyer on 2007-05-17
Just my 2 cents:

I noticed that the skydome picture is NOT displayed when I move it into the wallpaper folder (/usr/share/wallpaper) using sudo mv.

However, everything is fine when I use the same picture from my home folder.

Probably a permission issue?

The setup NOT working:
My /usr/share/wallpaper folder belongs to root (owner and group), the permissions are as set to 755. Hence, no write access for the users.

The setup working fine:
My home directory belongs to my (owner + group). The folder permissions are also 755, allowing me write access.

The picture properties (permissions, owner, group) are identical in both setups.

Has anybody noticed this behaviour as well?

---

### Post by Seeker84 on 2007-06-15
Hey this thread was a big help.  Figured out that mine needed a 2:1 and the file needed to be .png.  Thanks all.

---

### Post by d_xtremw on 2007-06-23
my max screen resolution is 2048 x 2048 but it still isnt accepting any of my skydome images even though they are in png format and are using the power of 2 as a ratio.  all that shows up is a light sky blue screen or a black screen. or the fallback gradient. any ideas why this could be?:(

---

### Post by PaulFXH on 2007-06-24
It's not just the RATIO of the image dimensions that needs to be a power of two (it can also be 1 -- which is the zeroth power of two). The actual image dimensions must also be an integer power of two.
So an image with 2000x1000 pixels won't work, but 2048x1024 will.

---

### Post by ScoPro on 2007-09-10
I have an ATI card and no matter what I tried, I couldn't get a skydome image to load... the screen would just go white on me, and no matter what the image size or format I tried, I got the same result. I finally gave up and started looking around for a fix for why my custom trueglass theme was going white when I hit the maximize button, and strangely enough... the fix for that fixed my skydome problem too!!

A big thanx to the people at [http://www.bloglines.com/blog/cybernout](http://www.bloglines.com/blog/cybernout) for helping me figure this out!

gksu gedit /etc/drirc


paste :



<driconf>

   <device screen="0" driver="radeon">

   <application name="all">

   <option name="allow_large_textures" value="2" />

  </application>

  </device>

</driconf> 

Now just save the file and you'll be off and running.

Hope this helps somebody out there!

(This is the first time I've ever logged a fix on the Ubuntu forums... I'm so excited!)

-ScoPro

---

### Post by mk4umha on 2007-11-08
> **dbarbour said:**
> On my widescreen laptop (native res of 1280x800) I get
```
maximum XvImage size: 1920 x 1080
maximum XvImage size: 2048 x 2048
```This means what as far as sizing my skydome image is concerned?

I have the same problem with the background stretching and looking like pixilated even if i use a high rez picture that's 2048x1024. Is there a super high rez background that anyone can post so we can test to see how to setup our own background? Every background that i've tried so far is pixilalted and cut off.

---

