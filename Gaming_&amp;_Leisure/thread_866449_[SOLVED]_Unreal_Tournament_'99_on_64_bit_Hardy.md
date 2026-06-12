---
title: "[SOLVED] Unreal Tournament '99 on 64 bit Hardy?"
date: 2008-07-21
forum: Gaming &amp; Leisure
---

### Post by Butthead on 2008-07-21
Hi,

Has anyone on the forum here gotten Unreal Tournament G.O.T.Y. '99 to run successfully on Kubuntu 8.04.1 x86_64 bit Hardy so far (or on any 64 bit rig, for that matter? :confused: )?  Neither Linux installer seems to work for me (but I'm by far not a Linux expert). :)

---

### Post by Butthead on 2008-07-24
Anyone?...anyone? :confused: :-k

I assume someone has been successful in getting it to run in a 64 bit environment, eh? :confused:

---

### Post by GSZX1337 on 2008-07-24
I made a topic here a little while ago asking the same thing.

No one answered. :(

---

### Post by Butthead on 2008-07-25
Hmm, I guess not then. :(

I think it's possible though, I know the "multilanguage" installer on the Loki page said it needed a certain file to be installed first (so there's some hope there).  The installer on the "Princess Leia" UT page crapped out completely on me though. :(

If I wasn't so lazy (and was better at finding needed missing files under Debian systems), I'd be tempted to try and get it (the Loki UT installer) running again.

Say what you want, Open Arena and Alien Arena (even though pretty good games in themelves) still don't measure up to a few rounds of good old UT '99 GOTY. :lolflag: 

Anyway, thanks for your answer! :guitar:

---

### Post by Joeb454 on 2008-07-25
I guess you should be able to install it under wine, if it's listed as working in the appdb.

I'm not sure though, as I'm not the biggest gamer

---

### Post by Brebs on 2008-07-25
According to the [Gentoo ebuild](http://sources.gentoo.org/viewcvs.py/gentoo-x86/games-fps/unreal-tournament-goty/), UT99 *will* work in 64-bit Linux.

It will need 32-bit libraries installed though, because the executable is 32-bit.

---

### Post by Butthead on 2008-07-26
Hmm, but would 32 bit games like UT '99 run on Wine installed on a 64 bit system though? :confused:

Thanks for the head's-up on the Gentoo ebuild, Brebs! (at least I know now that it's theoretically possible!).  I did have the 32 bit libraries installed when messing around with the UT '99 G.O.T.Y. installers, problem is, they still keep asking for a bunch of extraneous libraries to be installed first (example: libXxf86dga.so.1) that I don't think are included in Hardy Heron's base 32 bit and 64 bit file directories. :mad:

I wonder if it could be as easy as running Cappy's newest "Getlibs" program on the installers first?  Naw, that would be far **TOO** easy. :lolflag:

---

### Post by Brebs on 2008-07-27
> **Butthead said:**
> would 32 bit games like UT '99 run on Wine installed on a 64 bit system

[Yes, and here's the appdb entry](http://appdb.winehq.org/appview.php?iAppId=90). 64-bit doesn't matter - wine runs on 64-bit, with 32-bit compatibility libraries.

But "native" Linux running will most likely be preferable, for performance and stability (wine is still in heavy development).

---

### Post by Butthead on 2008-07-27
Well, that's good to know (WINe can run 32 bit games on a 64 bit system).  Thanks for the enlightenment, Brebs! O:)

But yeah, I would like to get it running natively in Hardy, if possible.  The good thing is is that if it becomes too big of a headache to get it working like that, hopefully I have enough horsepower (AMD Athlon 4600+ X2 processor & GeForce 7950 GT KO 512MB video card) to have it running eventually in WINe then. :guitar:

Thanks everybody for your help with this! :KS

---

### Post by GSZX1337 on 2008-07-29
> **Butthead said:**
> The good thing is is that if it becomes too big of a headache to get it working like that, hopefully I have enough horsepower (AMD Athlon 4600+ X2 processor & GeForce 7950 GT KO 512MB video card) to have it running eventually in WINe then. :guitar:


It's not so much the horsepower it takes to run the game, it's that Wine isn't always entirely accurate, so you may get glitches.

---

### Post by Butthead on 2008-07-29
> **GSZX1337 said:**
> It's not so much the horsepower it takes to run the game, it's that Wine isn't always entirely accurate, so you may get glitches.

Heh, can't get anymore "glitchier" than trying to find needed lib files, and then trying to determine where they go then (into the Lib32 or Lib64 directory)? :confused:  

BTW - how come I gotta install a whole Gimp plug-in to get one (1) file I need (libgtk-1.2.so.0) so hopefully the Loki installer will finally (doubtfully? ](*,) ) run for me?  And while I'm at it, why isn't there a webpage out there somewhere where I can just download libgtk-1.2.so.0 all by itself without having to download an entire package? :confused:

Wine is starting too look mighty tempting. :mad:

---

### Post by GSZX1337 on 2008-07-30
> **Butthead said:**
>  then trying to determine where they go then (into the Lib32 or Lib64 directory)? :confused:  
I don't screw around with libs too much, but maybe you can just copy it and place a copy in both directories?

> BTW - how come I gotta install a whole Gimp plug-in to get one (1) file I need (libgtk-1.2.so.0) so hopefully the Loki installer will finally (doubtfully? ](*,) ) run for me?
Because that lib is commonly used for the GIMP and was placed with the other required GIMP files? 
> And while I'm at it, why isn't there a webpage out there somewhere where I can just download libgtk-1.2.so.0 all by itself without having to download an entire package? :confused:

You sound like the perfect candidate to write a tutorial for installing this game and to code a webpage for it. ;)
> Wine is starting too look mighty tempting. :mad:
Bite your tongue! :o

---

### Post by Butthead on 2008-07-31
Ya know what, this is getting tiresome fast.  Not even taking into account that I still have to figure out how to install the bonus map packs and some extra stuff I have for the game. ](*,) 

I think I'll just take the lazy route and try out Wine.  As far as I know, Unreal Tournament is Platnium on it right now anyway.  Maybe that's why no one took the time out to answer our questions about 64 bit Ut '99, GSZX1337 because it's turning out to be such a pain in the rear. :mad:

Windows might suck as an OS, but getting stuff to run on it sure is darn tootin' easier. :rolleyes:

---

### Post by doorknob60 on 2008-07-31
*sigh* No one mentioned this yet??? [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

```
sudo getlibs ./executable-file-here
```

Works for everything I've tried so far (Skype, Mozilla Prism, probably more) (except Alarian Mod, has a big bug but it runs)

---

### Post by Butthead on 2008-08-01
Yes, "getlibs" was mentioned.  It might be worth a try.  Seems it would be much too easy if it actually worked though :-k

Problem is, even though the Linux specific Loki installers might run, the (originally programmed for) "Windows OS (tm)" Unreal Tournament programs still might (most likely :p ) choke things up. :confused:

Getting Windows things running on linux (and vice versa) is kind of like getting a Great Dane to mate with a Boston Terrier, I think.  It's theoretically possible if the stand the Boston Terrier's on doesn't collapse, or the Great Dane doesn't end up crushing it first.  That's before adding the whole 32 bit program on a 64 bit processor kink into the equation too. :rolleyes:

I'm basically lazy.  I hate going back trying to find a ton of things I've installed and try to delete them again when they (usually! ](*,) ) don't work. :mad:

---

### Post by doorknob60 on 2008-08-01
Funny coincidence, I just bought UT today, installed it on WIndows, then off to Google to see if I could run it in Linux. Looks what I ended up finding :-P [http://ubuntuforums.org/showthread.php?t=251985](http://ubuntuforums.org/showthread.php?t=251985) Ironically it's now on the first page of this forum :P It's working so far (the installer that is).  (Scroll down aways to where the guy suggests using linux32) EDIT: Game installed, works flawlessly :) A little googling (forum searching would have worked too) always does the trick :) EDIT: Grrr....it doesn't save settings :( EDIT: Oh, I probably just need to givve my user permissions to thhe root owned installation directory, false alarm :) EDIT: I tried that, it didn't work, I got scared, I realized that the installer (ran as root) made MY user preferences in ~/.loki. Change the permissions on that and your good to go :D

---

### Post by Butthead on 2008-08-02
Hmm, congratulations!  Glad you got it to work. :guitar:

I, OTOH spent the morning re-installing Kubuntu because (apparently) the getlibs trick didn't work for me, and I got a little overzealous cleaning out unneeded (or so I thought? :confused: ) files that getlibs downloaded by the ton on me. ](*,) :mad:

So, it's Alien and Open Arena for me for the time being or at least until I can screw up the courage to try Wine and UT.  You tend to forget just how many codecs you have to search for and re-install to get a K/Ubuntu system up and running satisfactorily. :rolleyes:

At least I can say that the big log-in font issue that I suffered from seems to fixed now.  Numlock light on on start-up still doesn't work though. :(

---

### Post by Butthead on 2008-08-12
Update - installed Wine (found under the "Advanced" tab at the top of System Settings  in Hardy Heron) and Unreal Tourney '99 is running as good (or better) than in Windows XP. \\:D/

My recommendation for 64 bit machines is just use Wine if trying to install UT '99 (saves on pulled-out hair frustrations). :guitar:

I guess this thread can officially be marked "solved" then.

---

### Post by GSZX1337 on 2008-08-24
I feel so damn stupid right now. There's a Unreal Tournament '99 installer for Linux [here]("http://www.liflg.org/?catid=6&gameid=51"). I used it and it works perfectly for me. Don't forget to grab the unofficial 351 patch [here]("http://utpg.org/").

---

### Post by BLTicklemonster on 2008-08-24
Here's how I installed UT GOTY on my Ubuntu64 machine:

[http://ubuntuforums.org/showthread.php?p=1694247](http://ubuntuforums.org/showthread.php?p=1694247)

Just dropped the first cd in, ran the command, and then dropped the second cd in when asked.

If you have a speed issue, I have a starter that will correct it.

---

### Post by Butthead on 2008-08-25
Hi GSZX1337 and BLTicklemonster,

Thanks for the help!  Unfortunately, GX1337, I never had any luck trying to run the Loki installer on my rig (I must have tried to do it at least six or seven times in ten different ways), and I never seemed to have any luck following your instructions either, BLTicklemonster. :(  I guess what works for some in Linux won't work for others. :confused:

Fortunately, UT '99 runs great for me in Wine. :guitar:  The only (small) complaint I have is the CityIntro seems to run a little fast (video and sound don't seem to be synched), but sounds are okay once in the actual game. \\:D/

I wonder if your "starter" would correct that for me, BLTicklemonster? :confused:  Does it run in Wine that you know of? :confused:

Anyway, thanks go out to the both of you for your appreciated help! :KS

---

### Post by BLTicklemonster on 2008-08-25
No, sorry, the starter I have loads the cpu down with junk so the system slows down enough for UT to play without speeeeding up, then jittering while the system catches up, and it is only for running UT in linux.

Glad you got it going.

Now go find a |ZARK| server (The Black Legion is a good one) and have some fun!

---

### Post by Butthead on 2008-08-26
Hi BLTicklemonster,

Naw, you guys would probably wipe up the floor with me over there. :-&

Anyway, thanks again for the help & support!  Not being able to play Unreal Tourney '99 (until trying it out under Wine, that is) was my only regret in switching from Windows. :(

Life is good now though. :popcorn:

---

