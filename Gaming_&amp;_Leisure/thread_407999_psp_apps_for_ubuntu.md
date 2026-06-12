---
title: "psp apps for ubuntu?"
date: 2007-04-12
forum: Gaming &amp; Leisure
---

### Post by Fittersman on 2007-04-12
i have ubuntu, but i have noticed that most (all) developers for programs that have something to do with the psp, develop them for windows based machines...

when i had windows (its been a while) i liked a few programs, such as an iso to cso changer, the iso editor program and a few others that i dont remember the names of..

so, anyone with a psp, what apps do you have on ubuntu that have anything to do with a psp?

---

### Post by HasratUSA on 2007-04-12
Wow! Nice to see a PSP fan in Ubuntu forum.I myself have been trying to find a Linux+PSP fan for a long time but to no avail, and I myself am looking forward to figuring out why one of the best hackers of the planet who went to the extent of bringing down Sony to their knees by constantly developing custom firmwire software and homebrew applications despite Son't futile but continous effort to keep their firmwire software's security improved and strong, didn't encourage him and other PSP homebrew apps developers to develop stuffs for PSP in GNU/Linux platform. 

By the way, one of my most favorite software (I haven't tried it yet because if I do, I will simply have a heart-attack out of sudden over-excitement LOL) is the 'one' that allows you to play ISO games off your computer's HDD by taking advantage of PSP's ability to transfer data to and from a computer through USB cables! I came across the software in question two-three days ago and it was entirely written using the GNU C compiler and also included a make file. I honestly believe that at first hackers are inventing cracks, holes, loopholes etc using or taking advantage of GNU/Linux environment and then porting their apps to Windows because most of the PSP owners are windows users, still! and hackers want as many people as possible to use their homebrew apps.

Not only in one occassion but also in several others I have seen a developer talk about compiling their souce-code from scratch using GNU C to optimize 'this and that' for the PSP. If you can tell me about a particular application for PSP you're in search of right now, may be I would be able to link you to the app's original GNU/Linux source-code, windows port or simply an alternative. I will try my best although I can't guarantee 100 percent.

However, whatever you do, never ever try to run those 'windows' programs for PSP under wine if you don't want to brick your PSP. Good luck and I'm looking forward to hearing from you :)

P.S. Have you hacked your PSP already?

---

### Post by zerosystem on 2007-04-13
HasratUSA, is there a way to play ISOs off your Linux system's hard drive? I mean, I know it works in Windows, but I get stuck on a step due to wine.

Fittersman, there is a ISO tool you can use for converting ISOs to CSOs. It's a windows program, but it works perfectly under Wine. I'll PM you with the info; I'm not sure if it's allowed on the forums.

There is a PSP video converter that works quite well, and can also create a image for the video for when you're scrolling through them in the PSP's xmb. It's called PSPVC, grab it at:
pspvc.sourceforge.net

There is another PSP utility called PSPForce. This one is linux native, and it seems to be somewhat out of date for the moment, but is nonetheless alive and features ISO compressing and management.

---

### Post by Fittersman on 2007-04-13
thanks for the replies, is there any app that will allow you to open up the iso file and take out certain files and replace them with smaller ones (to remove long boring movies that take up lots of room for example) i cant recall what the windows app was called and i cant seem to find it, and of course my psp is hacked :D (3.03 OE-C for the ability to change icons) and i will check out them apps you listed tomorrow.

umdgen is exactally what i was lookin for, thanks (thats the one i had on windows :D)

you guys wouldnt happen to have a blank .pmf file would you?

also, just another question, if you use isos or csos, how many do you have on your memory stick? (mine is 1GB and i have 3 right now) Do you edit them to be smaller by taking out the large movie clips and stuff that you dont need? (i do)

---

### Post by zerosystem on 2007-04-14
It depends on how big the games are. Of course, taking movies and music out will help, but AFAIK, PSPForce uses ripkits(?) which is basically a file that tells the program what you can safely take out. Go try PSPForce.

---

### Post by AJB2K3 on 2007-04-15
Im sure talk of iso's is illegal how ever ...
Use videolan for converting video's.
I have a virtual file psp system (mirrors the psp) on my hd and have psp specific file stored where they need to be but could do with some sort of file manager thats psp specific.

---

### Post by zerosystem on 2007-04-15
PSP works fine just as a removable drive. Just connect it, enable USB mode, and drag and drop.

You may want to try qpspmanager, though. Just google for it.

---

### Post by Fittersman on 2007-04-16
im trying to install pspvc right now, but i dont know what to do now.

so far ive double clicked on install.sh and it did its run through, now i have another folder called Work

what do i do now? (i prefer command line if you know how to do that, but anyway i can get it to work will do)

---

### Post by zerosystem on 2007-04-16
In a console, type "pspvc" to start the program. Select a file, and encode it, Don't forget to use the little screenshot thingy to make a suitabe thumbnail for your video.

It's pretty straightforward.

---

### Post by Fittersman on 2007-04-16
i already tried that, it just says that the command isnt found

it doesnt need to be somewhere special does it? or in a specially named folder? because its on my desktop right now with the folder name pspvc-install-0.3

i got pspforce working, what does that do? just iso --> cso?

---

### Post by zerosystem on 2007-04-16
Sounds like you haven't installed it.

Open terminal, cd to the folder (pspvc-install-0.3), and type

sh install.sh

PSPForce is a... ISO/game management utility. This is some text from its help window. The maker of the program is striving to make it much more useful with manipulating ISOs, like UMDGen. Since I only have CSO files right now, I can't tell you how the ISO managing goes, but it seems great.

* A gamedatabase with infos, screenshots and covers for > 500 games            
   * Ability to scan and detect games on your hdd                                 
   * Customizing of rips that can be created of full isos on your hdd             
     the data and languages you want to be included                               
   * Translations for chs, de, fr, gr, nl, no, ru, se

---

### Post by Fittersman on 2007-04-17
o, so its just like umdgen then? (i have that and i like it, so i wont bother to change)

and ill try the sh install.sh command when i get home

---

### Post by Drakx on 2008-01-05
OK, so pspvc will come in handy thanks guys :D, also does any one have a download link for PSPforce?

Edit:

There is a tool made by BOOSTER that will conver iso to cso and cso to iso also which is native to Linux too

---

### Post by DarkAngel88 on 2008-01-10
and... what is the application to do so ?

---

### Post by dlevans on 2008-04-13
i know this is an old thread but has anyone found any other psp linux apps? im basically looking for WOL to turn my computer(s) on from a hotspot, VNC so i can control them once they are on, and any other programs people have found useful. I dont download ISO's unless i own the game but i actually dont own a lot of games i just play old sega games and do the pc from anywhere thing if anyone finds something please send me a message

---

