---
title: "Check this out! Open Source World War II german submarine simulation"
date: 2006-04-16
forum: Gaming &amp; Leisure
---

### Post by Teroedni on 2006-04-16
[http://dangerdeep.sourceforge.net/](http://dangerdeep.sourceforge.net/)

Description
Danger from the deep (aka dangerdeep) is a Free / Open Source World War II german submarine simulation. It is currently available for Linux/i386 and Windows, but since it uses SDL/OpenGL it should be portable to other operating systems or platforms. (If anyone whishes to port it, please contact us.) This game is planned as tactical simulation and will be as realistic as our time and knowledge of physics allows. It's current state is ALPHA, but it is playable. If anyone want's to contribute in development, you're welcome, just email the dangerdeep-devel mailing list. Contributing binary packages for various Linux distributions would also be much appreciated.


I have just tried it and liked it alot. The graphics is very good and i will definitiv playe this game more....It is unfortunally a little unstable, but still a very good gameplay:)

---

### Post by ubernoob on 2006-04-16
Wow! Thats the best graphics i have ever seen on an opensource game. :D I'll give it a try!

---

### Post by Perfect Storm on 2006-04-16
Added the game to the ubuntu gamelist last year :cool: 
I havn't tried it yet, I'm not into such games but ut looks cool.

---

### Post by ubernoob on 2006-04-16
i just tried it. It was nice graphics, but too many buttons for me to understand. I guess i can't learn how to handle a submarine all by my self in 5 minutes :)

---

### Post by Footissimo on 2006-04-17
Reminds me of an great old Microprose (I think) game called Silent Service.  I don't suppose the debian binary works on Breezy does it? May well try this after Savage :)

---

### Post by dolny on 2006-04-17
It works flawlessly on my Dapper. Anyway, please check the Savage thread, maybe you'll be able to help me.

---

### Post by void_false on 2006-04-17
Mmm... SUSE packages. Cool, Gonna try now.

EDIT:
Installed the game without any issues and tried to play for few minutes. All I can say is WOW. Graphix are brilliant. Tried every button on my keyboard and it didnt help me to master the submarine. ;) What is really missing is a tutorial missions. On the other hand - outstanding job, devs!

---

### Post by Sealbhach on 2009-06-08
I've been playing it recently. Really cool graphics and soundtrack, but yes a nice demo would be good to get the basics, or even a help HUD would be nice.

.

---

### Post by cmay on 2009-06-10
> (If anyone whishes to port it, please contact us.)
anyone knows if it is hard to compile under open solaris. ?

---

### Post by sloggerkhan on 2009-06-11
I trede it a while ago, it was looking pretty good... Will be a pretty sweet game if it gets finished up.

---

### Post by imdmill on 2009-06-11
I checked out the website and was really excited to try it.  Installed it like I normally would install a .bin file, but when I run the "dangerdeep" command in the terminal to start the game, i get the following message.

```
daniel@Daniel-lappy:~$ dangerdeep dangerdeep: error while loading shared libraries: libfftw3f.so.3: cannot open shared object file: No such file or directory
```

Does anyone know the problem/ a fix to it?

---

### Post by sloggerkhan on 2009-06-12
try searching synaptic for tha tlibrary.

---

### Post by rosswmcgee on 2010-12-25
I can't figure out how to install this game, anyone know how?

---

### Post by huwjenjinn on 2010-12-31
> **rosswmcgee said:**
> I can't figure out how to install this game, anyone know how?

There's an Ubuntu PPA being maintained for this on Maverick, Lucid and Karmic here:

[https://launchpad.net/~aegirxx-googlemail/+archive/dftd-latest](https://launchpad.net/~aegirxx-googlemail/+archive/dftd-latest)

Should just be able to add the relevant link to your 'other software sources' list and then install DFTD through your preferred installer.

I'll be installing myself as soon as I get back to my PC (next week) so will check back in here to see if that's worked for you else I'll post up some command line stuff!

Good luck.

---

### Post by realzippy on 2010-12-31
How to install:
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo apt-get update
sudo apt-get install dangerdeep-latest
```


Manual:
[http://dangerdeep.sourceforge.net/dangerdeep_manual.pdf](http://dangerdeep.sourceforge.net/dangerdeep_manual.pdf)

---

### Post by alaukikyo on 2010-12-31
[QUOTE=realzippy;10300031]How to install:
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo apt-get update
sudo apt-get install dangerdeep-latest
```
Manual:
/QUOTE]

if someone prefers the gui then 

1. Go to Applications -> Software Center -> Edit (menu) -> Software Sources -> Other Software(tab) -> Add(button) then paste 'ppa:aegirxx-googlemail/dftd-latest' then close  software center and search for dangerdeep in the software center and install it . :)

---

### Post by realzippy on 2010-12-31
Anyone running NVIDIA 260.19.29 and having any problems with that game?
Unfortunately game crashes here after few minutes...

---

### Post by uidb4056 on 2010-12-31
> **realzippy said:**
> Anyone running NVIDIA 260.19.29 and having any problems with that game?
Unfortunately game crashes here after few minutes...

Hi have the same problem running with NVIDIA 260.19.06 on 10.10, I would appreciate any tip to be able to run without crashes.

---

### Post by nacho32 on 2011-01-16
> **alaukikyo said:**
> [QUOTE=realzippy;10300031]How to install:
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo apt-get update
sudo apt-get install dangerdeep-latest
```
Manual:
/QUOTE]

if someone prefers the gui then 

1. Go to Applications -> Software Center -> Edit (menu) -> Software Sources -> Other Software(tab) -> Add(button) then paste 'ppa:aegirxx-googlemail/dftd-latest' then close  software center and search for dangerdeep in the software center and install it . :)

I tried that and it installed but fails to show under games? any idea ?
I get the impression this game is like the windows based game thats call Silent Hunter, would like to try it out using Linux Mint 10

---

### Post by nacho32 on 2011-01-16
> **alaukikyo said:**
> [QUOTE=realzippy;10300031]How to install:
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo apt-get update
sudo apt-get install dangerdeep-latest
```
Manual:
/QUOTE]

if someone prefers the gui then 

1. Go to Applications -> Software Center -> Edit (menu) -> Software Sources -> Other Software(tab) -> Add(button) then paste 'ppa:aegirxx-googlemail/dftd-latest' then close  software center and search for dangerdeep in the software center and install it . :)

I tried that and it installed but fails to show under games? any idea ?
I get the impression this game is like the windows based game thats call Silent Hunter, would like to try it out using Linux Mint 10 sorry for multi post heavy server forum host lag

---

### Post by nacho32 on 2011-01-16
> **alaukikyo said:**
> [QUOTE=realzippy;10300031]How to install:
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo apt-get update
sudo apt-get install dangerdeep-latest
```
Manual:
/QUOTE]

if someone prefers the gui then 

1. Go to Applications -> Software Center -> Edit (menu) -> Software Sources -> Other Software(tab) -> Add(button) then paste 'ppa:aegirxx-googlemail/dftd-latest' then close  software center and search for dangerdeep in the software center and install it . :)

I tried that and it installed but fails to show under games? any idea ?
I get the impression this game is like the windows based game thats call Silent Hunter, would like to try it out using Linux Mint 10

---

### Post by uidb4056 on 2011-01-16
You can run it from terminal, dangerdeep --help will give you different options to start it.
Alternatively you can edit your menu adding under games a new launcher where you can put in the command line dangerdeep with your preferred options.

---

