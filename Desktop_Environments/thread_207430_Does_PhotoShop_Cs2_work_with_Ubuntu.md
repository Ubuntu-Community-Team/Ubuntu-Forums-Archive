---
title: "Does PhotoShop Cs2 work with Ubuntu?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by anony on 2006-07-01
Ok, I have my copy of adobe photoshop cs2 and I opened the setup using wine, I go through the agreement etc then  i get to the seriall page (right before the install) I insert my name and my organization and then i try to click in the box to input my serial but it won't let me. So I just click install 30 day trial thinking that I will input my serial later. I then click next. and this box pops up saying adobe photoshop was interrupted and must quit. Can photoshop work on linux? Any ideas to solve my problem?
anony

---

### Post by Dubbayoo on 2006-07-01
[QUOTE=anony]Ok, I have my copy of adobe photoshop cs2 and I opened the setup using wine, I go through the agreement etc then  i get to the seriall page (right before the install) I insert my name and my organization and then i try to click in the box to input my serial but it won't let me. So I just click install 30 day trial thinking that I will input my serial later. I then click next. and this box pops up saying adobe photoshop was interrupted and must quit. Can photoshop work on linux? Any ideas to solve my problem?
anony[/QUOTE]

You'd probably have better luck with codeweavers.

---

### Post by anony on 2006-07-01
codeweavers? is that another form of wine?

---

### Post by JoWilly on 2006-07-01
AFAIK only photoshop 7 works with crossover.

---

### Post by anony on 2006-07-01
Is there any way to get cs2 to work?

---

### Post by JoWilly on 2006-07-01
[quote=anony]Is there any way to get cs2 to work?[/quote] 
Not to my knowledge.

Edit: yes, in a vmware virtual machine :)

---

### Post by anony on 2006-07-01
Does any1 know if adobe has any sheduled development? Also, are there any other image editing programs which can open/edit psd files?

---

### Post by doris.houng on 2006-07-03
[QUOTE=anony]Does any1 know if adobe has any sheduled development? Also, are there any other image editing programs which can open/edit psd files?[/QUOTE]
[The GIMP](http://gimp.org/) can.  :D

---

### Post by olieviya on 2007-09-19
> **anony said:**
> Does any1 know if adobe has any sheduled development? Also, are there any other image editing programs which can open/edit psd files?

[Pixel?]("http://www.kanzelsberger.com/pixel/?page_id=12")

---

### Post by trishacupra on 2007-09-19
[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps]("http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps")

I've heard it's possible to use CS2 in Ubuntu. I'm about to try this myself. Photoshop 7 doesn't cut it for me.

---

### Post by trishacupra on 2007-09-24
I've got it working. The only remaining annoyance is an error about the Adobe Updater, but you just close it and CS2 then works fine.

Start with [Photoshop CS2 on Linux in 3 Easy Steps]("http://youralternative.blogspot.com/2007/06/photoshop-cs2-on-linux-in-3-easy-steps.html")

What you need to do is download a copy of PortashopCS2. You end up with an exe file called PhotoshopPortable.exe and a folder called Photoshop. 

You need to download some dll files and pop them into that folder. Then you end up with a 'lite' version of CS2. You can't 'save for web' or save as gif or png, so I wasn't happy about that.

So, I replaced the Photoshop folder with the one on my Windows box, and used the PhotoshopPortable exe to launch it. If you click on the Photoshop.exe file inside the folder, it won't work. But if you use the Portashop exe in the same folder as the Photoshop folder (and make sure that folder is called 'Photoshop') then it works well.
 
UPDATE - I forgot that I may have copied the AdobeLM.dll from the Portashop Photoshop folder into the Windows-box Photoshop folder. This may or may not be necessary.

Now I have a fully functional CS2 on Ubuntu. And as I said, the only annoyance I've found is the Adobe Updater error, which doesn't affect the functionality.

By the way, I can open it with Crossover Linux, but Wine is giving me trouble. So see how you go.

---

### Post by nowashburn on 2007-09-25
hi,

thanks for the info on turning portashop into the full version of photoshop! ive been using portashop for a while now and have been toying around trying to get the full version of cs2 to run with no luck. I guess i should have tried the obvious like you did, hope this really works! and luck getting illustrator cs2 running? i cant even find a portable version that will work :( other than illustrator.. i will have the full versions of the following web programs running on linux flawlessly: flash 8, dreamweaver 8, fireworks 8, and photoshop cs2 (judging that this method works). With all of these programs together, this is a great set of graphic/ web development software on linux.  I would like to take these programs that i have running and post them as a package somewhere for others to download. It seems as though working versions of these programs through WINE are in high demand and i bet a lot of people would appreciate them packaged together in one easy download. Any ideas where i could upload the package without running to legal issues? thanks again!

---

### Post by nowashburn on 2007-09-25
hi,

thanks for the info on turning portashop into the full version of photoshop! ive been using portashop for a while now and have been toying around trying to get the full version of cs2 to run with no luck. I guess i should have tried the obvious like you did, hope this really works! and luck getting illustrator cs2 running? i cant even find a portable version that will work. i will have the full versions of the following web programs running on linux flawlessly: flash 8, dreamweaver 8, fireworks 8, and photoshop cs2 (judging that this method works). With all of these programs together, this is a great set of graphic/ web development software on linux.  I would like to take these programs that i have running and post them as a package somewhere for others to download. It seems as though working version of these programs with wine are in high demand and i bet a lot of people would appreciate them packaged together. Any ideas where i could upload the package without running to legal issues? thanks again!

---

### Post by trishacupra on 2007-09-25
> **nowashburn said:**
> hi,
Any ideas where i could upload the package without running to legal issues? 

That's the 6 million dollar question. If I knew, I would have uploaded it myself.

---

### Post by asipi on 2007-09-26
Get use to using GIMP. It is professional and almost the same features like photoshop and it is native linux application...

---

### Post by trishacupra on 2007-09-26
I've tried to use GIMP (and GImpshop), but I don't have time to learn a completely new (and very different) application when I am used to using Photoshop every day. As a graphic designer I can't just drop everything and stop making income just to learn how to use GIMP.

"Just learn GIMP" may be good advice for the average home user who just wants to crop or rotate the odd photo, or to the professional just starting up. But it's not practical for the already-established design professional.

---

### Post by trishacupra on 2007-10-23
I've discovered that the type tool in my Portashop/CS2 setup is buggy. I'm kind of resigned to the idea of needing to dual boot XP for a long time - unless I get a Mac...

---

### Post by SkIMMas on 2007-11-18
> **trishacupra said:**
> I've discovered that the type tool in my Portashop/CS2 setup is buggy. I'm kind of resigned to the idea of needing to dual boot XP for a long time - unless I get a Mac...

I installed the Microsoft Core Fonts and that apparently solved the type tool problems.

---

### Post by trishacupra on 2007-11-18
I already had the MS core fonts installed,  but maybe reinstalling them might help. The bug is an on-again, off-again kind of affair.

---

