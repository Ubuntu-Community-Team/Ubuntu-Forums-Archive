---
title: "I refuse to give up ubuntu."
date: 2006-08-25
forum: Desktop Environments
---

### Post by Guns90 on 2006-08-25
Wine is proving to be, by far, the hardest installation I've encountered.  I have attempted all the suggested installs I found in my forumn searches, but I have failed to get wine installed/working.  Maybe I need to go back and start from scratch.

1.  I only have a few Windows learning programs that I want to use wine with.(Mind Power Math Review, Mavis Beacon, Spanish Tutorial, etc.)  Do I even have to have wine, or are there Linux equivelants?

2.  Should I try to remove (if that's even possible now) what I have already installed (pertaining to wine) and reinstall?  (I have tried so many 'howto's', I can't even rememmber what I've installed.)

3.  What is the best known 'howto install wine' site?  I clicked on WIKI, then did a wine search.  It gave me seven links.  (I'm using Dapper)

I would very much appreciate some assistance on this matter.  Thanks.

---

### Post by indytim on 2006-08-25
Guns90,

There's an excellent "how to" posted in the how-to's.  I used it successfully in Breezy and will be tackling it soon in Dapper. Link attached:

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=WINE]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=WINE")

IndyTim

---

### Post by Guns90 on 2006-08-25
indytim, That was the first one I tried.  There's no way I can remember all the error codes.  If I remember correctly, it couldn't find some site during the install.  I even read all eleven pages of replies, but my issue wasn't covered.

---

### Post by zxee on 2006-08-25
Have you looked at the winehq site itself? [http://www.winehq.org/](http://www.winehq.org/)
There are some excellant docs there. I just recently started playing with wine again, and in slackware anyway I've managed to get stuff working that has me suprised. As the wine folks say it's always best to use the latest release possible. What version is on the repos. The latest release is 0.9.20

---

### Post by Guns90 on 2006-08-25
zxee, I was trying to install 0.9.19.  I thought 0.9.20 was the beta version.  I always wait for the released version.  (I know I'm not smart enough to fix bugs.)

---

### Post by Metacarpal on 2006-08-25
[Frank's Corner]("http://frankscorner.org/") has quite a bit of useful information on WINE.

---

### Post by Guns90 on 2006-08-25
Thanks Metacarpal, it looks like a very useful site; however, it seems to most helpful once wine is installed.  Unfortunately, I'm not there yet.

---

### Post by Guns90 on 2006-08-25
Let me try one question at a time.

1. I only have a few Windows learning programs that I want to use wine with.(Mind Power Math Review, Mavis Beacon, Spanish Tutorial, etc.) Do I even have to have wine, or are there Linux equivelants?

---

### Post by petersjm on 2006-08-25
Well, you could search over at [http://sourceforge.net](http://sourceforge.net) for software alternatives, if you're okay with installing from source - although some will have debs.

As a Mavis alternative, you could try:
[Typing Trainer](http://sourceforge.net/projects/typingtrainer), or
[TypeFaster Typing Tutor](http://sourceforge.net/projects/typefaster)

I can't see anything for learning Spanish, and I've no idea what that Power Math thing is, but you might have better luck finding something suitable yourself.

---

### Post by Guns90 on 2006-08-25
Thanks petersjm, I appreciate the url.  As for the Power Math thing, its's a math review program for Algebra I, Statistics, Algebra II, Geometry, Trigonometry, and Calculus.  It's a real nice refresher after a summer break.

---

### Post by petersjm on 2006-08-25
Ah, that's why I don't know of it... I'm not brainy enough! LOL. Good luck finding something native to Linux that's suitable. There must be something out there...

---

### Post by Guns90 on 2006-08-25
I'm not brainy enough either.  It's for my kids.  It comes in real handy if you've forgotten a rule or formula.

---

### Post by Guns90 on 2006-08-25
Okay, now my second question...

2. Should I try to remove (if that's even possible now) what I have already installed (pertaining to wine) and reinstall? (I have tried so many 'howto's', I can't even rememmber what I've installed.)

My last attempt at installing was at [http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine) . When I entered the code tar -xf winetools*, it responded with 

gary@my-desktop:~$ tar -xf winetools*
tar: winetools: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
gary@my-desktop:~$

I wouldn't know where to begin to uninstall it now.

---

### Post by Metacarpal on 2006-08-25
winetools is really best used only if you can't get your programs to run under a basic installation of WINE.  It's sort of a toolset to change the WINE configurations a bit, install some fonts, and get InternetExplorer working under WINE (though why, I have no idea).

Installing winetools doesn't actually give you WINE.  If you'd like to install WINE, you have two options:

To install the latest Ubuntu-specific release of wine, open a terminal (Applications menu > Accessories > Terminal) and type:

```
sudo aptitude update
```
then give it your password and wait for it to do its thing and give you a prompt again.  Then type
```
sudo aptitude install wine
```
and the package manager will do the rest.

If you prefer using a graphical interface instead of the Terminal, you can also install WINE using Synaptic (System > Administration > Synaptic), clicking Reload, then searching for WINE.  You then click the box next to wine (screw caps, lol) and select "Mark for Installation".  Then click Apply.  (I gave the command line version first because it's fewer total steps...)


You can also get the most up-to-date version of wine from the winehq website using Synaptic.  Open Synaptic, then click Settings > Repositories.  Click Add, Custom, and paste in the following:
```
deb http://wine.budgetdedicated.com/apt dapper main
```
Then do the same thing to add:
```
deb-src http://wine.budgetdedicated.com/apt dapper main
```
Then click Reload and search for wine, etc.

If you already have wine installed, then after adding the new repositories, you can click the box for your existing wine package and then select "Mark for upgrade"

---

### Post by Guns90 on 2006-08-25
Sorry I left without as much as a goodbye.  I shut down my computer while I was gone.  When I just booted back up, I had an available update pop up.  I clicked on it and it downloaded version 0.9.20 of wine, so I guess that I do have wine installed.  It doesn't appear in my Applications Menu though.  I'd like to have wine show up in the menu.  

The install that I did claimed to have installed IE 6.0 and had me test to see if it was working alright.  Everything worked fine at that time, but just now, as I booted back up, I tried the same terminal command 'wine IEXPLORE.EXE' and I got a blank WINE INTERNET EXPLORER window and my command line showed this.....

gary@my-desktop:~$ wine IEXPLORE.EXE
fixme:shdocvw:IEWinMain "" 1
fixme:rpc:I_RpcServerStartListening (0x10024): stub
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000001,00000000): stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x17e07c)->((null) 1 0x33fb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17e07c)->((null) 25 2 0x33fb20 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17e07c)->((null) 26 2 0x33fb20 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa34 0x33fa80 (nil) 0x33fa44)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa34 0x33fa80 (nil) 0x33fa44)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x17e07c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClientSite_GetContainer (0x17e07c)->(0x33fb4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17e07c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fc50 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
err:urlmon:URLMonikerImpl_BindToStorage InternetCrackUrl failed: 87
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000000,00000000): stub
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cf10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cec8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x17dd00, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x16c880, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
gary@my-desktop:~$


Any suggestions?

---

### Post by sulobanks on 2006-08-25
Check this one out. I had the same problem as you and this worked great.

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by Guns90 on 2006-08-25
Thanks sulobanks.  I guess that I didn't make myself very clear.  I could care less about ever being able to use Internet Explorer again.  I was only trying to give an example of what I am getting on the command line.  

I think things would be a little easier for me if I could get Wine to be listed on the Application menu.  Any ideas how I can make that happen?

---

### Post by Metacarpal on 2006-08-25
Strictly speaking, Wine isn't an application.  It's a compatibility layer that enables running Windows-based executable files (.exe) in a Linux OS.  Once Wine is installed, you can usually either choose an exe file on your system and right-click then choose "Open with WINE", or often simply double-click the .exe and Wine takes over.

Alternately, you can use Wine from the command line (also great for launchers) by typing
```
wine [path][program]
```
where path is the faux-windows directory where the program was "installed" in your /home/username/.wine/ folder.  For instance, if a program called woohoo.exe was installed "in" c:/Program Files/woohoo/ then your command entry would be:
```
wine c:/Program Files/woohoo/woohoo.exe
```

---

### Post by peabody on 2006-08-25
Hmm, I simply installed wine from the dapper repositories, sudo apt-get wine.  I've been able to use the dapper wine for WarCraft and Monkey Island 4 and it seems to run the ies4linux script really nicely which I was amazed with (automated script that installs ie5.01, ie5.5 and ie6sp1).

The one thing you need to understand about wine is that it isn't a point and click thing and it has limited functionality out of the box and can't get everything running.  Some people manage to get things working by copying dll files from a windows machine to their wine install.  Still, wine is basically a compatibility layer for Linux to run windows apps and A LOT of functionality of Windows simply isn't completely emulated yet.

While I haven't used it myself, you may wish to try out CrossOver people.  They sell point and click stuff for Wine (mostly focussed on Office to my understanding, but I believe they have a generic frontend that can be used for all apps).

Bottom line is, unless you've got testimony from someone else that the particular applications you're trying to get working do work in Wine, there simply is no gaurantee they will.

---

### Post by Guns90 on 2006-08-26
Just to let ya'll know that your advice was not in vane, I do in fact have wine installed and configured like the how to says it's supposed to be.  I installed the Math Review PC and the Spanish programs by right clicking on their .exe files.  They seemed to load properly (at least they went through the whole loading process that they did under windows), but I haven't been able to get either program to run.  The Math program locks up when I click on 'start', and the Spanish program doesn't get past the first data I input.  If I can find a way to make them work I'll post it back in here.  

Thanks for all the help guys.  I truly appreciate it.

---

### Post by zxee on 2006-08-26
> **Guns90 said:**
> Just to let ya'll know that your advice was not in vane, I do in fact have wine installed and configured like the how to says it's supposed to be.  I installed the Math Review PC and the Spanish programs by right clicking on their .exe files.  They seemed to load properly (at least they went through the whole loading process that they did under windows), but I haven't been able to get either program to run.  The Math program locks up when I click on 'start', and the Spanish program doesn't get past the first data I input.  If I can find a way to make them work I'll post it back in here.  

Thanks for all the help guys.  I truly appreciate it.

I don't remember if I mentioned this in this thread or not but opening > winefile seems to provide better app launching than just using the wine <application.exe> command.
After winefile opens you can navigate to the app you're trying to run and then just double click it.

---

### Post by Guns90 on 2006-08-27
Thanks zxee, but I can't even get them to open through winefile.

---

### Post by bbarrons on 2006-08-27
morning guns,
I installed edubuntu awhile back because I was looking at putting this onto a few computers at the elem school in the computer lab. It was full of math, science, and language programs. You might just find what you are looking for there. About wine, its good to drink but I never found it very easy to setup and use in linux. I did test crossover office with quite a few different windows applications and it worked with most. I didnt use it past the trial stage because I found I could live without windows programs. 
wine runs thru command lines. You wont find it in the start menu.
crossover will setup  links for you in the menu.
good luck in your search....
Bill

---

### Post by Guns90 on 2006-08-27
Bill, I now concur with your assessment of wine.  I have been trying (unsuccessfully) to run every windows program I have.   I've become too frustrated with it and just unistalled it.

I think I'll give edubuntu a try to see what kind of luck I might have with it.  May I assume that edubuntu installs exactly like ubuntu?  Will I be able to dual boot with edubuntu installed on my second hard drive?

---

### Post by bbarrons on 2006-08-27
you should be able to install edubuntu thru synaptic. The programs avail from edubuntu should then be avail. I did setup a duak boot when I first tested it because I was using the dapper beta and edubuntu was 5.1. If you setup  a dual boot it has a very elementary grade look to it. If your kids are of that age they might really like it.
Bill

---

### Post by bbarrons on 2006-08-27
If you install edubuntu thru syn you will have all the educational software installed in your applications menu. no need to dual boot unless that is what you want for your kids......

---

### Post by Guns90 on 2006-08-28
Thanks guys, It seems to be working fine.  The screen savers are little juvenile, but I've always thought that kids need to be kids.  Thanks again.

---

