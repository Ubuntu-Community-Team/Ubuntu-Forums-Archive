---
title: "skydome doesnt show"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by Valkyrie Wrath on 2007-08-22
I'm new to this. Just got Ubuntu today. When I try to make a picture a skydome, it just turns out white. How can I make the image show up?

---

### Post by Happy_Man on 2007-08-22
You need to have it at the right resolution. It needs to have sides of length of an even power of 2. So 1024x1024 would work, but not 1024x768.

---

### Post by Rupertronco on 2007-08-22
In addition: Make sure the file is of .png type (jpg,gif,etc wont work).

---

### Post by gundumfx on 2007-08-25
> **Happy_Man said:**
> You need to have it at the right resolution. It needs to have sides of length of an even power of 2. So 1024x1024 would work, but not 1024x768.

ummm well i have the same problem well cane you give me like screen shots how you do it or were you go an stuff please i need help just tell me what i have to go an do

---

### Post by Happy_Man on 2007-08-25
You can either take an existing image and crop it using GIMP, or you can make your own.

---

### Post by Rupertronco on 2007-08-25
> **gundumfx said:**
> ummm well i have the same problem well cane you give me like screen shots how you do it or were you go an stuff please i need help just tell me what i have to go an do

Save an image somewhere, make sure it's .png file format, open CCSM (compiz config manager) and go to  the cube options, check the option to use skydome, and locate the file you wish to use for it (wherever you saved it).

Play around with the program a bit, and get to know it.

---

### Post by gundumfx on 2007-08-25
> **Rupertronco said:**
> Save an image somewhere, make sure it's .png file format, open CCSM (compiz config manager) and go to  the cube options, check the option to use skydome, and locate the file you wish to use for it (wherever you saved it).

Play around with the program a bit, and get to know it.

well i don't know were ccms is but can you find me a short cut like in terminal command so i can open it from there

---

### Post by Happy_Man on 2007-08-25
The terminal command *is* "ccsm".

---

### Post by Valkyrie Wrath on 2007-08-25
Whats a good program to change the format?

---

### Post by Rupertronco on 2007-08-25
Gimp, as mentioned before. When you ask for help the least you could do is read the responses instead of firing off redundant questions. I'm sorry to be a bit harsh, but poke around and read a bit.

---

### Post by ajkenney on 2007-08-26
> **Rupertronco said:**
> Save an image somewhere, make sure it's .png file format, open CCSM (compiz config manager) and go to  the cube options, check the option to use skydome, and locate the file you wish to use for it (wherever you saved it).

Play around with the program a bit, and get to know it.

I've been having some minor problems with Desktop Effects but I've muddled through the simple interface and have the basic functions working.  I don't expect a lot as I know it's still a work in progress but, overall, I think it's great.  Then I read the post above and went looking for the CCSM (compiz config manager).  I manually searched and ran file searches with Nautilus for "CCSM", "compiz-config", etc., and couldn't find it.  I'm using 7.04 Feisty and have everything working well under it (except my Epson C90 printer).  I also couldn't find it in the repositories and I have them all enabled.  The last thing I did was to reinstall compiz but, it's still not there!  Help!  Where is my "compiz config manager"?  :confused:

---

### Post by Rupertronco on 2007-08-26
CCSM is the comipiz config settings manager, you run it by opening up a terminal or by pressing alt+f2 and typing just "ccsm". you will not have this unless you have the compiz-core with the additional packages for settings manager. these packages are not available through the ubuntu repositories. add vorian(most stable new), armanranth(most stable but older), or trevino(all newest packages, but experimental) repositories. you can get the information on how to add those repositories and their addresses in threads in this forum, notably the sticky and highly viewed howto threads.

---

### Post by Rupertronco on 2007-08-26
> **ajkenney said:**
> I've been having some minor problems with Desktop Effects but I've muddled through the simple interface and have the basic functions working.  I don't expect a lot as I know it's still a work in progress but, overall, I think it's great.  Then I read the post above and went looking for the CCSM (compiz config manager).  I manually searched and ran file searches with Nautilus for "CCSM", "compiz-config", etc., and couldn't find it.  I'm using 7.04 Feisty and have everything working well under it (except my Epson C90 printer).  I also couldn't find it in the repositories and I have them all enabled.  The last thing I did was to reinstall compiz but, it's still not there!  Help!  Where is my "compiz config manager"?  :confused:

You've overcome the hardest part, getting your computer to use the 3-d acceleration and enable compositing. Now you just need some more compiz packages for cooler effects.

---

### Post by ajkenney on 2007-08-27
> **Rupertronco said:**
> You've overcome the hardest part, getting your computer to use the 3-d acceleration and enable compositing. Now you just need some more compiz packages for cooler effects.

Thanks for your help on this but, I think I'll wait until things stabilize a bit more.  I've been looking through the forums and saw that people were having a lot of problems when they were doing the upgrades on their own.  I could do it but, I really don't have the time right now.  I'm running my own small business from my laptop and I've 6 proposals to do for various satellite communications projects!  Eye candy will have to take a back seat.

Good news is, when I'm with my clients and I flash the cube back and forth between the proposal and drawings, these guys sit there with their Windows laptops and drop their jaws on their keyboards!!  :)
What will happen when I got more of the features working!!

Their next question is "what's Ubuntu?"  :lolflag:

Cheers!

---

### Post by Happy_Man on 2007-08-27
That just makes it all worthwhile, doesn't it? :)

---

