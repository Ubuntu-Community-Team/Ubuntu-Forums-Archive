---
title: "Americas Army 2.5 Deploy OUT NOW"
date: 2008-10-26
forum: Gaming &amp; Leisure
---

### Post by JonnyM on 2008-10-26
Americas Army 2.5 Assist is out now on GNU/Linux, Windows AND Mac OSX.

It's a completely free and highly realistic FPS shooter game and installation is as easy as just a few clicks of the mouse with this Assist Client.

Visit [http://25Assist.com](http://25Assist.com) for more Info

2.5 Assist is a Deploy Client for America&#8217;s Army, It is deigned to make the process of Installing and getting up and running with AA as easy as possible. 
If you are new to the game this little Application will fully automate the download and installation of the game from it&#8217;s own repository server and handle all the needed updates and checks. It will then guide you through the process of creating an account and then load your account details automatically when you first play.
Getting up and running with this free game is now as easy as a few clicks of the mouse.

If you already have America&#8217;s Army 2.5 this Application will make a copy of your existing installation and put it into a completely separate folder so it does not alter your existing installation and then bring everything up-to date. Once you are happy you may delete your old installation of AA if you wish

---

### Post by crazyfuturamanoob on 2008-10-26
Actually 2.5 has been released a long time ago for linux.

---

### Post by JonnyM on 2008-10-26
This deploy client has just been released, It should make install americas army on linux ALOT easier. You just install this 1.4mb file and everything is taken care of for you.

---

### Post by stefanwa on 2008-10-26
I only get second of the GUI to see and then it crashes with a "Segmentation fault" error when I try to start it with Intrepid. Any hints?

---

### Post by JonnyM on 2008-10-26
Sorry, i've never tested in intrepid, it's not out yet... but i'll be sure to get onto it soon.

---

### Post by Rotarychainsaw on 2008-10-26
Crashed in intrepid for me too. I want to play this though, so hopefully it gets going. Hows it compare to urban terror?

---

### Post by Swarms on 2008-10-26
Great work, thank you very much! :)

---

### Post by Vadi on 2008-10-26
Looks good. Does anyone have contact info for this? I'd like to suggest a few interface improvements...

Edit: erm, been flying half of the planet so my mind is foggy. jonnym, could you provide a 64bit version of the program? it looks kinda odd for me: [[img]http://www.ubuntu-pics.de/thumb/4878/screenshot_01_Wf0m6V.png[/img]](http://www.ubuntu-pics.de/bild/4878/screenshot_01_Wf0m6V.png)

---

### Post by JonnyM on 2008-10-27
Am going to install Intrepid R.C. later today and will try and get it working.

EDIT: Just tried a fresh copy of Ubuntu Intrepid 8.10 Kernel 2.6.27-7-generic, Gnome 2.24.0 and everything is working perfectly, Sorry i don't know what to do about it with being able to replicate the problem. You could try manually installing AA, Downloads at [http://hsf.zapto.org/downloads.html](http://hsf.zapto.org/downloads.html)

Just out of interest, can one of the people having trouble:>  sudo apt-get install libstdc++5

---

### Post by Polygon on 2008-10-27
is this program open source? (deploy).

i am NOT entering my account information into some random program. that is a great way to get your account stolen.

---

### Post by Vadi on 2008-10-27
> **Polygon said:**
> is this program open source? (deploy).

i am NOT entering my account information into some random program. that is a great way to get your account stolen.

Unless you compile every application yourself (but if you're on Ubuntu, chances are you don't) you're in equal danger of getting your account stolen.

---

### Post by Perfect Storm on 2008-10-27
Going to give it a whirl! :popcorn:
Looks like a great app.

---

### Post by Polygon on 2008-10-27
> **Vadi said:**
> Unless you compile every application yourself (but if you're on Ubuntu, chances are you don't) you're in equal danger of getting your account stolen.

i dont enter my americas army password randomly, i only enter it on the americasarmy.com website, and then the actual game itself. Being required to enter it on a program made by some guy i have never heard of before, (and therefore the program is not made or supported by the army), it just makes me highly nervous as i have heard many things from my brother and from other video games saying that these kinds of things, skill calculators, game 'enhancers' and all that are a major reason why people get their accounts stolen.

even though this game is free, id rather not have to start all over, go through teh stupid training and work my way up to 20 honor just so i can play SF maps.

---

### Post by JonnyM on 2008-10-27
Sigh, Why would i spend all this time developing an application to steal peoples America's Army accounts?? What would i even do with them.. Play AA? WHY?    Use a packet sniffer to check what its sending if you want. The App will be released open-source eventually when I'm done developing it.
It doesn't matter anyway because this app isn't really aimed at people who already have AA.

---

### Post by Vadi on 2008-10-27
Some people are simply paranoid :)

---

### Post by Rotarychainsaw on 2008-10-27
Will installing through this client make the sound work? I installed the normal installer, but I got no sound. Can't wrestle with it right now.

---

### Post by JonnyM on 2008-10-28
New version out today.. 1.2

Deploy should automatically update itself, if it does not download from [http://25deploy.co.uk](http://25deploy.co.uk)

Whats New...
Fixed Segmentation fault in Intrepid.

Better handling of PB Updates.

Checks if compiz desktop effects are running and option to turn it off (causes graphics corruption in the game).

Option to change the sound driver America's Army uses to OSS or ALSA. (for those of you having sound problems).

And fullscreen/windowed option.

Enjoy.

---

### Post by Rotarychainsaw on 2008-10-28
I dont see any updated packages? Site still says 1.0, I re DL'd still segfaulting.

---

### Post by JonnyM on 2008-10-29
Sorry, Have updated the page now.

---

### Post by Vadi on 2008-10-29
> **JonnyM said:**
> 
Checks if compiz desktop effects are running and option to turn it off (causes graphics corruption in the game).

I believe this is only an issue on ATI cards, not nVidia ones

---

### Post by Rotarychainsaw on 2008-10-29
Still no good. Segfault

---

### Post by JonnyM on 2008-10-29
Have you installed all the latest ubuntu updates?
The only thing can suggest is to delete all the files in folder /home/USER/.25deploy/
but don't delete the armyops folder or you have to download AA all over again.

---

### Post by Rotarychainsaw on 2008-10-29
I am on a brand new 8.10 install, updated. I'm x64 though, that might be why. 

nothing in .25deploy.

---

### Post by JonnyM on 2008-10-29
Ah, I've never tested in 64-bit, have you tried installing this:
> sudo apt-get install ia32-libs

And if it's still not working try launching like this:
> export GTK_PATH=/usr/lib32/gtk-2.0
./AA-25Deploy-Linux

---

### Post by Rotarychainsaw on 2008-10-29
Gets a lot farther running the export command, but still segfaults before I can do anything. You have source? I can compile it.

---

### Post by JonnyM on 2008-10-29
This is written on realbasic and that does not have a 64-bit compiler, have you had a look at this thread [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Rotarychainsaw on 2008-10-29
Getlib says all dependencies are good. It looks like I could manually go through and install all the dependencies through getlib if I knew what they were. Sounds like a pain though.

---

### Post by doorknob60 on 2008-10-29
I get a segfault on Arch 32 bit...meh oh well IDRC :P

---

### Post by Vadi on 2008-10-29
I'm on 64bit intrepid and it worked fine

---

### Post by JonnyM on 2008-11-01
Version 1.3 now out.

New Features..

Automatic download and installation of TeamSpeak
TeamSpeak Account Managment
Built-In Buddy List
Online Chat Room Built-in
PulseAudio Support AA and TS (LINUX)


[http://25deploy.co.uk](http://25deploy.co.uk)

---

### Post by Vadi on 2008-11-01
Are there any restrictions on redistributing the linux version?

---

### Post by JonnyM on 2008-11-01
No, You can do as you please with it. I will also put the source code up on [http://aa25deploy.sourceforge.net/](http://aa25deploy.sourceforge.net/) at some point.

---

### Post by JonnyM on 2008-11-04
Version 1.31 Released 
New Features.. 
Completely re-written code for launching AA (Mouse Bug) (MAC) 
SafeMode Mouse driver option (LINUX) 
Fixed standing dead people bug(LINUX) 
Option to load-in your config files from your old install (Mac & Linux) (will not show up if your old config files are not there) 
Fixed major bugs with the built-in chat room (ALL) 

Enjoy.

---

### Post by JonnyM on 2008-11-07
Hi, Does anyone know how i can get this included in the ubuntu repositories?

---

### Post by Vadi on 2008-11-07
Here you go: [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

Be prepared for a rather slow and beauractatic process however, as my and others exprienced showed. Ubuntu doesn't do too well in this part. Prolly because they dont have enough people who do it (MOTU's) or something, no idea.

---

### Post by Vadi on 2008-11-07
Thanks for posting it up on sf.net btw. We'd like to get it added to playdeb.net, but I got this error when I opened the project file:

[http://www.ubuntu-pics.de/bild/5335/screenshot_01_Q1Y4ZD.png](http://www.ubuntu-pics.de/bild/5335/screenshot_01_Q1Y4ZD.png)

---

### Post by JonnyM on 2008-11-07
OK, Have uploaded those files now in a zip file.

---

### Post by decades on 2008-11-14
great stuff.

how can i uninstall the previously install of aa?
can I start game from applications menu or I must start from aa-deploy file?

---

### Post by JonnyM on 2008-11-15
You will most likely find your old install of AA in /usr/local/games/armyops just delete that folder.
You can write a script to manually launch the AA executable but it is better to launch from Deploy itself because it checks for updates when starting up and launches with various command line arguments. You can put your Deploy executable on the desktop or in your home folder and make a link into your Applications Menu.

---

### Post by blitzer on 2008-11-17
WOW !  Impressed !
Clicked your link in the post and downloaded and extracted to documents folder doubled clicked the icon for AA-25deploy-Linux. Deploy launched and asked me if I had Americas Army installed I clicked NO and away it went to downloading and installing (Fast Server :))

Very well done I hope Linux 3.0 is in your (Linux) future :lolflag: 
Perfect all the way around and then some.  All the features included especially PunkBuster updates - TeamSpeak - Chat built in, to much to list.

JohnnyM:
> installation is as easy as just a few clicks of the mouse with this Deploy Client.
This is the biggest understatement for gaming in linux :guitar:  
:KS:KS:

> **JonnyM said:**
> Americas Army 2.5 Deploy is out now on GNU/Linux, Windows AND Mac OSX.

It's a completely free and highly realistic FPS shooter game and installation is as easy as just a few clicks of the mouse with this Deploy Client.

Visit [Http://25deploy.co.uk](Http://25deploy.co.uk) for more Info

2.5 Deploy is a Deploy Client for America’s Army, It is deigned to make the process of Installing and getting up and running with AA as easy as possible. 
If you are new to the game this little Application will fully automate the download and installation of the game from it’s own repository server and handle all the needed updates and checks. It will then guide you through the process of creating an account and then load your account details automatically when you first play.
Getting up and running with this free game is now as easy as a few clicks of the mouse.

If you already have America’s Army 2.5 this Application will make a copy of your existing installation and put it into a completely separate folder so it does not alter your existing installation and then bring everything up-to date. Once you are happy you may delete your old installation of AA if you wish

---

### Post by drarem on 2008-11-17
Sweet utility, all should be this easy. I installed it on amd64-bit, but I did have those lib32 libraries already.

The only sad part is, development has ceased on this game.

---

### Post by Dropknee on 2008-11-19
Segmentation Fault here, any fix???

---

### Post by Vadi on 2008-11-19
Ubuntu version?

---

### Post by Dropknee on 2008-11-19
8.10

---

### Post by ZootHornRollo on 2008-11-21
i am downloading this now and it is painfully slow!!!

like 1 hour and still not completed 26MB...

any ideas for spedding it up?

using deploy client.

---

### Post by &amp;co on 2008-11-21
> **Dropknee said:**
> Segmentation Fault here, any fix???

Try sudo. Fixed it for me.

---

### Post by JonnyM on 2008-11-21
I know, the download speed is embarrassing, it is all explained here [http://25deploy.co.uk/repo/readme.txt](http://25deploy.co.uk/repo/readme.txt)

Basically i used up my 1tb of bandwidth for the month and deploy has switched to the backup server.

---

### Post by Vadi on 2008-11-21
edit: nm. have you considered using sourceforge for the hosting?

---

### Post by blitzer on 2008-11-23
Hi JonnyM,

Just got the message to update to ver. 1.35 to 1.36 without a readme on your [Home Page]("http://25deploy.co.uk/Home.html").  Just like to know why I would like to update or informed of what changed.

Checked the forums here and found nothing ?

Just curious no worries :guitar:

---

### Post by Gondee on 2008-11-26
Wow, this is a lot of things packed in to one location. Very good idea, and very well done. So glad i found this!!

---

### Post by JonnyM on 2008-11-30
2.5 Deploy Version 1.51 Released.

Changes,

Major re-design of the user interface, Looks more like its part of the game.
Ability to join passworded servers.
Lots of minor bug fixes.

The primary server is now back up so downloads should be back to full speed.

See [http://25deploy.co.uk](http://25deploy.co.uk)

---

### Post by Jive Turkey on 2008-12-01
I would think twice before installing any software from the US DoD.  You have no idea what those people are capable of.

---

### Post by KingHanco on 2008-12-01
Like the army be at his website door. lol

---

### Post by Vadi on 2008-12-01
Looks very nice now.

---

### Post by JonnyM on 2008-12-13
Good news for people who are having trouble downloading or have slow internet connections.. 
You can now order the 2.5 Deploy CD-ROM, It Includes an installer that installs 2.5 Deploy and the Americas Army 2.5 System files so you don't have to download anything. 
The software is totally free but you must pay for postage and packaging. 

For more info or to order see [http://25deploy.co.uk](http://25deploy.co.uk)

---

### Post by Vadi on 2008-12-13
That's a great idea.

---

### Post by Toffeeapple on 2008-12-13
> **Jive Turkey said:**
> I would think twice before installing any software from the US DoD.  You have no idea what those people are capable of.

I'm with you there bro!

: )

having said that, I'm crap, I couldn't get through the training part, so it all may just be sour grapes on my part... bastards!

---

### Post by lacie on 2008-12-13
hm i downloaded and extracted the Deploy, but when i start it, it opens an empty window..  and after 4 seconds it greys out and ends..

Someone had the same error?

---

### Post by Polygon on 2008-12-16
> **Jive Turkey said:**
> I would think twice before installing any software from the US DoD.  You have no idea what those people are capable of.

oh just take off your tinfoil hat. yes, the game is designed as a recruitment tool, but look past that and its a very fun game. I have over 300 hours on this game (playing since like 2003) and i haven't gotten any calls from the army, or a indescribable desire to go enlist.

once you get past the training (yes i agree its annoying), you really see no propaganda in the game at all, besides the fact that your team is always US ARMY and the opposing team is the terrorists, but in a way, i prefer this. That way, your always looking for the same player models (people with ski masks, etc) and people in camo are on your team. 

the main game is no more propaganda then games like battlefield 2 where they feature soldiers in camo running around shooting each other.

now get back on topic.

---

### Post by JonnyM on 2008-12-22
Version 1.53 now released.

Changes,

-Deploy now gives you the option of installing the mAAp pack, This is a collection of new missions created by the 2.5 community. Deploy automatically loads these maps in when you join a server running a maap mission and then unloads them after.
-Added support for 5.1 Surround sound (Linux).
-Fix bug where deploy crashes on minimizeing AA in Windows XP.
-Minor changes to layout of Buddies screen.
-Removed those annoying tool tips, See the readme instead.
-Various Bug Fixes.

Open Deploy and accept the automatic update.

ENJOY!

---

### Post by RookieUbuntuUser58 on 2008-12-23
How do you completely remove this game from Ubuntu? The only thing I see is the file on my desktop for the game and when I click on that it goes to the game screen (choose servers, deploy, settings, and etc).

---

### Post by JonnyM on 2008-12-23
Delete the AA-25Deploy icon from your desktop or where ever and then open a terminal and do:-
> rm -R ~/.25deploy

---

### Post by RookieUbuntuUser58 on 2008-12-23
Thanks that seemed to have worked.

---

### Post by Rotarychainsaw on 2008-12-23
Update from me; seems to be working. Something got fixed along the way. wooo

---

### Post by iheartubuntu on 2008-12-24
> **Polygon said:**
> oh just take off your tinfoil hat. yes, the game is designed as a recruitment tool, but look past that and its a very fun game. I have over 300 hours on this game (playing since like 2003) and i haven't gotten any calls from the army, or a indescribable desire to go enlist.

I think you missed the point the person was trying to originally make. Putting anything from the DoD on your computer isnt smart. Its like giving NSA, CIA, FBI, ATB, etc, etc, etc a front door to your computer. Many people switch to linux for the very reason of security and this game could compromise that.

---

### Post by Vadi on 2008-12-24
Actually, switching to Linux wouldn't me smart (if you go by your paranoia) because SELinux is developed by NSA ;)

[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

---

### Post by dannytatom on 2008-12-24
hahaha, oh gawd.

---

### Post by JonnyM on 2009-01-03
Change Log 1.6

Assist server manager added...
Unique Features,
-For the first time ever, You can run a server on a mac and have it show up in the server list!
-mAAp fully integrated, mAAp pack maps on Assist server manger run in authorised mode with full authorizion and honor correctly displayed. You can change mAAp maps without the server disappearing from the server list and also the server can be hot swapped between Normal, Border/Dusk and mAAp pack modes without needing separate server installation for each. Server can be switched between modes using the in-game F12 menu.
-Server is constantly monitored so if it crashes or freezes it is automatically terminated and restarted.
-Options for HackHunter, PB banlist and Weapon forcing all built in.
-Display of players currently in the server with ability to pull stats and Background check ETC.
-Checks ports are open before stating to avoid any problems.
-Supports MultiHomeing so server only binds one network interface.



Added Ability to change where deploy stores its files and the AA installation by creating a folder next to the AA-25Assist executable simply called '25deploy'...

For example if you want to put deploy on the D: drive (windows) in a folder called AA, You would move AA-25Assist.exe to D:\AA\ and then create the folder D:\AA\25deploy\

If you already have Assist set-up before doing this you will then need to move all the files over from the old deploy folder to the new one!
The Old Assist folder can be found here...
MAC OSX /Users/-USERNAME-/Library/Application Support/25Deploy/
LINUX /home/-USERNAME-/.25Deploy/ (Hidden Folder)
WINDOWS c:\Documents and settings\-USERNAME-\Application Data\25Deploy\
VISTA C:\Users\Username\AppData\Roaming\25deploy\

Enjoy!

---

### Post by ahddm on 2009-01-03
How do I turn Compiz back on?

---

### Post by JonnyM on 2009-01-03
Log-out and then back in again or Restart your computer or goto System > Prefrences > Appearnce...

---

### Post by ahddm on 2009-01-03
Lol I feel dumb now.

I have a suggestion since you're creating this for newer players you could add a tutorial tab for the training when I first started it took me a while to figure out how to unlock next training and etc... I'm sure alot of em would like to access to those tutorials or guideline in your script.

---

### Post by JonnyM on 2009-01-14
Version 1.63 released.

Change Log...

Updates to Hotfix B2 on Mac, To make use of new HSF-SMBS.

HSF-SMBS server list moved onto a faster and more reliable server with master lists obtained from multiple sources so should never go down... Hopefully.

Assist Server Manager now working properly on All Platforms, Including Windows VISTA, Sorry for the buggy release last time.
Added GUID tracking option to Send PB GUID information in the GameSpy query To/From AAOTracker, This provides safer and more accurate tracking.
Server manager tested and fully operational in Regular and mAAp modes on the following platforms:-
Windows 2000 Server
Windows XP Home/Pro
Windows 2003 Server
Windows Vista Home Premium
Linux Ubuntu 8.10
Linux Fedora 10
Linux Cent-OS 4 Server
Mac Tiger
Mac Leopard

Screenshot 2 x 25Assist servers running on Linux Cent OS4 using Tiny Desktop..
[img]http://25abackup.zapto.org/repo/srvlin.png[/img]


Plus lots-o-Bugfixes,
Enjoy!

---

### Post by Black_agent on 2009-01-14
Thanks For The Info!
I'm gonna install it...:KS

---

### Post by iheartubuntu on 2009-01-15
Guys, I downloaded Americas Army Assist but after a few seconds it crashes and dissappears. Anyone else with this prob? I have an nvidia card and not using compiz.

---

### Post by wolfyking2 on 2009-01-16
Looks good.  Downloading right now!:popcorn:

---

### Post by JonnyM on 2009-02-25
Version 1.71 Released.

Many new features and bug fixes but best of all includes the new mAAp pack 5.0, A collection of the best community made missions for America's Army, The New mAAp Pipeline mission included with this pack is based on the upcoming AA3.0 version.

Download only takes a couple of minutes so give it a try.

[IMG]http://img407.imageshack.us/img407/9641/maappackflyer.png[/IMG]

---

### Post by Vadi on 2009-02-25
Include a link to the site ;)

---

### Post by JonnyM on 2009-02-28
.[http://maappack.com](http://maappack.com) mAAp pack project home page.
[http://25assist.com](http://25assist.com) Americas army 2.5 Assist home page.

---

### Post by -jay- on 2009-03-16
call me a idiot but how do i install this ap deploy

---

### Post by iKonaK on 2009-03-16
I don't get it, why in the world would anyone want to install a piece of proprietary software made by any government ?

---

### Post by Vadi on 2009-03-16
> **iKonaK said:**
> I don't get it, why in the world would anyone want to install a piece of proprietary software made by any government ?

Because it's a fun game and not everyone has this high level of paranoia :popcorn:

---

### Post by JonnyM on 2009-10-02
Version 1.8 out now.
Includes the new mAAp pack v6. Introduces lots of new maps and some re-makes of old maps.

---

### Post by ErikEhlert on 2009-10-03
Ive seen AA everywhere now! Internet, TV, more internet...

I guess when I get the time and I am not downloading other stuff to slow my computer to a crawl I will look into it ;D

---

### Post by lowpine on 2009-10-03
thanks JonnyM, I'm new to ubuntu and I got it installed without issue last night :guitar:.  well done.

---

### Post by buttrunks101 on 2009-10-04
hello all very new to ubuntu. just yesterday i was running vista ultimate and was running virtual box just to try ubuntu well seems pretty sweet so i switched.
 on the virtual machine i had installed the americas army 2.5 assist and was able to finish and run the game. However right now i click it the screen pops up to load, but as quick as it comes it vanishes. i dont know what to do for it....:confused:

Fixed my problem. used sudo in terminal to install works great..

---

### Post by oboedad55 on 2009-10-04
> **iKonaK said:**
> I don't get it, why in the world would anyone want to install a piece of proprietary software made by any government ?

I'm with you bro. It looks like an advertisement for state-sponsored terror.

---

### Post by lowpine on 2009-10-04
any idea why my full-screen pops to a small window when playing aa?  this happens even if I turn down the graphics requirements in the game

---

### Post by JonnyM on 2010-09-24
2.5Assist is now back online again, Download at [AA25.org]("http://AA25.org")
Using Assist is the easiest way to get Americas Army working natively on Linux.

---

