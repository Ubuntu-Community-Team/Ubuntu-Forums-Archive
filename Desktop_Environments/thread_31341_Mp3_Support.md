---
title: "Mp3 Support"
date: 2005-05-02
forum: Desktop Environments
---

### Post by shanghaipi on 2005-05-02
I cannot play mp3 files at all on KubuntuI went to the Kubuntu faq and reinstalled and installed akode over and over.  I have no idea what the heck killall is supposed to revert the settings.  I'm really new to linux and am getting used to apt-get and all those command functions.  If someone can help me, could you please be specific.  That faq wasn't very specific and I want to listen to my mp3s.  

Better yet, does anyone know of a good program where I could change all my mp3s into ogg?  I've been wanting to do that for a while, but wanted to rip all my cds again so i could get good quality.  I don't think I'm going to rip all my cds anytime soon, so can someone please help me?  Any help would be much appreciated.  Thank  You.

New Linux User

---

### Post by shanghaipi on 2005-05-03
Can anyone answer my question, or is it too stupid.  I have been searching the forums and the internet for this answer and nothing...please somebody help me!!!!!!!!!

---

### Post by andypowell on 2005-05-04
Patience. 
(Im considering migrating to the Kubuntu, love Ubuntu at the minute, so iam trawling posts to predict any problems i may have ;  found your frustations so thought i'd chirp in with some help hopefully!)

Just glanced at your post but you need to drop in some more specifics. 
Have you any sound at all? I had a problem for ages with KDE and Suse9.1 cause my sound was onboard and the kde upgrade killed it. 
If you do have sound can you play .ogg? your post implies this a wee bit as you ask for conversion. If you can play .ogg then try a different player. 
If you are having diffs with apt-get just use the synaptic installer (or whatever its called) does it all for you!!! :-) OOops just reread the post is there a synaptic installer in Kde there is in Gnome you see? If not is there a YAST installer even easier!!

Have fun, dont give up yet!

---

### Post by dave9191 on 2005-05-04
Im running kubunutu now and I think that it played mp3's from the day I installed it. 

First of all you want to enable extra repositories (ubuntuguide.org) will tell you how. Then you want to 

sudo apt-get install kpackage

a very nice package manger (like synaptic). It lets you graphically browse the repositories and install files that way. Or you can just use Kynaptic that in your menu already to do that. But Im not too keen on that program. 

Ubuntuguide.org also tells you how to get mp3s working on ubuntu. Or you can install xmms, that should come with mp3 support. 

Dave

---

### Post by Takis on 2005-05-04
[QUOTE=shanghaipi]I cannot play mp3 files at all on KubuntuI went to the Kubuntu faq and reinstalled and installed akode over and over.[/QUOTE]

Are you an ex-Windows/Winamp user? XMMS is a real good one for this, nice and easy, although you have to manually install .wma support if you need it.

---

### Post by shanghaipi on 2005-05-04
I tried to install Kpackage and this is what I got.

tj@kubuntu:~$ sudo apt-get install kpackage
Password:
Reading package lists... Done
Building dependency tree... Done
Package kpackage is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kpackage has no installation candidate

Anyhoo, I was kind of a winamp user, but recently changed to Musikcube because I liked the one screen interface.  It is still young, but it was beginning to become a cool app. 

As of now, I'm sort of using Amarok.  But can't play any of my music because they are all mp3s.  I can load them and all, but when I click on them, amarok seems to just hang on the command.  I tried uninstalling and reinstalling amarok via synaptic.  

I just downloaded an OGG sample file and worked fine on amarok.  Still stumped about why it won't play mp3s.

What would be another good music app where i can get quality sound and good configuration?

---

### Post by dave9191 on 2005-05-04
Thats exacly the output you would expect to get if you didnt do the first thing i said. You need to enable the extra repositories. If you dont, then it wont know where to get it from. 

And you need to install the mp3 codecs that arent bundeled with ubuntu because of legal reasons. They are not free software.

---

### Post by jesseman on 2005-05-04
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by shanghaipi on 2005-05-04
Okay, I tried following that link to the ubuntu guide for the extra repositories.  Since I'm using KDE, the gedit command didn't work.  So I tried Kate, that didn't work either.  I tried searching online, but no avail.  Please bear with me, because I'm super new at this.  I downloaded "guifications" for Gaim (used it on my windows xp), but can't get the damn 'write protection' off.  Slow going over here.

As for Mp3s, I went on synaptic and found out that KDE already had 'akode' installed.  I read somewhere that that's where you can get support for mp3s.  Sorry about all this, but I'm seriously trying to hard to fix this because I like KDE and Linux and want to learn how to use it.

---

### Post by wwwolf on 2005-05-04
For the MP3 codecs, check out the post I made to myself

[http://ubuntuforums.org/showthread.php?t=31577](http://ubuntuforums.org/showthread.php?t=31577)

Audacity is really great for editing, listening and converting to OGG. If you enable the commented out repositories in /etc/apt/sources.list

then run:

sudo apt-get update

You can then select audacity from kynaptic and tell it to install. It will put it in your multimedia menu.

HTH,

wwwolf

---

### Post by wwwolf on 2005-05-04
[QUOTE=shanghaipi]Okay, I tried following that link to the ubuntu guide for the extra repositories.  Since I'm using KDE, the gedit command didn't work.  So I tried Kate, that didn't work either. [/QUOTE]

sudo nano

if nano isn't installed then run your package manager or probably

sudo apt-get install nano

when you run nano as root you can overwrite files with root access.

I know, I like kate too, but I once tried to run kate as root in the console and I broke it.

HTH,

wwwolf

---

### Post by crane on 2005-05-04
[QUOTE=shanghaipi]Okay, I tried following that link to the ubuntu guide for the extra repositories.  Since I'm using KDE, the gedit command didn't work.  So I tried Kate, that didn't work either. [/QUOTE]

I'm not real familiar with kde but did you try replacing gedit with kwrite? I believe that is another editor you can use if your wanting a gui based editor.
You could also use vi for command line editing.

---

### Post by dave9191 on 2005-05-05
Gedit is gnomes text editor. And kate is funny about being run as root. 

apt-get intsall kwrite and use the in place of gedit for a nice gui editor. Using nano is cool, but it can be annoying at first. Ctrl+x closes it and asks you if you want to save changes. There are other commands at the bottom of the screen when you open nano.

---

### Post by subhankar on 2005-05-05
Going back to the original problem: Mp3!!

Well, I don't think converting mp3s directly to ogg is a good idea as it's not that popular. Have a look at the following thread which discusses this issue in quite detail:

[http://www.linuxquestions.org/questions/showthread.php?threadid=29354](http://www.linuxquestions.org/questions/showthread.php?threadid=29354)

Now, there is a tool called mp32ogg for this, which you can find here :

[http://freshmeat.net/projects/mp32ogg/](http://freshmeat.net/projects/mp32ogg/)

As you said, your sounds okay but you can't play mp3s! Well, this shouldn't happen with a default Kubuntu install as mp3s do play by default!! Did you do an upgrade? That might break things, but I'm not sure. Mine was a cd-install. If possible, you might try re-installing Kubuntu. Also, do a "sudo apt-get install akode" to make sure that the latest version is properly installed.

Hope that helps :-)

Regards,
Subhankar

---

### Post by shanghaipi on 2005-05-05
Thank you all for your help, I just got home from school and configured the extra repositories successfully with nano.  Thanks for the 'ctrl-w' tip otherwise I would have pulled my hair out trying to figure out how to save it.  

I downloaded Audacity and it seems to play mp3s alright, but amarok is now crashing when I play mp3s no matter which engine I use.

I'll try and work things out when I get back from work.

---

