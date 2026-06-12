---
title: "wheres thumbnail view when you upload pics to the web???"
date: 2008-07-23
forum: Desktop Environments
---

### Post by bigdee973 on 2008-07-23
is there any possible way i could get a thumbnail view when i upload pictures from MY COMPUTER onto a site like myspace or photobucket?... all i get is this list where i can barely see the image...take a look here...
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot1.png[/IMG]

as you can see u can barely see the images in those small tiny icons.  i want to get my images looking at this here.

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot2.png[/IMG]

please help me with this im tired of having to use WINDOWS XP just so i can upload pictures...i have a huge library of pics and uploading them to my server too is a pain in the buns.  is this possible hopefully i get an answer from someone. thank u.

---

### Post by tuxxy on 2008-07-23
There should be a preview window to the right if your using GNOME.

---

### Post by mcduck on 2008-07-24
The image preview is an optional feature of the Gnome's file chooser dialog. It ahs to be enabled on a per-program basis (meaning that to use it in Firefox, Firefox developers have to enable it). This is because not every application has any need for picture previes (think about text editors, for instance).

You should send feedback to Firefox developers and ask them to enable the picture preview.

---

### Post by bigdee973 on 2008-07-25
> **tuxxy said:**
> There should be a preview window to the right if your using GNOME.

> **mcduck said:**
> The image preview is an optional feature of the Gnome's file chooser dialog. It ahs to be enabled on a per-program basis (meaning that to use it in Firefox, Firefox developers have to enable it). This is because not every application has any need for picture previes (think about text editors, for instance).

You should send feedback to Firefox developers and ask them to enable the picture preview.

no theres absolutely no preview option and mcduck i guess seems to be right mcduck could u please help me to get this message delivered to an expert at mozilla so that they are aware of this problem? please? i have a hard time figuring this out...also could it be a ubuntu problem? do u think i should contanct ubuntu themselves and ask them to help this get fixed im very very shocked and surprised that this hasnt be a resolved issure being that we are almost already approaching the 8.10 version!!! wow!.  well if anyone out there has advice or could help me deliver the message so that they coudl fix this it would be greatly helpful.  also is it just possible to grab the source code from mozilla and compile it urself in order to fix this unique problem? well all help is appreciated and i thank u guys for your help if no one gets to answer me thanks...

---

### Post by DoktorSeven on 2008-07-25
Firefox 3.0 and above have image preview on the file chooser.  Which browser are you using?

---

### Post by BLTicklemonster on 2008-07-25
Open the terminal and type

sudo aptitude install thunar


close terminal

right click your tool bar, and click on add to panel.

choose custom application launcher, then 

Name: Thunar

Command: thunar

leave comment blank or just put something about it being a file browser....

Click okay.

Use that, and to the right, chose your view.

No idea why your nautilus doesn't show how to change your views, heck it doesn't even show your normal file edit etc stuff. Could be compiz messing you up. Try turning off your desktop effects first, though. Maybe that will solve it without having to install thunar.

---

### Post by bigdee973 on 2008-07-25
> **DoktorSeven said:**
> Firefox 3.0 and above have image preview on the file chooser.  Which browser are you using?

im using firefox 3.0.1 as of writing.  the only thing i get when i try to upload is the same picture as u see above in my first post i have tried looking for a button that will display a preview of the thumbnail...i also tried hovering my mouse over the file to see if a bigger view would appear but i have failed to see anything in particular... maybe i have to click something else or navigate to another drop down list perhaps? any further assistance would be much appreciated thank you.

---

### Post by bigdee973 on 2008-07-25
> **BLTicklemonster said:**
> Open the terminal and type

sudo aptitude install thunar


close terminal

right click your tool bar, and click on add to panel.

choose custom application launcher, then 

Name: Thunar

Command: thunar

leave comment blank or just put something about it being a file browser....

Click okay.

Use that, and to the right, chose your view.

No idea why your nautilus doesn't show how to change your views, heck it doesn't even show your normal file edit etc stuff. Could be compiz messing you up. Try turning off your desktop effects first, though. Maybe that will solve it without having to install thunar.

thank u for the workaround my friend its very much appreciated.  i would really like to solve the issue with this firefox issure not showing any thumbnail previews.  its quite rare to have this attribute handed down to me in this browser.  i tried turning off compiz but yet again that failed to due anything..i seem to get the same exact output as you see above in my image.  however getting closer to your theory...i have typed

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons

into my terminal in order to get my gnome theme intacted with my root theme (its to make the custom theme appear in the root theme as well so u dont get a mixed up look..take a look here if ur more curious....
[http://ubuntuforums.org/showthread.php?t=839521](http://ubuntuforums.org/showthread.php?t=839521))  so, im not too sure if by me doing that i have somehow thrown off the root to not show or display some form of thumbnail view while i try to upload pics from ff3...well thank you for your help and i will surely put your advice into practice and use it as a work around but now i am determined to get into the bottom of this malicious event and be able to solve this and hopefully many other FF3/ubuntu users out there having the same problem so if anybody else could chip in or give some form of advice or help to contact developers about this it would be much appreciated by me and many others in the community thank you.

---

### Post by BLTicklemonster on 2008-07-25
Oh. Now I understand exactly what you are saying. I was up late because I lost grub when I resized a partition that had absolutely nothing to do with the / partition and was looking for help, got bored, saw this and replied.

I'll look back at my box tonight when I get home and see if I can come up with anything, though it's doubtful. FFV3 is not acting right on my machine at all. Frequent crashes if I click a tab, and upon first opening up, when I click on my bookmarks, it immediately acts like I clicked to save to bookmarks. Every time. I'm thinking of removing 3 and installing 2 or just using seamonkey. But I like the forward/back buttons working in FFV3...

---

### Post by BLTicklemonster on 2008-07-25
[center]For anyone who missed it, this first picture is a screenhot of what he sees in _***firefox***_ when he's trying to upload an image.

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot1.png[/IMG]



This next image is what he sees when browsing in _***nautilus***_.
 
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot2.png[/IMG]

[/center]

I just figured that out.

---

### Post by bigdee973 on 2008-07-25
> **BLTicklemonster said:**
> [center]For anyone who missed it, this first picture is a screenhot of what he sees in _***firefox***_ when he's trying to upload an image.

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot1.png[/IMG]



This next image is what he sees when browsing in _***nautilus***_.
 
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/screenshot2.png[/IMG]

[/center]

I just figured that out.

yes thats correct...the first image is what i see when i upload a file to myspace or photobucket... and the 2nd is just what i get when i click "Places">"Pictures" or go to home/(my user account)/ pictures...the second is just regular standard view of pictures...  cant seem to understand why i cant view those thumbnails.

---

### Post by CJay554 on 2008-12-16
I am using Firefox 3.0.4 but this seems to be not working, i tried snooping around the gconf editor but i could not find any values for firefox or nautilus for this problem... it would be really nice if this was incorporated into the browser... for simplicity sake.

---

### Post by xjcannonx on 2008-12-26
No thumbnails for me either but the thumbnail preview in nautilus does work for myspace if I use the link they provide on the upload page that says```
Upload photos to share with friends and family.
If you don't see the Upload Photo form below, click here

```

---

### Post by rcool on 2009-01-02
This issue is the main sticking point that my wife has now that I put Ubuntu on her computer. She uses York Photo to get prints of her digital pics, and she absolutely **hates** how she almost can't see the pics when she tries to upload them.

I was going to try it on Kubuntu to see if it is something specific w/ Nautilus. Has anyone tried that? 

Firefox works w/ Windows, and the images actually upload fine; it is just very hard to see which images you are actually uploading.
Thanks!

---

### Post by mcduck on 2009-01-03
> **rcool said:**
> This issue is the main sticking point that my wife has now that I put Ubuntu on her computer. She uses York Photo to get prints of her digital pics, and she absolutely **hates** how she almost can't see the pics when she tries to upload them.

I was going to try it on Kubuntu to see if it is something specific w/ Nautilus. Has anyone tried that? 

Firefox works w/ Windows, and the images actually upload fine; it is just very hard to see which images you are actually uploading.
Thanks!

Like I have already said on the previous page of this thread, this is a limitation of the Linux version of Firefox, and has nothing to do with Nautilus (except the fact that both use GTK as their toolkit).

Here's how it works: when making a program , the programmer asks GTK to draw a file selection dialog. He can, at that point, enable or disable the file preview section of the dialog. Firefox developers have chosen to keep it disabled, and the only place where you will be able to enable it s the Firefox source code.

(In Windows the preview works fine with Firefox because the windows toolkit's file selection dialog is made to _always_ display the preview)

Don't ask me why Firefox developers haven't enabled the preview, possibly because not all the files can/should be previewed and having the preview open when uploading binary files, for example, could be annoying. Or possibly because the optional preview in file selection dialog is a fairly new addition and Firefox developers just haven't yet changed their code to use it..

---

### Post by Solethara on 2010-02-23
I got the same problem I got many pictures and thumbnails are too small. I can't pick going one by one on the whole list.

I even looked if to compile firefox from source to see if mozconfig has a setting about it but I was unable to find it.

Anyone have a solution?

---

### Post by alexthunder on 2010-05-12
This is not only related to Firefox. The same happens in Opera and Google Chrome.  This is an ubuntu problem rather than anything else. One should be able to change the view of the files the same way it is done in windows (list view, thumbnails,...)

---

### Post by vs8 on 2010-10-17
That's great Gnome development. It seems they always forget to fix trivial bugs like this one and the network-indicator disappearing when switching users.

---

