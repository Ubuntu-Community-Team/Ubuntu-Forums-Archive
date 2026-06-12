---
title: "HOWTO: Install OpenTTD"
date: 2006-05-12
forum: Gaming &amp; Leisure
---

### Post by tdehoog on 2006-05-12
[IMG]http://www.openttd.org/images/top.gif[/IMG]

I'm not a native english speaker, so don't blame me on my english

Since there isn't a nice howto for the installation of this game yet I thought I'd create my own and share it with you 

In this howto I'm going to (try to) explain how you can install OpenTTD on your Ubuntu(/Kubuntu/Xubuntu/Edubuntu/Some other Ubuntu fork) Dapper box. It's pretty simple, but it needs some work with the command-line. So if you have an extreme fobia for the commandline, get the hell out of here and install Windows on your pc, or buy a mac or something.

1.What is OpenTTD

(if you know Transport Tycoon or Locomotion skip this part.)

OpenTTD is an opensource version of the popular Transport Tycoon Deluxe game by Chris Sawyer. You have the task to create a transport imperium with which you have to make as much profit as possible. There are four types of transport: Road, Rail, Air and Water. Each of these have their cons and pro's. You need to set up transport networks between sources and destinations like coal and powerplants, livestock/grain/steel and factories, iron ore and steel factories, wood and sawmills, passengers/mail and cities, etc, etc... There are a dozen of things to look after, like the capacities of the vehicles, the demand and the offer of various sources and destinations, the age of your vehicles, the financial figures, and competing companies. There is also a very good multiplayer part with built-in server browser. Guaranteed fun at lans :)

Enough info about the game, if you need more info, visit the official site:

[www.openttd.org]("www.openttd.org") (especially the wiki's)

2.Installation

First, download the *.deb package from the official site. (this is the latest version: [click]("http://prdownloads.sourceforge.net/openttd/openttd_0.4.7-1_i386.deb?download")) and the windows files: [click]("http://forums.7wolf.net/ttd/files/game/ttd-win.zip"). Don't let the word 'Windows' scare you off. We need some files from the original Transport Tycoon Deluxe.

Second, install the *.deb package. This is very simple. Just doubleclick the file to let the debian installer in Ubuntu do it's work.

Third, this one's bit tricky (at least, for n00bs like me...:) ). We need to copy some files from the ' ttd-win.zip'  file to the installation folder and change the file permissions. I'm going to do most of this with the command-line, so you just need to copy/paste the lines.

1.Extract 'ttd-win.zip' to a folder you can easily find with the command line. (I extracted it to my 'Desktop' folder.) You can remove it later.

2.Open the terminal and cd to the folder you just extraced 'ttd-win.zip' to. It should be names 'ttd-win'. Open this folder ('ls').

3.Now, you should see 5 files with '*.grf' as its extension. As already might guess, these files contain the original grapics of the game. These files need to beed copied to the 'data' folder of the OpenTTD installation as well as the 'sample.cat' file. I did it like this:
		
```
sudo cp *.grf sample.cat /usr/share/games/openttd/data
```

(if your target folder is different, don't forget to change the command.)

	This command copies all the required files to the openttd/data folder.

4.Now whe need to set the proper file permissions to the files whe just copied. Since we're not going to play the game in root (the user that copied the files) all the time. Use these commands:

```
cd /usr/share/games/openttd/data
```
```
sudo chmod 777 *.grf sample.cat
```

5.If you still got the terminal open type in this command:

```
openttd
```

And voilá, there you go. One finishing touch (optional):

Create a menu entry with Alacarte in the game menu and/or a shortcut on the desktop/whereever you want it. Use this command: 'openttd'. The icon for openttd is in the standard icon folder (this was done by the *.deb installer). 

Have fun!

---

### Post by Perfect Storm on 2006-05-12
Wouldn't it be easier with 
```

sudo cp *.grf sample.cat /usr/share/games/openttd/data

```

?

---

### Post by tdehoog on 2006-05-12
[QUOTE=Artificial Intelligence]Wouldn't it be easier with 
```

sudo cp *.grf sample.cat /usr/share/games/openttd/data

```

?[/QUOTE]

Ok, I changed it. 

These are little tricks a n00b like me still has to learn

Thanks :)

---

### Post by Sammi on 2006-05-31
Thx for the howto. Helped me to set up and get started in no time :-D

---

### Post by holr on 2006-05-31
Just wondering, were you able to get both sound and music in the game? Ive had troubles with suse but fedora (my current distro) works with both. I know theres sometimes issues with the midi music...

---

### Post by frying_fish on 2006-06-01
If you are after midi output would using timidity not be a good idea, and run it with the option of timidity -iA -Os  for ALSA input and Stereo Output. (haven't run open TTD, so don't know if it would help but maybe it would...)

---

### Post by tdehoog on 2006-06-28
[QUOTE=holr]Just wondering, were you able to get both sound and music in the game? Ive had troubles with suse but fedora (my current distro) works with both. I know theres sometimes issues with the midi music...[/QUOTE]

I haven't fugured the music out yet. But I know these files are in the ttd-win.zip file, since the windows installer from openttd also copies these. 

I'm going to compare a window installation with a linux one, to figure which files are required. 

After this I'll update the howto.

The sound-effects worked out of the box in my case.

---

### Post by joelchr on 2006-08-21
> **tdehoog said:**
> I haven't fugured the music out yet. But I know these files are in the ttd-win.zip file, since the windows installer from openttd also copies these. 

I'm going to compare a window installation with a linux one, to figure which files are required. 

After this I'll update the howto.

The sound-effects worked out of the box in my case.

The sound is in the gm-folder and must be copied into /usr/share/games/openttd/gm. But I have no idea how to get the music working...

---

### Post by NiceGuy on 2006-09-05
I might have just got lucky but here is what I did to get the sound and music working.

First I just copied the file **sample.cat** from the **/data** directory on my windows copy of ttd to **/usr/share/games/openttd/data** - this got the sound working.


and then all the files from the **/gm** directory on my windows copy to **/usr/share/games/openttd/gm**. Then I installed (from synaptic) **timidity**.

When I next started the game the music worked...


...well actually... thinking about it I did need to start a new game and go to the jukebox and click the **play** button. :D

lol - I bet you'll be kicking your selves if thats what the problem is!

Hope that helps.

---

### Post by ShirishAg75 on 2006-09-06
first of all there is a newer 0.4.8 which is a bug-fix. I was not able to install it the first time around but was able to install 0.4.7 & then install 0.4.8 which sat on top of it. Secondly timidity took another 30 MB to make the sound files work hence it would have be better if these guys use .ogg at some point so memory used would be less. The wiki gives some more info. when we can expect the changes. Looks like another couple of years down the line. [http://wiki.openttd.org/index.php/Roadmap](http://wiki.openttd.org/index.php/Roadmap) . The new graphics do seem cool [http://wiki.openttd.org/index.php/City_Buildings_%28New_Graphics%29](http://wiki.openttd.org/index.php/City_Buildings_%28New_Graphics%29) although its supposed to take sometime to make it workable.  I didn't have to do any magic to hear the sounds as I did copied the .gm files & then used timidity. :)

Edit :- Looking forward to 0.5 as & when it's released. The UI needs lots of improvement.

---

### Post by Iesos on 2006-10-05
I'm trying to get OpenTTD up-and-running. But it seems to fail.
I have followed this howto (sort of... I did the same thing) But I get the error message:

```

$ openttd
openttd: gfxinit.c:88: LoadGrfIndexed: Assertion `b' failed.
Aborted

```

Anyone got any idea how to fix this?

---

### Post by Perfect Storm on 2006-10-05
by any chance you have compiz and XGL installed/in use?

---

### Post by Iesos on 2006-10-05
Installed, but not in use.

But! I've got amd64 Dapper, so first I tried to install it with --force-architecture, but then I got the message in my last post.
So I thought: Hey why not try chroot. So I installed it under my 32bit-chroot, where I don't have XGL installed, but I get the same message.

---

### Post by Iesos on 2006-10-05
oh, it works now. I just reinstalled it under my chroot.

---

### Post by phocis850 on 2007-08-22
bump for an awesome game

---

### Post by dink1000 on 2007-10-18
i'm trying to copy the files to the directory but i keep getting this in terminal

*****@*****-desktop:~$ sudo cp *.grf sample.cat /usr/share/games/openttd/data
Password:
cp: cannot stat `*.grf': No such file or directory
cp: cannot stat `sample.cat': No such file or directory

the 6 files are on the desktop but it just doesn't seem to be able to see them:confused:

---

### Post by chez17 on 2007-11-15
Just installed on Gutsy, sound effects work fine but music doesn't. I used 0.5.3 and the game itself works perfectly. Nice howto.

---

### Post by BDNiner on 2007-11-15
openttd is in the repos and in add remove. 

dink1000 I created a folder on my desktop and then copied the files from there. but the music still doesn't work. 

other than the music the game works flawlessly, even with compiz fusion enabled

---

### Post by lock-aze on 2007-11-17
Just needed to say, I had the game open, didn't get the sound to work, but then I installed (from synaptic) timidity (as said before) this made the sound work instantly.. :)

---

### Post by Mazza558 on 2007-12-15
Doesn't work at all... I get this:

> openttd
Error: Cannot open file '/usr/share/games/openttd/data/sample.cat'
openttd: openttd.c:88: error: Assertion `0' failed.
Aborted (core dumped)


I've tried 2 different SAMPLE.CATs and 2 different versions of OpenTTD (0.47 and 0.52). Help?

---

### Post by Mazza558 on 2007-12-20
Anyone know a solution?

---

### Post by Beren Camlost on 2007-12-21
I used the windows files from this download and had no problems: [http://nl.dl.owenrudge.net/TT/game/ttd-win.zip](http://nl.dl.owenrudge.net/TT/game/ttd-win.zip)

Edit: By the way, did you follow the Howto in original post and changed permissions for your files?

---

### Post by viktro on 2008-01-28
> I've tried 2 different SAMPLE.CATs and 2 different versions of OpenTTD (0.47 and 0.52). Help?

Yes, SAMPLE.CAT is not sample.cat. Rename it.

---

### Post by Perfect Storm on 2008-01-29
There's a guide on how to install OpenTTD at the full Circle Magazine in issue 9 page 20 - [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Mazza558 on 2008-02-19
Finally got this working. What you have to do is RENAME ALL THE ORIGINAL GAME FILES TO LOWER-CASE.

---

### Post by Tenesis on 2008-09-20
The only thing that I was not able to do was to download the original files from the link you gave us. Also I have a 64bits version so I've had to install the 64bits one. The homepage of the game already had selected the correct version for me.

I've downloaded an old DOS version of TTD from [abandonia ]("http://www.abandonia.com/en/games/44/Transport+Tycoon.html"). Then I've just copy the commands from the original post and everything worked fine.

Thanks for the post :KS

---

### Post by TheCowboy on 2009-01-09
haha my girlfriend is gonna go mad if i install Openttd.

she thought the game was gone, the minute i switched to ubuntu. 

i think i'll try tonight:D ;)

---

### Post by meborc on 2009-01-09
> **TheCowboy said:**
> haha my girlfriend is gonna go mad if i install Openttd.

she thought the game was gone, the minute i switched to ubuntu. 

i think i'll try tonight:D ;)

yeah, i have spent way too many hours with that game too :) 

but it gets depressing when you start a new game and you see all that land unused... ;) 

my strategy - airplanes

---

### Post by TheCowboy on 2009-01-09
> **meborc said:**
> yeah, i have spent way too many hours with that game too :) 

but it gets depressing when you start a new game and you see all that land unused... ;) 

my strategy - airplanes


Correct strategy. Good to see the citys get in shape... haha.

---

### Post by inuit-joe on 2009-03-22
Do you  need the CD of it?

---

### Post by Perfect Storm on 2009-03-22
> **inuit-joe said:**
> Do you  need the CD of it?

You need the original game data.

---

### Post by widzhit on 2009-05-20
Thanks a bunch for this tutorial!

---

### Post by biodiesel-bri on 2009-11-27
Anyone else having problems with OpenTTD in Karmic 9.10 64 bit?  It was working fine for me in Jaunty 64 and I just did a clean install - no sound with OpenTTD.  Other SDL games give me sound.

Any ideas?

---

### Post by biodiesel-bri on 2009-12-04
Never mind, it was a problem with pulseaudio that I fixed.

---

### Post by Sealbhach on 2009-12-07
I've been playing this game for hours on end during the past week. It is so absorbing, I can just sit watching my trains for hours on end. It's having my own little train set.

I've just added the [Swedish Houses GRF]("http://www.tt-forums.net/viewtopic.php?f=26&t=44360"). They look so cute!

Any other good GRFs that people think are a must have? I have the World Airlines set which is cool.

.

---

### Post by thematrixuum on 2010-02-25
I'm having problem installing this game.. i have done all what u said in the 1st thread. but when i tried to run the game, the terminal gave me this error : Error: Failed to find a graphics set. Please acquire a graphics set for OpenTTD. See section 4.1 of readme.txt.

But I already copied the windows files at the /usr/share/games/openttd/data/ folder.. can anybody help me?

---

### Post by kiwited on 2010-03-26
> **thematrixuum said:**
> I'm having problem installing this game.. i have done all what u said in the 1st thread. but when i tried to run the game, the terminal gave me this error : Error: Failed to find a graphics set. Please acquire a graphics set for OpenTTD. See section 4.1 of readme.txt.

But I already copied the windows files at the /usr/share/games/openttd/data/ folder.. can anybody help me?


Did you change the permissions?

Just installed v1.00 on Lucid - fantastic!!

Theo

---

### Post by AlexanderDGreat on 2010-03-27
How do you get the music to work for Karmic or Lucid? Game works fine only with sound effects. Pls. help. Tis is amazing game!

---

### Post by willwesmck on 2010-07-06
> **AlexanderDGreat said:**
> How do you get the music to work for Karmic or Lucid? Game works fine only with sound effects. Pls. help. Tis is amazing game!
I'm assuming your only option in Base Music Set is NoMusic. Two ways to get OpenMSX.  
1.  Download from [/[COLOR="Blue"]bananas[/COLOR]]("http://us.binaries.openttd.org/binaries/bananas/index.html") and extract the zip to ~/.openttd/gm
or 2. From check online content and search for OpenMSX.  
Cheers.

---

### Post by ICrapBombs on 2011-12-05
On that russian website for the windows COunter parts Its in RUSSIAN, I AM NOT RUSSIAN, so i cant read it soooo. DIrect mediafire link? 

Sorry for the crumy pucuation and grammar/ spelling its just me typing lazly

---

