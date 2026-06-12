---
title: "Windows Games + Wine = not working"
date: 2009-02-04
forum: General Help
---

### Post by UranUtan on 2009-02-04
Hi,

I need some ruses to encourage my wife to switch over to Linux. She likes the type of games at [http://www.reflexive.com/](http://www.reflexive.com/)

Using Ubuntu 8.10 Desktop x32. I have made two attempts, installing two different games under Wine 1.1.14. Each time the computer slowed down so much and the screen becomes covered with full screen graphic. The mouse barely moves. I had to power off to exit the game. I read that Wine can run a lot of Windows games. The two attempts I made had failed miserably.

If any of you had succeeded in making these Reflexive games works under Wine can you show me how to do that?

Otherwise I wonder if running them in a virtual machine would be better.

Thanks in advance for any help.

---

### Post by Old *ix Geek on 2009-02-05
I'd never been to that site before but just now I popped on over there, downloaded a couple of games at random, installed them, and played them just fine.  I didn't do anything special, so I don't know what to tell you!  They play perfectly and look great.  If you'd like screenshots, let me know.

---

### Post by UranUtan on 2009-02-05
> **Old *ix Geek said:**
> I'd never been to that site before but just now I popped on over there, downloaded a couple of games at random, installed them, and played them just fine.  I didn't do anything special, so I don't know what to tell you!  They play perfectly and look great.  If you'd like screenshots, let me know.

May I know your Ubuntu and Wine version? I have tried Bejewel 2 ([http://www.reflexive.com/Bejeweled2Deluxe.html](http://www.reflexive.com/Bejeweled2Deluxe.html)) game and it didn't work for me.

I don't think it's a hardware issue I have P4 2.8GHz 3 GB Ram, video is good enough, Compiz graphic customization accepts "advanced" settings. 

This game works OK under XP on a much poorer machine (P3 1GHz basic video card).

May be I did something wrong in the installation. How did you install it?

Thanks in advance for any clarification.

---

### Post by khelben1979 on 2009-02-05
Have you tried the [Wine Wiki]("http://wiki.winehq.org/")?

Also, [this page]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html") might be of interest to you in order to be able to play more games together with Wine.

---

### Post by UranUtan on 2009-02-05
> **khelben1979 said:**
> Have you tried the [Wine Wiki]("http://wiki.winehq.org/")?

Also, [this page]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html") might be of interest to you in order to be able to play more games together with Wine.

Hi,

Thanks very much for the tips. Excerpted from the Wiki:

> 9.1. What are the system requirements for Wine?

The rule of thumb is that if your application runs fine in Windows, it should run fine on the same system using Wine. Wine, along with the operating system you use to run it, generally requires less disk space and memory than Windows itself. If you're not currently running a Windows application, Wine won't consume any resources at all other than about 20 megabytes of disk space.

Sounds like I am going to need a lot of tuning. May be there is some hope. Currently the same game run may be 100x slower under Wine 1.1.14 on a much more powerful computer than the retired P3 I used to run the game under XP. Will keep you posted if I make any progress.

---

### Post by daengbo on 2009-02-06
UranUtan,

Reflexive games are hit and miss. Your best bet is to update to the latest Wine and configure it to run in a virtual desktop of 800x600. Most of the Reflexive games will run at that resolution, anyway, and it leaves you more options than letting the game go full screen.

I've got over 7- reflexive games that work with no tweaking on my website:
[Games That Work]("http://games.ibeentoubuntu.com").

---

### Post by UranUtan on 2009-02-06
Hi,

I found "Games That Work" blog ([http://games.ibeentoubuntu.com)]](http://games.ibeentoubuntu.com)]) and wrote to the author (daengbo) who has just answered above. He gave me permission to cite his answer in the email

> **daengbo said:**
> Probably only 25-30% of reflexive games work. Since Reflexive is just a reseller in most cases, it's not really possible to tell in advance which games will work. We download the trials and test those out for an hour to make sure there are no glitches.

Of the 70% that don't work (a couple hundred now), probably half have some functionality, but on-screen glitches or mouse problems take the game out of the "just works" category. The other half either fail silently or, in some cases, hang the computer completely.

If I wanted to make some generalizations, games which require DirectX 7 or claim to be Win98 almost (but not) always work. DirectX 9 games fail 80-90% of the time. Other than that ... I've got nothing.

As a side note, the Bejewel 2 game that failed to work properly now works perfectly. May be the Ubuntu system update I made last week had fixed something.

---

### Post by darkknight045 on 2009-02-06
I also strongly recommend you have the latest drivers for your video card installed.  Wine's functionality seems to be improving drastically as the Video Drivers improve.

---

### Post by UranUtan on 2009-02-06
> **darkknight045 said:**
> I also strongly recommend you have the latest drivers for your video card installed.  Wine's functionality seems to be improving drastically as the Video Drivers improve.

Thanks, did you meant I should continue the automatic system update frequently? Or should I go somewhere else to get the graphics driver and update it myself?

My video is Integrated Intel 865G. Do you have a good source of graphic drivers to recommend for this model?

Thanks

---

