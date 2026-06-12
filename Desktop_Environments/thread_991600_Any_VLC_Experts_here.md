---
title: "Any VLC Experts here???"
date: 2008-11-23
forum: Desktop Environments
---

### Post by keithld on 2008-11-23
I installed it and got everything working and since I installed the Mac4Lin Ubuntu theme I wanted to change the theme for VLC (0.9.4-1ubuntu3) to the "Crossover_Leopard Skin" and I never bothered to check their site since I figured this would work...


Opps!!!, it doesn't work and I read where Skins2 is "Broken"... Hmmm

Well I can't change back to the default skin or any others and can no longer get into any of the "Preferences and make changes" I also can't find a preference file in the VLC folder to either change the skin or just to delete the preference file and get the defaults back...

I tried running vlc -I skins2 in a Terminal and basically it just tells me what skin is installed and I get this error at the end:

[00000417] main generic error: object is not attached
Segmentation fault

I can use RhythmBox/MoviePlayer but I was hoping to use VLC for my DVD Viewing and Audio listening, I like the Equaliser in VLC which RhythmBox doesn't seem to have...

So should I use the "Synaptic Package Manager" and do a "Complete Uninstall of VLC" and try to install again???...

Thanks guys... :guitar:

---

### Post by ellgor on 2008-11-24
Hi,

I had the same problem when I got new skins and tried to run them, I found that if I downloaded the skin file/folder to one of my own folders ( example:/home/movies) and left it unzipped it worked ok, however a cautionary note, out of the six I downloaded 3 just wouldn't display properly and of the others there was some, how shall we say, unexpected happenings. I can say that I'm most disappointed with this new Vlc altogether, you may have noticed a few other posts mentioning it, suffice to say I have gone back to an earlier trusted version, hope this of use to you.
(you can change the location of where the files are when you click on the change skin tab)
Regards, Ellgor.

---

### Post by HRshovinstuff on 2008-11-24
I have experienced the same problem in the past.  Trying to change to a different theme within vlc's preferences.  Then restart the program and it won't boot, or isn't visible.   

What you need to do to get it back to default settings is remove any config files.  I believe I found mine in
 ~/.vlc

Although this could vary.  You might find them in /home/username/.vlc

Grep to find directories.


Once configuration files are removed the program will reset itself to default.

Don't forget to visit the #Ubuntu channel on IRC for more support.

](*,)

---

