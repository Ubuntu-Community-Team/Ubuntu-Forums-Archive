---
title: "Dreamweaver 8 and Flash 8 WORKING on Ubuntu!"
date: 2006-09-30
forum: Desktop Environments
---

### Post by mark2741 on 2006-09-30
I just wanted to post this as I recall when it was originally posted a while back (by someone else) it got flamed by someone who intimated that it didn't really work....

Well, I followed these directions a couple of weeks ago:

[http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)

...and they wouldn't work for me because of the step in their about copying one of the Windows folders called Application Data\Macromedia. I couldn't find mine because it turned out it was hidden. Prior to knowing that I was able to run Flash and DW 8 but I would get the "You need to reinstall" window basically saying there was something fishy with my registration. 

Sure enough when I found out that the app data folder in windows was hidden and then copied it over to my wine folder it now works great. I've had flash 8 and dw8 running on Ubunut (at the same time, on different desktops!) for about 8 hours straight now with no issues.

So...it worked for me. I know that for myself, who has been using Ubuntu for about 7 months straight now, there have been only 2 things I didn't like about it: 1. No Macromedia apps and 2. No clean, simple to use personal finance app. 

Well, #1 is now officially taken care of!

---

### Post by djRobbieF on 2006-09-30
Congrats!  So... who needs Windows??  ;)

PS - My QuickBooks runs fine under wine...  just a thought towards #2.  Or, if you don't already have QuickBooks, [MyBooks Pro]("http://www.appgen.com/aptus/my_books_professional_linux2.htm") for Linux looks promising...

---

### Post by Footer on 2006-10-01
You should try KMyMoney:

[INDENT][http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html)[/INDENT]

It's for KDE but it is definitely a clean, simple to use personal finance app!  Give it a try!

:)

---

### Post by ProjectWhat on 2006-10-01
I cant get dreamweaver 8 to work at all. When I run under wine it shuts off for a couple of minutes. Then install shield pops up saying that dreamweaver was interupted. That I should restart the install. 

* Note I do not have windows on my desktop.


wait i just thought of something. I have windows on my laptop. So if I can install it on my laptop then do the transfer files thingy it should work right?

---

### Post by mark2741 on 2006-10-01
It doesn't matter where you get th Dreamweaver install files, so long as they are already on a Windows pc (installed there originally). While there may be a way to install into Wine and then try it that way my guess is if that worked someone would have figured it out long ago (like codeweavers, etc who haven't been able to do it (or aren't interested for whatever crazy reason).

I had the entire suite installed on my Windows XP OS which resides on the same PC as my Ubuntu partition. I just followed the directions and copied everything over and did what the directions stated, except for the couple of critical typos in it like the conversion of the reg key (make sure you read ALL of the comments on that webpage to find the correct way to do it). The one thing that hung me up was that I forgot about the hidden folders thing and at first couldn't find my APplication Data\Macromedia folder because it was hidden. Finally someone came along and posted a comment to clue me in on that and then I got it to work!

One thing I have not been able to do is create a launcher. I *have* to manually navigate via a terminal to the proper folder and then type: 

wine Flash.exe

or wine Dreamweaver.exe

For whatever reason a .sh file or a launcher won't work. I have no idea why. All I know is it ain't working for me unless I start directly from the folder and from the terminal. Strange, but it works! I haven't had time to do a lot of testing with them but they seem to work flawlessly so far. I loaded both Dreamweaver and Flash 8 at the same time and left my PC on for a day and came back and everything was still running fine - no crashes.

---

### Post by mark2741 on 2006-10-01
Just thought of something...it's a lot of hassle but if you're like me and you really wanted these apps on linux for a long time then it'd be worth it.

If you have the Dreamweaver 8 or Studio CD and a Windows XP (or 98, 2000) install CD then you could just install vmware server on your ubuntu system and then create a windows vmware image and then install dreamweaver 8 and flash 8 into that. Then burn a CD (can you burn a CD from a vmware image? I'm assuming you can) or somehow xfer the files from that to your ubuntu box and do the procedure that way. 

Either way be sure to let me know how you made out. Good luck!

---

### Post by panki on 2006-10-10
Just a quick note, I got Dreamweaver 8 working on Edgy... just apt-get install wine, then installed the package, and the run dreamweaver.exe...

No problems, no delays...

---

### Post by mark2741 on 2006-10-11
You serious? By "installed the package" do you mean you just inserted your dreamweaver cd and installed it into wine and it all worked fine?

If that's the case then I really have to believe that Macromedia/Adobe planned for this and is leaning towards supporting a linux version of studio within the next couple of releases. Certainly they should work towards that at least for Flex.



> **panki said:**
> Just a quick note, I got Dreamweaver 8 working on Edgy... just apt-get install wine, then installed the package, and the run dreamweaver.exe...

No problems, no delays...

---

### Post by BKK on 2006-11-05
I kind of had them working. ha

I could make a launcher work by typing this in the command:

gksudo wine "/home/USERNAME/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe"

The  " " are essential.

I also followed the guide but I still get the "need to reinstall" thing

Hope that helped, if you know what I may be missing that'd be great too!

---

### Post by jackkerouac on 2006-11-05
> Just a quick note, I got Dreamweaver 8 working on Edgy... just apt-get install wine, then installed the package, and the run dreamweaver.exe...

No problems, no delays...

Me too. I just installed it with Wine and it worked great. I have it running right now, actually.

[[IMG]http://img221.imageshack.us/img221/635/screenshotpt1.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screenshotpt1.png)

---

### Post by BKK on 2006-11-06
Wow! Just install like normal using wine!? OK I'll try that for Flash 8 as well. If it works I'll be as happy as a pig in poo!
--How about running beryl- that shouldn't affect anything -- right?

---

### Post by randlieb on 2006-11-06
> **panki said:**
> Just a quick note, I got Dreamweaver 8 working on Edgy... just apt-get install wine, then installed the package, and the run dreamweaver.exe...

No problems, no delays...

i have wine installed. i did it to get ies4l (Internet Explorer for Linux) installed to test web pages on IE (which i did and they work fine). i also thought i'd go ahead and install flash mx and fireworks mx. can't get them to open though. i click on the flash.exe and get a brief flash (no pun intended) of the flash splash screen and then nothing. same with fireworks. i know this is discussing flash 8 not mx but i figured if 8 is working surely mx would?

i'm on edgy, also.

---

### Post by BKK on 2006-11-07
Same thing I can get the Flash 8 and the Fireworks 8 install programs started, however, they don't finish. Dreamweaver 8 installed fine, no problems and it works great!

---

### Post by geoken on 2006-11-07
Can anyone comment on the speed/responsiveness of these apps(Flash in specific)? I was wondering if there was any notable "laggyness" when compared to the app runing on your XP partitions? 

I'm currently running it in VMWare and I'd say it runs at about 80%-85% of the speed that it runs in XP. I'm contemplating taking the WINE route because it would be a lot less hassle than running it through VMWare, but it wouldn't be worth it to me if it ran slower than it does in VMWare.

---

### Post by Julius on 2006-11-07
So dreamweaver is the only one that installs normally? Cuz I would love to have fireworks installed!

Update: I ran the install with Wine and it worked like a charmed. I'm using it now :)

---

### Post by geoken on 2006-11-07
> **Julius said:**
> 

Update: I ran the install with Wine and it worked like a charmed. I'm using it now :)

How does it run? When you draw an object does it animate fluidly or is it jumpy? In VMWare the app runs well but if I, for example, try and resize a shape it doesn't animate smoothly. It acts really jumpy, like it's pushing 10 FPS.

---

### Post by BKK on 2006-11-09
Any thoughts on this:
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7b0,0x00000000), stub!
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
JS Error: 
        MM is not defined
        filename: C:\Program Files\Macromedia\Dreamweaver 8\Configuration\Startup\helpDocs.js
        lineno: 2


I have Flash 8 working just fine. 
I installed Dreamweaver by running the installation file. This error occurs when starting dreamweaver. It stops and does not load any further...

---

### Post by rejser on 2006-11-10
I get the exact same problem as bkk, real anoying. Tried different wine versions, compiled myself or ready binarys. Have no clue

---

### Post by randytuggle on 2006-11-22
> **panki said:**
> Just a quick note, I got Dreamweaver 8 working on Edgy... just apt-get install wine, then installed the package, and the run dreamweaver.exe...

No problems, no delays...

I cannot get wine to work for me on Edgy. I've tried and tried...any way to make the wine configuration easy for a noob? I run VMWare Server with Win XP Home on it - but I hate it...I'd much rather just be able to run windows apps in Ubuntu- IF it's faster than running VMWare Server. Offer me some help! *I have a nephew wanting a MAC for Christmas and IF I can get wine to work flawlessly, I need to stop my sister from buying a MAC for him ASAP! I had several macs - all ended up with expensive hardware repairs - especially the damn iPods!*

---

