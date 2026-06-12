---
title: "[SOLVED] flight tomarow, still need video on my ipod!"
date: 2008-12-26
forum: General Help
---

### Post by Kain000 on 2008-12-26
PLEASE HELP ME! 

I've got a long flight to mexico tomarow with alot of down time, just the chance to catch up on some of my fav shows (code monkies ect.) on my new ipod classic 120 gb.   

Problem is i've been searching for the last week for the answer, and I think i'm almost there but just cannot get it to work right.

so here is where I am so far.

the ipod is a new classic 120 gb 

I've been using Amarok to sync the music and podcasts just fine.

From what I've found the Ipod can play mpeg-4 videos so I used Avidemux to convert the .avi files to ipod friendly mpeg-4's.

Using Gtkpod-aac form the repos, I can connect and brouse my ipod.   I've 
tried just transfering the video to the ipod and saveing, dismounting and It cannot find it.     
I tried placeing in into the podcast folder... no luck, And It made a mess of my podcasts.

I've created a "video" playlist to put the video into, and that transfered and I could find it on my ipod, but it only plays the audio.

Each time under the video tab of the main menu on the ipod it shows no videos.


Does anyone have an answer for this?   I would really like to have my videos transfered for tomarow.


I know if there is anyone who could help they would be on this forum.

thanks in advance
-sean

---

### Post by Monotoko on 2008-12-26
Hmm...Ipods have something inbuilt that causes them to not play something without Media Usage Rights....Windows Media Player 11 does the same thing when it doesnt have them, just plays audio, no video.

This is just a hazzardous guess, as i dont own an ipod, but maybe thts the answer?

---

### Post by Kain000 on 2008-12-26
> **Monotoko said:**
> Hmm...Ipods have something inbuilt that causes them to not play something without Media Usage Rights....Windows Media Player 11 does the same thing when it doesnt have them, just plays audio, no video.

This is just a hazzardous guess, as i dont own an ipod, but maybe thts the answer?

ugh knowing apple, this sounds about right.....   well that sucks.  oh well audio books it is for me I guess.    thanks for the reply tho.

---

### Post by tact on 2008-12-26
I have an iPhone 3G and it plays video files and it doesn't matter if the files are with media usage rights or ripped (from legally bought media) and transcoded to the correct formats (and thus stripped of protections).

So I don't think DRM (or lack therof) is your problem.  I suspect its one of two things:
1.  You have still not hit on the correct format .  It took me a long time to find a script that produced the correct output for transcoded (converted) files so they would show up and play correctly on the iPhone.

2.  Using anything other than iTunes to sync files to your pod may be a problem.  I use iTunes to transfer all my music/video to the iPhone.  I run the windows version inside an XP VM running on ubuntu.

---

### Post by Kain000 on 2008-12-26
> **tact said:**
> I have an iPhone 3G and it plays video files and it doesn't matter if the files are with media usage rights or ripped (from legally bought media) and transcoded to the correct formats (and thus stripped of protections).

So I don't think DRM (or lack therof) is your problem.  I suspect its one of two things:
1.  You have still not hit on the correct format .  It took me a long time to find a script that produced the correct output for transcoded (converted) files so they would show up and play correctly on the iPhone.

2.  Using anything other than iTunes to sync files to your pod may be a problem.  I use iTunes to transfer all my music/video to the iPhone.  I run the windows version inside an XP VM running on ubuntu.

Thats a good idea, what virtual machine are you useing?  vm ware?

---

### Post by ispy on 2008-12-26
Virtual Box is free and I beleive it can share USB ports (you may want to google it though, i'm not sure how good it is).

I'm really interested now because i'm going to buy an ipod nano 4g and may want some video on there too.

---

### Post by Kain000 on 2008-12-26
> **ispy said:**
> Virtual Box is free and I beleive it can share USB ports (you may want to google it though, i'm not sure how good it is).

I'm really interested now because i'm going to buy an ipod nano 4g and may want some video on there too.

alright I'm going to try the virtualized xp/itunes as much as I want to do things open source I need this in the short term.   Downloading now...

---

### Post by ispy on 2008-12-26
make sure you use the .deb from the Virtualbox site not the one in the repos because I got an error message when I used the repos one.

Something about the kernel. It's easier to just use the .deb.

EDIT:
[This guide]("http://linuxmini.blogspot.com/2007/10/virtualbox-usb-setting-on-ubuntu-and.html") explains how to set up USB support for VirtualBox.

---

### Post by MarblePanther on 2008-12-26
I heard itunes works decently in WINE.  Maybe try that?
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

---

### Post by Kain000 on 2008-12-26
> **MarblePanther said:**
> I heard itunes works decently in WINE.  Maybe try that?
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

I've tried that before and it was pretty buggy, it would hang alot and freeze.  I herd tho that if you downloaded an old verition of itunes you could get the store to work.  No luck here tho.

---

### Post by ispy on 2008-12-26
> **MarblePanther said:**
> I heard itunes works decently in WINE.  Maybe try that?
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

Looked at the link

Said it works, but really slow. Also, it said that USB support doesn't work and they didn't even try video support.

I'd still stick with VirtualBox.

---

### Post by MarblePanther on 2008-12-26
I'm not sure if Rockbox will install on your ipod, but its worth a look:

[http://www.rockbox.org/](http://www.rockbox.org/)

edit: i looked!  nevermind it doesn't

*limps away with tail tucked between legs ;)

---

### Post by Kain000 on 2008-12-26
> **ispy said:**
> Looked at the link

Said it works, but really slow. Also, it said that USB support doesn't work and they didn't even try video support.

I'd still stick with VirtualBox.

yeah I just fired it back up for another try... NO ipod detect even tho it's mounted.  And really slow is an understatement..

Also couldnt inport any video files into the library

---

### Post by Kain000 on 2008-12-26
> **MarblePanther said:**
> I'm not sure if Rockbox will install on your ipod, but its worth a look:

[http://www.rockbox.org/](http://www.rockbox.org/)

edit: i looked!  nevermind it doesn't

*limps away with tail tucked between legs ;)

lol yeah when I first got my ipod and pluged into the ubuntu box and rythm box opened up I was like AWESOME linux you've done it yet again.... only to find that it wasnt as simple as all that.   too bad apple feels that it's too good for open source, except when they want some piece or project here and there, slap a new gui on it with a feature or two and call it theirs. :(

---

### Post by MarblePanther on 2008-12-26
> **Kain000 said:**
> lol yeah when I first got my ipod and pluged into the ubuntu box and rythm box opened up I was like AWESOME linux you've done it yet again.... only to find that it wasnt as simple as all that.   too bad apple feels that it's too good for open source, except when they want some piece or project here and there, slap a new gui on it with a feature or two and call it theirs. :(

Haha exactly...darwin/bsd+shiny gui=$2,000 please, oh and our hardware!

apple is the new microsoft and microsoft may be the next ibm one day

---

### Post by Kain000 on 2008-12-26
> **MarblePanther said:**
> Haha exactly...darwin/bsd+shiny gui=$2,000 please, oh and our hardware!

apple is the new microsoft and microsoft may be the next ibm one day

lol it's funny because anyone who knows much about computer's and OS's can tell you that tho OSx may be flashy and "neat" looking it's not that revolunary, or impressive actually.   

at least Steve Jobs sees that there is somthing to gain from the open source world... where as Baulmer just thinks "linux is a cancer"


Where does virtural box install to?   I Installed it via the deb and cannot find it on my system.

**edit   re-installed and found it this time**

---

### Post by ispy on 2008-12-26
> **Kain000 said:**
> lol it's funny because anyone who knows much about computer's and OS's can tell you that tho OSx may be flashy and "neat" looking it's not that revolunary, or impressive actually.   

at least Steve Jobs sees that there is somthing to gain from the open source world... where as Baulmer just thinks "linux is a cancer"


Where does virtural box install to?   I Installed it via the deb and cannot find it on my system.

you might need to log out and log back in. then it should be in the menu (I'm in an XFCE environment right now due to a broken HD, but that should work)

---

### Post by MarblePanther on 2008-12-26
At least Bill Gates was fun to make fun of!  Ballmer is just plain scary...

__

It should install a shortcut, or else try the terminal

---

### Post by Kain000 on 2008-12-26
alright got virtural box running, how do you install xp?  I've got my xp disk in the drive but it's telling me it cant read form boot media.         I have the drive mounted in the VM but it doesnt seem to want to boot from the cd.

---

### Post by Kain000 on 2008-12-26
> **Kain000 said:**
> alright got virtural box running, how do you install xp?  I've got my xp disk in the drive but it's telling me it cant read form boot media.         I have the drive mounted in the VM but it doesnt seem to want to boot from the cd.

**edit spoke too soon, wrong drive mounted... DUH!**:lolflag:

---

### Post by Kain000 on 2008-12-26
Alright, installed with Itunes, does anyone know how to transfer files from my file system to my virtural c drive?

---

### Post by Monotoko on 2008-12-26
Shared Files, you need to install the Virtualbox extras (mount the disk in your virtual XP and install) you should then be able to use shared folders

---

### Post by Kain000 on 2008-12-26
> **Monotoko said:**
> Shared Files, you need to install the Virtualbox extras (mount the disk in your virtual XP and install) you should then be able to use shared folders

alright, I've installed the "guest additions" already, and within xp, how do I mount my ubuntu filesystem?

---

### Post by Sin@Sin-Sacrifice on 2008-12-26
Don't know if this will help but I have a 30gig ipod video black and my videos work wonderfully after I type ```
ffmpeg -i /home/username/wherethefileis -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 /home/username/whereveryouwantthefile
``` into the command line. You can change some of the settings in there to fit your ipod and/or better qaulity (being as you have 120gig to work with) but that works perfectly on mine. I know of a 2 pass code for the G1 that might work, with a little manipulation, for the ipod that gets immaculate quality. Whatever works for you.

---

### Post by Kain000 on 2008-12-26
> **Sin@Sin-Sacrifice said:**
> Don't know if this will help but I have a 30gig ipod video black and my videos work wonderfully after I type ```
ffmpeg -i /home/username/wherethefileis -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 /home/username/whereveryouwantthefile
``` into the command line. You can change some of the settings in there to fit your ipod and/or better qaulity (being as you have 120gig to work with) but that works perfectly on mine. I know of a 2 pass code for the G1 that might work, with a little manipulation, for the ipod that gets immaculate quality. Whatever works for you.

nice, what do you use to put the video onto your ipod?  Gtkpod?

---

### Post by Sin@Sin-Sacrifice on 2008-12-26
Yeah... gtkpod is probably your best bet. I think there's a way to use amarok and I'm pretty sure I've used rhythmbox but it's been a while because I got the G1.

---

### Post by Kain000 on 2008-12-26
> **Sin@Sin-Sacrifice said:**
> Yeah... gtkpod is probably your best bet. I think there's a way to use amarok and I'm pretty sure I've used rhythmbox but it's been a while because I got the G1.

sweet i'll give that a try.

---

### Post by tact on 2008-12-26
> **Kain000 said:**
> Thats a good idea, what virtual machine are you useing?  vm ware?

Yep ...  am using vmware server on my ubuntu laptop to get linked up to my iPhone via the windows version of iTunes.  Its free also.  

I see you have already progressed nicely with virtualbox.  I use virtualbox too (on other machine for other things)....  virtualbox is fine.  If you find you cannot get the USB port recognised inside the virtualbox VM do some googling as I think you might need to tinker a bit to get that working (used to be needed - maybe not now?).

Note that whilst you can sync movies, music, pics, apps etc...  all fine and wonderful in iTunes in a VM.  Don't try to do a restore or install new operating firmware onto your pod/iphone - as part of the process requires rebooting the pod/iphone into a mode to accept new firmware and that process will fail and you may brick your pod/iphone (at least until you can get to a windows/Mac  iTunes box that is not running in a VM). 

Cheers

---

### Post by Kain000 on 2008-12-26
> **tact said:**
> 
Note that whilst you can sync movies, music, pics, apps etc...  all fine and wonderful in iTunes in a VM.  Don't try to do a restore or install new operating firmware onto your pod/iphone - as part of the process requires rebooting the pod/iphone into a mode to accept new firmware and that process will fail and you may brick your pod/iphone (at least until you can get to a windows/Mac  iTunes box that is not running in a VM). 

Cheers

wow thanks for the advice, that would have been a costly mistake.

I'm still trying to transfer my music over to the VM so I can import them into itunes.

---

### Post by Kain000 on 2008-12-27
does anyone know what the file extention for an ipod friendly mpeg-4 should be?  I thought it was .m4p but perhaps not.   Gtkpod wont import the file without the extention even though when I look at the properties for the file it says it's a mpeg-4 video.

---

### Post by Kain000 on 2008-12-27
Alright Gents,  (and ladies if applicable)

Done and done!    thanks for all your help and suggestions.   

I think I will be producing a How To before bed on this, as I have been searching for about a week now.


What I ended up doing:

Using Avidmux (GTK) to convert the .avi video to mpeg-4  using it's auto> Ipod format.

I had to save the file as filename.**mp4** for things to work correctly even tho it was already a mpeg 4 file.

Using Gtkpod aac to transfer the now .mp4 files to the ipod, worked like a charm.

but thanks for all the VM help, that will be helpful for many other reasons (programing, maintaining the apple extreme basestation w/o my wife's macbook)

---

### Post by kostkon on 2008-12-27
You could also try *Floola*, it's a very good iPod management application. You can download a .deb from [*getdeb.net*]("http://getdeb.net/") (although it doesn't offer the latest version) or get the latest binary from [its site]("http://www.floola.com/").

Hope that helps.

---

### Post by Kain000 on 2008-12-27
> **kostkon said:**
> You could also try *Floola*, it's a very good iPod management application. You can download a .deb from [*getdeb.net*]("http://getdeb.net/") (although it doesn't offer the latest version) or get the latest binary from [its site]("http://www.floola.com/").

Hope that helps.

Nice, that looks like the somthing i've been looking for, I dont like that I have to use two seperate apps to manage my media content.  I will look into that when I get back into town, but right now I think I will suffer threw and finish what i've started.    I was hopeful when I found songbird, but it was beta and VERY glitchy.    After the first ipod mount and transfer, it would take literly HOURS to mount.  (only waited once to see how long) Now the offical 1.0 release is out so perhaps they've fixed that.. I hope so because that is a huge flaw.

---

### Post by tact on 2008-12-27
> **Kain000 said:**
> wow thanks for the advice, that would have been a costly mistake.

I'm still trying to transfer my music over to the VM so I can import them into itunes.
No need to fill up your VM virtual HDD by copying your files to the VM.

Just share the folder (SMB) where the files are on your linux box (password the share if needed to restrict access).  Then go into the VM, windows explorer, map the shared folder to a drive letter.  Then add that to iTunes library.  It then grabs the files across the virtual network share and you dont duplicate the files and use up space unnecessarily.

Cheers

---

### Post by Kain000 on 2009-01-09
> **tact said:**
> No need to fill up your VM virtual HDD by copying your files to the VM.

Just share the folder (SMB) where the files are on your linux box (password the share if needed to restrict access).  Then go into the VM, windows explorer, map the shared folder to a drive letter.  Then add that to iTunes library.  It then grabs the files across the virtual network share and you dont duplicate the files and use up space unnecessarily.

Cheers

haha yeah that is a much better plan, thanks for the advice.

---

### Post by hyperdude111 on 2009-01-09
Try using handbrake rather than avidemux, handbrake is a lot faster for me.

---

### Post by Kain000 on 2009-02-13
> **hyperdude111 said:**
> Try using handbrake rather than avidemux, handbrake is a lot faster for me.

thats because handbrake has the ability to utilize mutable cores on a CPU

---

