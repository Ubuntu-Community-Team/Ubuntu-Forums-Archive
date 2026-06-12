---
title: "game install help"
date: 2005-08-08
forum: Gaming &amp; Leisure
---

### Post by immortal on 2005-08-08
im new to linux    --machine spec--
amd64 3000+
nvidia 5900xt (i have a 6800gtoced but it wont in ubuntu now that i have nvidia drivers install i will put it in and see if it work
1 gig 3200 ddr also as a spare i have 2 gig 2700
   (doeslinux run ram like windows if i put in all 4 chips of2700 will it be faster)
ubuntu amd64  (i used chroot but i dontthink it working)

ok what i want to do is install a game any game that is decent graphic and decent gameplay as i have cod and loki installer but i cant get them to work cause wine doesnt run in 64 also i have rtcw for linux downloaded but cant install it i also download cube_2004_05_22.tar.gz and open mortal_0.7.tar.gz but i dont know how to run tar.gz file i googled how to use it much to say it didnt explain much i tried gunzip but had no idea what i was doing it didnt tell me where to install the file or howto extract it or what ever it needs to do can anyone help me

---

### Post by tonysathre on 2005-08-08
k first [FONT=Courier New]mkdir[/FONT] (make directory from terminal), or you can do it via the gui, where ever you wanna install the game(probably under your home directory. then [FONT=Courier New]cd[/FONT] (change directory) to that directory. with the file in that directory,at the terminal type [FONT=Courier New]tar zxvf filename.tar.gz[/FONT] and press enter, this will extract all the files. then [FONT=Courier New]ls[/FONT] to see what sub-directory everything was extracted to. then [FONT=Courier New]cd [/FONT] to the new directory, next type [FONT=Courier New]./configure [/FONT] , then when that is done, type [FONT=Courier New]make[/FONT], this builds your makefiles, then type [FONT=Courier New]sudo make install[/FONT], this installs the program.
this guide works for any app you need to compile 
if you get a file that has a tar.bz2 extension use the tar command [FONT=Courier New]tar jxvf filename.tar.bz2[/FONT]

hope this help...post back if something didnt work

---

