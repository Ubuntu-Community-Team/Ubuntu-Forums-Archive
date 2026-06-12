---
title: "How do I install xgl"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Se[BBB]e on 2006-06-01
Alright. Let me start by saying I'm a linux noob. So you'll have to explain everything slow and easy. What I want to do is to install xgl, I simply want those cool effects. I know there are other things involved, like compiz, but I'm very bad at what all of those things really are and I just want it to work. I've tried the Kororaa live cd and xgl works great, but I cant figure out how to get it on Ubuntu on my HDD.

I have tried various guides but only ended up with errors and it even brought down my entire SuSE installation. I want to know which guide can help me through the entire process. From a standard Ubuntu/Gnome installation (ATI gfx card) to having the effects running (I cant find one that explains it all). Then I post problems/question in this thread.

Help is very, very much appreciated. I feel so lost in linux :-|

---

### Post by LAurel on 2006-06-01
Hello,

While I'm a newbie myself, I think that [this thread](http://ubuntuforums.org/showthread.php?t=148351) is a very good starting point.

Hope it helps :) .

---

### Post by eqisow on 2006-06-01
What LAurel said. :)

Edit: I do want to mention that I don't really recomend messing with it as a newb. The software is still pre-alpha and is by no means stable.

---

### Post by JoWilly on 2006-06-01
Yep... please use the search function. There are already a dozen threads with howtos for this. ;)

---

### Post by Se[BBB]e on 2006-06-01
[QUOTE=eqisow]
Edit: I do want to mention that I don't really recomend messing with it as a newb. The software is still pre-alpha and is by no means stable.[/QUOTE]
But in Windows I'm such a 1337 :( Seriously, I'm even into programming and I run servers and all kinds of stuff...

---

### Post by JoWilly on 2006-06-01
[QUOTE='Se[BBB]e']But in Windows I'm such a 1337 :( Seriously, I'm even into programming and I run servers and all kinds of stuff...[/QUOTE]



Don't worry, xgl/compiz is very easy to install. Just follow the howtos.

---

### Post by Se[BBB]e on 2006-06-01
First problem.

"1. Get your xorg.conf setup properly. The main thread has more than enough information on this. Follow it paying attention to the ATI differences that are well noted." 

An /etc/x11/xorg.conf file doesn't exist. And even if it did, I wouldnt know what to add or what to search the forums to get an answer. I guess Xorg is not installed but I have no idea how to install it.

Alright, I looked at another howto and followed the instructions to install Xorg.

When I wrote "sudo apt-get update" lots of text scrolled past and finally and error reading "GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: Följande signaturer kunde inte verifieras för att den publika nyckeln inte är tillgänglig: NO_PUBKEY 31A5F97FED8A569E" (following signatures could not be verified because the public key is not available).

Then I tried the second line in the howto ("sudo apt-get dist-upgrade") it returned "Invalid operation "dist-update""

And when I write "sudo gedit /etc/x11/xorg.conf" I still get an empty file.

I used these howtos:
[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)
[http://www.ubuntuforums.org/showthread.php?t=132406](http://www.ubuntuforums.org/showthread.php?t=132406)

---

### Post by egsgaard on 2006-06-01
Xorg should be installed by default - it is the graphical server. Did you make a text-only install?

---

### Post by JoWilly on 2006-06-01
[QUOTE=egsgaard]Xorg should be installed by default - it is the graphical server. Did you make a text-only install?[/QUOTE]

:mrgreen:

Really, /etc/X11/xorg.conf should definitely be there...

---

### Post by egsgaard on 2006-06-01
"When I wrote "sudo apt-get update" lots of text scrolled past and finally and error reading "GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: Följande signaturer kunde inte verifieras för att den publika nyckeln inte är tillgänglig: NO_PUBKEY 31A5F97FED8A569E" (following signatures could not be verified because the public key is not available)."

for all non-scandinavian, the error is: "for the following signatures, it could not be verified that a puplic key is aviable" or something like that :)

---

### Post by mgmiller on 2006-06-01
I think you may be getting tripped up by case sensitivity.  You wrote that you can't find /etc/x11/xorg.conf.  This is correct, that path does not exist.  try /etc/X11/xorg.conf and see what happens.  The directory name is X11 not x11.  Using tab complete when you enter commands can speed things up a lot too.  

Good luck

---

### Post by JoWilly on 2006-06-01
[QUOTE=egsgaard]"When I wrote "sudo apt-get update" lots of text scrolled past and finally and error reading "GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: Följande signaturer kunde inte verifieras för att den publika nyckeln inte är tillgänglig: NO_PUBKEY 31A5F97FED8A569E" (following signatures could not be verified because the public key is not available)."

for all non-scandinavian, the error is: "for the following signatures, it could not be verified that a puplic key is aviable" or something like that :)[/QUOTE]

... just click on the link you have just posted, on the first page it explains how to add the key ;)

---

### Post by pauljwells on 2006-06-01
[QUOTE=mgmiller]I think you may be getting tripped up by case sensitivity[/QUOTE]

Good advice for ppl used to Windows. Linux is case sensitive - I've wasted many an hour searching for bugs to find I just missed a capital letter in a conf file...

Take care with typing!

---

### Post by Gustavo on 2006-06-01
[This topic]("http://compiz.net/viewtopic.php?id=652") may help you.

---

### Post by Se[BBB]e on 2006-06-02
[QUOTE=pauljwells]Good advice for ppl used to Windows. Linux is case sensitive - I've wasted many an hour searching for bugs to find I just missed a capital letter in a conf file...

Take care with typing![/QUOTE]
lol yeah, I forgot... I knew that. It's annoying me as hell, but I guess it's just a bad old DOS/Windows habit.

---

### Post by Se[BBB]e on 2006-06-02
I'm sorry to double post but I need everyone's attention.

I've configured my xorg.conf as instructed and followed the guide to install compiz and xgl on ATI. Everything worked out. But when I start Ubuntu I get a blue screen with random ASCII characters on them and the text "The X server is incorrectly configured". I chose OK, logged in manually and wrote startx. The same blue screen appeared, but the my desktop suddenly started loading. But it's just as before. No xgl, no effects.

---

### Post by PriceChild on 2006-06-02
you can't really notice the difference with xgl (much anyway)

It is "compiz" which really gets the blood flowing!

Pricey

---

### Post by Se[BBB]e on 2006-06-02
Ok but I've installed compiz and xgl and it doesnt work.

---

### Post by JoWilly on 2006-06-02
[QUOTE='Se[BBB]e']I'm sorry to double post but I need everyone's attention.

I've configured my xorg.conf as instructed and followed the guide to install compiz and xgl on ATI. Everything worked out. But when I start Ubuntu I get a blue screen with random ASCII characters on them and the text "The X server is incorrectly configured". I chose OK, logged in manually and wrote startx. The same blue screen appeared, but the my desktop suddenly started loading. But it's just as before. No xgl, no effects.[/QUOTE]

Have you started xgl (editing /etc/gdm/gdm.conf-custom) and STARTED compiz ?

Also... I think that startx actually starts xorg, and not xgl...

---

### Post by Se[BBB]e on 2006-06-03
That file reads

[servers]
0=inactive
1=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer
flexible=true

in the end. If the problem is that it's not started, can I start it manually some way?

---

### Post by DeeZiD on 2006-06-03
I've updated the HowTo for ATi-users.
The new drivers seem to have the same quality as the nvidia ones.
Even fbos are possible and everything is snappier.

[http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860)


regards Dennis

---

### Post by Se[BBB]e on 2006-06-03
Since my install is now messed up I'll reinstall the entire system and try with the new guide.

----

I have followed to guide and done exactly as it said but now my freshly installed Ubuntu refuses to start without manual login and displays errors at start. The troubleshooting section in the new guide is no help. IT says I should run a command to shutdown compiz but my machine just says "no process quit".

Maybe it's because I havent installed the proprietary ATI driver, but that's seems to be as hard as installing compiz/xgl...

---

