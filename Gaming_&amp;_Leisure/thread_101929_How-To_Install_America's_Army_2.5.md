---
title: "How-To Install America's Army 2.5"
date: 2005-12-10
forum: Gaming &amp; Leisure
---

### Post by bjweeks on 2005-12-10
This how-to will cover installing Americas Army on breezy. Americas Army or AA is a free FPS paid for by the U.S. Army, it comes in Windows, Mac and Linux clients.

Get the game from the AA download page, it is 734 MBs.
[AA Download Page]("http://www.americasarmy.com/downloads/")

Now Change to the directory you saved it in. In my case my home directory.

```
cd /home/bjweeks
```
The file I downloaded was called "armyops250linux.run", change it if yours was different.

Make the file executable.

```
chmod +x armyops250linux.run
```

Then run it.

```
sudo ./armyops250linux.run
```

Ingnore the warning, 
hit exit at the license agreement,
say yes to the license agreement,
say ok at the directory scree,
say no to the symbloic links,
say yes to base install, 
say yes to startup entries.

Your done! Now you need to create an account [here]("http://login.americasarmy.com/views/register_01.php"). You have to complete the boot camp maps before you can play on serers. Post any feedback and if you need any help with boot camp or want to play pm me.

---

### Post by Hanzerik on 2005-12-12
And please make sure your Video Card Acceleration is working before trying to run this game. You can check it by using glxgears.

---

### Post by tomwell on 2005-12-13
Hey,

Dont want to worry anyone but wouldnt you guys worry about a free game by the US Army available on linux + Windows + Mac??? sounds iffy...!!! Me defo not going to install!!!

Not that am paranoid or anything...!!

Lol

Peace

Tom

---

### Post by bjweeks on 2005-12-13
Ok... you do that:rolleyes:

---

### Post by tomwell on 2005-12-13
Bj, is the rolleyes.gif directed to me???

Have you heard of echelon???

[http://www.echelonwatch.org/](http://www.echelonwatch.org/)

Enjoy the read and then come back and talk about worrying about installing government softrware on ur pc...

;o)

Peace

Tom

---

### Post by Breepee on 2005-12-13
[QUOTE=tomwell]Bj, is the rolleyes.gif directed to me???

Have you heard of echelon???

[http://www.echelonwatch.org/](http://www.echelonwatch.org/)

Enjoy the read and then come back and talk about worrying about installing government softrware on ur pc...

;o)

Peace

Tom[/QUOTE]
:rolleyes:

---

### Post by tomwell on 2005-12-13
[QUOTE=Breepee]:rolleyes:[/QUOTE]


Breepee??? Whats that about?? Any words come out of ya???

Peace

tom

---

### Post by bjweeks on 2005-12-13
[QUOTE=tomwell]Bj, is the rolleyes.gif directed to me???

Have you heard of echelon???

[http://www.echelonwatch.org/](http://www.echelonwatch.org/)

Enjoy the read and then come back and talk about worrying about installing government softrware on ur pc...

;o)

Peace

Tom[/QUOTE]
:rolleyes:

---

### Post by tomwell on 2005-12-13
[QUOTE=bjweeks]:rolleyes:[/QUOTE]

[QUOTE=breepee]:rolleyes:[/QUOTE]


Now that's what i call "Orignal"!!!

LAMO!!! Ooooooo sorry thats LMAO!!!


Tom

---

### Post by bjweeks on 2005-12-13
Did anybody read the how-to?

---

### Post by tomwell on 2005-12-13
[QUOTE=bjweeks]Did anybody read the how-to?[/QUOTE]

Read The how to, Great how to might i add... But the fact that its governement software I would never add it to my box....

We have a thread running...

[http://ubuntuforums.org/showthread.php?t=103203&goto=newpost](http://ubuntuforums.org/showthread.php?t=103203&goto=newpost)

Peace

Tom

---

### Post by ninocass on 2005-12-13
[QUOTE=tomwell]Hey,

Dont want to worry anyone but wouldnt you guys worry about a free game by the US Army available on linux + Windows + Mac??? sounds iffy...!!! Me defo not going to install!!!

Not that am paranoid or anything...!!

Lol

Peace

Tom[/QUOTE]


:rolleyes: :rolleyes: :rolleyes: :rolleyes: :rolleyes: 

ohhh noooozzzzzz govt in my puterrrrrrr ;)

only kidding m8, i know what you mean, its pretty scary what they can get away with monitoring and with everything becoming more dependant on internet/IT they can monitor (VOIP is my main stigma i bet theres a load of people listening in on that!!!)

following guide now, just downloading the last 50MB :D

Nino

---

### Post by tomwell on 2005-12-13
Ninocass,

I am going nuts about the fatct that all these ricans are telling me that ther gvt would not try and control them or there pcs...,  but then they freak out when they hear about TC or M$ going crazy....!!!

LMAO!!!

Peace

Tom

---

### Post by ninocass on 2005-12-13
you have to ask yourself a question, does G. bush even know what a computer is????? ;)

---

### Post by ninocass on 2005-12-13
okay this is where the fun begins:

ive ran the glxgears and i can see the purdy animation

this is my terminal after install:
```

nino@LAPTOP:~$ chmod +x aa.run
nino@LAPTOP:~$ sudo ./aa.run
Password:
Verifying archive integrity... All good.
Uncompressing America's Army for GNU/Linux 2.5.0.....
Second stage unpacker running...
Starting actual installer...

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.
nino@LAPTOP:~$

```

how to i start the game?

---

### Post by tomwell on 2005-12-13
[QUOTE=ninocass]okay this is where the fun begins:

ive ran the glxgears and i can see the purdy animation

this is my terminal after install:
```

nino@LAPTOP:~$ chmod +x aa.run
nino@LAPTOP:~$ sudo ./aa.run
Password:
Verifying archive integrity... All good.
Uncompressing America's Army for GNU/Linux 2.5.0.....
Second stage unpacker running...
Starting actual installer...

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.
nino@LAPTOP:~$

```

how to i start the game?[/QUOTE]


Dude You have gone too far...!!!


Just blow up your PC....!!!!

LMAO!!!


Tom

---

### Post by ninocass on 2005-12-13
hee hee

its working a treat thanks for the how to!!!!!!

---

### Post by bjweeks on 2005-12-13
I'm and glad you could install it, I  hope you have fun playing it. tomwell stop posting in the thread till you have something usefull to say.

---

### Post by tomwell on 2005-12-13
[QUOTE=bjweeks]I'm and glad you could install it, I  hope you have fun playing it. tomwell stop posting in the thread till you have something usefull to say.[/QUOTE]

BJ WEEKS can you stop posting into our europeen thread please....

You are getting onto our nerves.....!!!!!


Now JUST STOP!!!!

---

### Post by ninocass on 2005-12-13
think i spoke too soon when i load up the MOUT mission it gets as far as the "Xoldiers creed" part and then stalls ive been waiting for over 15 minutes

---

### Post by bjweeks on 2005-12-13
What are your computer specs?

---

### Post by ninocass on 2005-12-13
Processor

Model : Intel(R) Pentium(R) M processor 1.73GHz



Mainboard

Bus(es) : ISA X-Bus PCI IMB PCMCIA CardBus USB FireWire/1394 i2c/SMBus



Total Memory : 504MB DDR2-SDRAM



Chipset 1

Model : Dell Computer Corp 82915PM/GM/GMS, 82910GML Host Bridge

---

### Post by bjweeks on 2005-12-14
It's the video card.

---

### Post by ninocass on 2005-12-14
video card is:

Video System

Adapter : Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family

take it theres nothing i can do?  uninstall time :( :(

---

### Post by bjweeks on 2005-12-14
I don't think so, that card is lame but it is a laptop so...

---

### Post by jekamean on 2005-12-14
Thanks for taking the time for the howto, I forgot about aa until i read it, i will be installing it tonight

Tom, AA is a great game that the army developed to 1. get people interested in the army as a recruting tool, and 2. to help the soldiures they have develop team/squad skills. Studies have shown that even when they are in their down time, they play this game. They started out by moding fps's (dont remember which ones) and decided to get a game to do what they want, (not show your team mates) they would develop their own. 

Dude, it is also out on xbox

---

### Post by gil-galad on 2005-12-14
I have some problems with this howto.  You seem to be making it more complicated than it is.  

1)  You should be able to just double click the install file in nautilus and hit "run" There is no need to set permissions or run from the command line.

2)  You do not need to be root to install the game.  It might be better to simply install the game to the users home folder.

---

### Post by ninocass on 2005-12-14
loaded it up on the PC, ive completed all the training including the SF stuff

the joining game menu is bloody confusing, how the hell do i get a US loadout i keep getting stuck with that sodding AK

nino

---

### Post by bjweeks on 2005-12-14
[quote=gil-galad]I have some problems with this howto.  You seem to be making it more complicated than it is.  

1)  You should be able to just double click the install file in nautilus and hit "run" There is no need to set permissions or run from the command line.

2)  You do not need to be root to install the game.  It might be better to simply install the game to the users home folder.[/quote]

1) I never tired this but is doesn't work because the installer needs root to install to /usr

2) Same as above.

---

### Post by bjweeks on 2005-12-14
[quote=ninocass]loaded it up on the PC, ive completed all the training including the SF stuff

the joining game menu is bloody confusing, how the hell do i get a US loadout i keep getting stuck with that sodding AK

nino[/quote] 
On SF maps you only get the US kit if you compleated all the SF training.

---

### Post by gil-galad on 2005-12-14
[QUOTE=bjweeks]1) I never tired this but is doesn't work because the installer needs root to install to /usr

2) Same as above.[/QUOTE]

No, it doesn't.  It installs to the home directory if you run it as user.

---

### Post by bjweeks on 2005-12-15
[quote=gil-galad]No, it doesn't.  It installs to the home directory if you run it as user.[/quote]
No, it doesn't.

---

### Post by gil-galad on 2005-12-15
[QUOTE=bjweeks]No, it doesn't.[/QUOTE]

Yes, it does.  :)

---

### Post by bjweeks on 2005-12-16
No, try installing it.

---

### Post by FierceDeity on 2005-12-17
man, that last SF mission is crazy...

---

### Post by bjweeks on 2005-12-17
Yep, I never have beat it myself.

---

### Post by gil-galad on 2005-12-17
> No, try installing it.

Ok.

---

### Post by nalmeth on 2005-12-17
good job on howto
I will install shortly

In regards to tom, I wouldn't worry about it too much. Since the game is open source, any malicous pieces would be detected by some of the gurus out there. And since freedom is such a sensitive issue with the OS community, I think that any organization attempting to break civil rights would be more careful than to do so blatantly against those who are so ready, and are actually seeking such behavior. 
No, I think this type of software has more use as a conditioning tool, which is of course nothing new.
I will just enjoy the fun and games. I'm sure its a pretty sweet fps.

In regards to others, if this issue doesn't mean anything to you, do you spend more energy rolling your eyes or simply ignoring the post?

---

### Post by nalmeth on 2005-12-17
wow, i just saw the discussion that was going on, and eventually locked regarding this issue..

So to rectify what could be a continuation of *that*.. ahh theres little to say that won't polarize the issue.

I say we all kick-back, relax, cut down the coffee, enjoy what we have, and aim for a happy world, full of smiles und sunshine! :p

---

### Post by Fibre on 2005-12-18
Thanks BJweeks I'll be saving this and looking at it in the future once my head has gotten around a few things with Ubuntu. Sounds like it's a great game and thanks for the entertainment regarding safety issues good side thingy :)

Saved for a later date, tanks much, can't wait.

There free to look at me there's nothing to see LOL. being a NEWbee.

---

### Post by bjweeks on 2005-12-18
[QUOTE=gil-galad]Ok.[/QUOTE]
Bah that not the installer I got... wtf?

---

### Post by Fibre on 2005-12-18
I gotta go with gil-galad I first tried the how to and come up to some problems then I thought I'd just try gil-galad's explanation and bam it's on to easy.

I'm a newbie and frankly it couldn't have been easier.

I havn't played it yet because I'm just about to go to bed it's to late to start now but it's installed and ready to go.

Gil-galad wrote on #27 page 3 thanks for your input gil-galad.

---

### Post by bjweeks on 2005-12-18
I don't get the GUI installer its just CLI. I will try it on my other box...

---

### Post by Fibre on 2005-12-18
I think what you've done is good bjweeks. I'm just a newbie and was lucky that the program gil-galad mentioned was on my system.

Custimization tips and tricks on home page in the Ubuntu breezy 5.10 section
[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

**Arnieboy** has put a great download together that gives you a wide range of software called Automatix, I think thats the name. It installs all  programs of your choosing all at once and does some clean up afterwards. You can pick and choose what you want and it even has some drivers for nvidia, which I did'nt need because I have ATI.

Being a noob it probably saved me a week of headache's lol.

Took an hour or so to do it very painless. I would recommend it to anyone who would like to try out a number of programs and just couldn't be bothered to take the time to work out how to download and install them.

But make sure you read about it before using it it may not suit everyone. And I think it's mainly for Ubuntu. Others have used it though but it's not full proof, not that anything is.

---

### Post by neurosis on 2005-12-19
[QUOTE=tomwell]Bj, is the rolleyes.gif directed to me???

Have you heard of echelon???

[http://www.echelonwatch.org/](http://www.echelonwatch.org/)

Enjoy the read and then come back and talk about worrying about installing government softrware on ur pc...

;o)

Peace

Tom[/QUOTE]

:rolleyes: 

Sony, on the other hand.. :)

---

### Post by Dark Damo on 2005-12-20
Hmm i only get about 20 fps in Americas Army 2.5 on Windows 2000 pro :( I plan  on switching my GeForce 6200 for an Radeon 9800 pro and see how i go on linux hehe

---

### Post by Brynster on 2005-12-20
I used the install tips used here butin Linux the latest version i could find was amyops230-linux.run so a little editing of the commands it installed fine.

When i launched the game it said it couldn't find a lib file. quick hunt in synaptic et voila file found, installed, and the game runs great getting 30-40 fps with a 28 athlon XP 512mb and a Geforce FX5500 (256mb on board version)


Thankyou.

---

### Post by Fibre on 2005-12-20
Yeah I wasn't to impressed with the online gaming I'm not great at the game and I get my buttocks kicked but that's not the problem.

The only servers showing seem to all be over seas and I've got a 1500 adsl connection but get roughly a 250 ping on the best server up for offer. 

how do I check my fps on this game or anygame for that matter - I've got no idea when it comes to Ubuntu. If thats my ping though I'd say I'm the same as you with the fps problem.

Perhaps if I lower my resolution and also I think I may have driver issue's something I'm still saughting out.  

I notice a difference with games on xp when lowering the resolution with call of duty united offensive that was with another lesser card though, when playing on the net. I did have a fx5200 128mb, now I have the ati sapphire radeon 9550 256mb. Man what a difference, and it's the bottom of the range ati card. Does well with quake4-doom3 where as my previous card had tiny little annoying gaps. Not very smooth game play. Apparently the 9550 has the same architecture as the 9600 anyway. Can be a little noisy but I'm so hooked into the games and the sounds right up, so I don't hear it LOL.

One thing I have noticed is with cube, on my xp it wasn't bad, but it's definitly faster on Ubuntu. But then again I didn't have the 9550 in the pc so yeah.

---

### Post by Brynster on 2005-12-20
once ypu have connected to a server in America's Army you can check your ping by pressing F1.

To return to the game press F1 again.

Indifferent games the ping will be usually shown on a menu somewhere. You will need to check for others as i cannot advise with knowing which game it is your playing.

---

### Post by Fibre on 2005-12-20
ok, will do. Thanks mate, not that happy with aa but I'll give it a few more goes before I kick it.

Between the pings and the constant deaths LOL it's not that enjoyable. Although I don't really know the maps so I don't know where the objectives are :)

---

### Post by bjweeks on 2005-12-26
Sorry about the mix up in the how-to, I am on a trip and it will be changed the day I get back.

---

### Post by Ninjapimp on 2006-01-03
Yes, i've read the how-to and find it usefull. :smile:

---

### Post by JonnyM on 2009-05-05
No need to mess around with all this, There is now a GUI that Downloads and Installs Americas Army for you. See [http://25assist.com/downloads.html](http://25assist.com/downloads.html)

---

