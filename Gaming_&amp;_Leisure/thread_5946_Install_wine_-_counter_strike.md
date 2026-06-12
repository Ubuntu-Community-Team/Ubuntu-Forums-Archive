---
title: "Install wine - counter strike"
date: 2004-11-23
forum: Gaming &amp; Leisure
---

### Post by spirospr on 2004-11-23
I installed wine, configured it and made an installation of counter strike 1.5

Everything to work fine but i have those two problems :

1. I manage to load the game but after passing the menus and finally go into the game nothing happens. It seems like everything is loaded but nothing is displayed in the screen.

2. I have no sound

Any suggestions? I attached the config file of the wine

I have heard about cedega but i don't want to pay. If so i would have stay in windows.....

---

### Post by BWF89 on 2004-11-23
How did you go about making an installer? Did you just configure Wine or did you write an installer? And, how easy is it to do something like you have just done?

---

### Post by spirospr on 2004-11-23
[QUOTE=BWF89]How did you go about making an installer? Did you just configure Wine or did you write an installer? And, how easy is it to do something like you have just done?[/QUOTE]

Well it is not very difficult. You install wine and winesetuptk from synaptic , then run wine from terminal and configure it by winesetup. For exmple for installing a game you mount the cd and then give the command "wine d:\setup" It will be installed in your fake windows folders. Then you run it doing the same "wine /?????/????" Where questionmarks the path for the folder where the windows executable file is.

There is some documentation, if you search, for more details....

---

### Post by BWF89 on 2004-11-23
So with a little configuring you can run alot of Windows games on Linux useing Wine?

---

### Post by Ozitraveller on 2004-11-23
What is commandline to mount cd?

I can see the contents of the cd in nautilus, but couldn't install.

---

### Post by spirospr on 2004-11-24
[QUOTE=Ozitraveller]What is commandline to mount cd?

I can see the contents of the cd in nautilus, but couldn't install.[/QUOTE]

You don't have to do it by commnd line. Just right click on the icon of your cd-rom and select mount. After you will have to run the installation file with wine. For exmple this could be :

[COLOR=Red]wine d:\setup[/COLOR]

Normally this shoud work.

---

### Post by Ozitraveller on 2004-11-24
Thanks for the info.

I'm just curious as to why I need to mount the cdrom, for the game, when I browse the cd from nautilus and it works. Doesn't that mean the cdrom is mounted correctly?

---

### Post by spirospr on 2004-11-25
[QUOTE=Ozitraveller]Thanks for the info.

I'm just curious as to why I need to mount the cdrom, for the game, when I browse the cd from nautilus and it works. Doesn't that mean the cdrom is mounted correctly?[/QUOTE]

Well it think that the instruction about mounting the cd rom is just to be sure that it is loaded. Ofcourse if you can browse the cd-rom , it is mounted.

I tried to load some games to play with wine in Ubuntu but nothing. So i think i will settle down to windows when it comes to gaming. 

Does enyone have a good site for cs source maps?

---

### Post by plasmo on 2004-11-25
wine isnt really made for gaming
you would want to try out cedega [winex] which is wine but has 3d support
i can run my steam / cs:s / cs1.6 nicely on cedega under ubuntu

---

### Post by spirospr on 2004-11-26
[QUOTE=plasmo]wine isnt really made for gaming
you would want to try out cedega [winex] which is wine but has 3d support
i can run my steam / cs:s / cs1.6 nicely on cedega under ubuntu[/QUOTE]

You are right. After some searching around i came to the conclusion that i will need cedega if i want to play games on linux. But here is my thinking:

1.Why should i pay for software that simulates (even if it doesn't as most say , i think that this is how it works) windows services so that i can play games on linux? 

2. The main reason i turned to linux is the idea of a community where everything is shared to achieve a goal

3.If i had to pay i would stick to windows where everything is simpler

I think that dual booting will be the option for me until i get tired.

I know that my thinking is not very suitable for a linux forum and might provoke some. But this how it works for me.

---

### Post by Martijn on 2005-02-26
[QUOTE=plasmo]wine isnt really made for gaming
you would want to try out cedega [winex] which is wine but has 3d support
i can run my steam / cs:s / cs1.6 nicely on cedega under ubuntu[/QUOTE]


What about the steam/game updates? Do they work so I can play on all servers?

---

### Post by bored2k on 2005-02-26
[QUOTE=Martijn]What about the steam/game updates? Do they work so I can play on all servers?[/QUOTE]


i use cedega 4.2.1
steam has updated correctly my games and yes i can play on official 1.6 servers

---

### Post by Martijn on 2005-02-26
[QUOTE=bored2k]i use cedega 4.2.1
steam has updated correctly my games and yes i can play on official 1.6 servers[/QUOTE]
 Well.... thats great :D

---

### Post by DJ_Max on 2005-02-26
[QUOTE=spirospr]You are right. After some searching around i came to the conclusion that i will need cedega if i want to play games on linux. But here is my thinking:

1.Why should i pay for software that simulates (even if it doesn't as most say , i think that this is how it works) windows services so that i can play games on linux? 
[/QUOTE]
You don't have to pay, Cedega is freely available, you don't get support or Point2Play. If you want both, you just pay $5. And it doesn't really simulate.
[QUOTE=spirospr]
2. The main reason i turned to linux is the idea of a community where everything is shared to achieve a goal
[/QUOTE]
Right, and thats what you got.
[QUOTE=spirospr]
3.If i had to pay i would stick to windows where everything is simpler
[/QUOTE]
Paying $5 doesn't seem like a lot, considering everything else is free & open source.

---

### Post by Martijn on 2005-02-27
waar is cedega gratis te krijgen dan ?

---

### Post by DJ_Max on 2005-02-27
[QUOTE=Martijn]waar is cedega gratis te krijgen dan ?[/QUOTE]
English :confused:

---

### Post by Martijn on 2005-02-28
[QUOTE=DJ_Max]English :confused:[/QUOTE]
 Sorry :) 

Were can I get cedega for free? If i search on google I find sites were I have to pay for...

---

### Post by Snipersnest on 2005-02-28
You should be able to find the CVS version for "free" ...But your not going to find a very current copy free, not to mention the updates. 

TG just released an update for CS:Source due to the recent Steam Patch this month. Seems the Steam source code has a bad memory leak and it floods out under Linux. Windows ends up almost freezing after you exit with this bug. You might be able to find that patch for free so your Cedega and Source play nice together. GL w/ that.

I don't understand why someone wouldn't be willing to give $5 a month to a worthy development. You get to pick what they should update or change by being a subscriber and you get the updates instantly. When you first sign up you pay for 3 months in advance ($15). 

But most people I've seen you the "free" version have tons of problems no one else runs into with the "subscribed" copy.  Hope this helps!

---

### Post by Martijn on 2005-03-01
[QUOTE=Snipersnest]You should be able to find the CVS version for "free" ...But your not going to find a very current copy free, not to mention the updates. 

TG just released an update for CS:Source due to the recent Steam Patch this month. Seems the Steam source code has a bad memory leak and it floods out under Linux. Windows ends up almost freezing after you exit with this bug. You might be able to find that patch for free so your Cedega and Source play nice together. GL w/ that.

I don't understand why someone wouldn't be willing to give $5 a month to a worthy development. You get to pick what they should update or change by being a subscriber and you get the updates instantly. When you first sign up you pay for 3 months in advance ($15). 

But most people I've seen you the "free" version have tons of problems no one else runs into with the "subscribed" copy.  Hope this helps![/QUOTE]
 Thanx, I'll keep searching


I'll tel you you why 5$ is to much:)

I only get 15 euro of pocketmoney a month... so that those $5 will be 33% of that... thats way to much for me!

---

### Post by bored2k on 2005-03-01
[QUOTE=Snipersnest]You should be able to find the CVS version for "free" ...But your not going to find a very current copy free, not to mention the updates. [/QUOTE]

Yes you can find a VERY updated CVS Cedega.
There is a script made by the guys from Linux-Gamers wich automatically updates CVS Cedega version.

It's posted **[here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45) ** 

Sometimes this CVS will not work ... why ? Because its a CVS..daily updated , and sometimes the developer might leave in an unusable state, so if  it doesnt work "today", try "tomorow" .

BTW, I use the official Cedega 4.2.1 -nonfree- [without Point2Play -dont like gui-... nothing that apt-get install msttcorefonts and Xover Office 4.1-nonfree- can't do !].

---

### Post by bored2k on 2005-03-01
BTW, for anyone using the script on the last post, when asked for a password #-o .... its cvs  8-) .

---

### Post by Beire on 2005-03-01
[QUOTE=plasmo]wine isnt really made for gaming
you would want to try out cedega [winex] which is wine but has 3d support
i can run my steam / cs:s / cs1.6 nicely on cedega under ubuntu[/QUOTE]


yeah but i cant get it to work here. there's a thread on my plroblem in the hoary forums.

I'm trying the cvs version. Others aren't free :(

---

### Post by Snipersnest on 2005-03-01
lol the others aren't free because you get support and a full tested working copy!  CVS is just code where the dev team may have left off in the middle. You can't expect it to work like the real subscribed version.  

Its $5 a month, thats if you want to keep getting support and updates... Its $15 just to get the software and 3 months of support. Its well worth supporting too.

---

### Post by fuzzylogic on 2010-04-16
I have ubuntu 9.10 OS and need to know which wine version is the best and how to install it..
Thanks

---

### Post by Dnasty777 on 2010-04-16
> **fuzzylogic said:**
> I have ubuntu 9.10 OS and need to know which wine version is the best and how to install it..
Thanks

Its pretty easy, just go to ubuntu software center and type "wine" in the search and it should install itself.

---

