---
title: "Ubuntu games on Xubuntu"
date: 2006-09-22
forum: Desktop Environments
---

### Post by heydabop on 2006-09-22
Is it possible to put the Ubuntu GNOME games on Xubuntu?:confused:

---

### Post by Cable on 2006-09-22
Yep, it will work just fine.

---

### Post by heydabop on 2006-09-22
How do you get the games on Xubuntu? Do you just take files from the Ubuntu disk?

---

### Post by heydabop on 2006-09-22
I moved the game files onto Xubuntu, but I couldn't run them. What do I do?

---

### Post by songo on 2006-09-22
sudo apt-get install gnome-games

---

### Post by heydabop on 2006-09-22
Is that a command for the terminal?

---

### Post by darkhatter on 2006-09-22
I only used the old xfce, but open up the package manager on xfce, and type in gnome games, and kde games then install the games you want, I just hope they'll show up in the menu.

---

### Post by heydabop on 2006-09-22
I typed "sudo apt-get install gnome-games" and got an error saying package has no installer. Also, what is the package manager, and hwere can I find/run it?

---

### Post by heydabop on 2006-09-22
Does the new xfce even have a package manager?

---

### Post by acefreely on 2006-09-22
> **heydabop said:**
> Does the new xfce even have a package manager?

Yes it does, synaptic just like the gnome and kde versions.  

The xubuntu is quite nice to be perfectly honest.  I have been using Red Hat since 1998 as my primary machine.  I have tinkered around with other distros over the years but never made the total switch until I had a look at xubuntu 64 bit.  I dig the lightweight window mangers, Fluxbox used to be my favorite, and xfce is very impressive.

---

### Post by heydabop on 2006-09-22
What's synaptic? Sorry if I sound like a newb, but that's what I am to (X)Ubuntu.

---

### Post by heydabop on 2006-09-22
I can't find synaptic.

---

### Post by heydabop on 2006-09-23
Ok, I found Synaptic, but I can't find the games.

---

### Post by songo on 2006-09-23
> **heydabop said:**
> I typed "sudo apt-get install gnome-games" and got an error saying package has no installer.
try on the terminal "sudo apt-get update" first and then "sudo apt-get install gnome-games".

---

### Post by heydabop on 2006-09-23
Thanks for the help, the only problem is, I don't have internet on my computer yet, but when I do I'll do what you said.

---

### Post by heydabop on 2006-09-24
I've just learned that I will not be getting internet on my computer. Is there a way I can take the updates from a computer with internet to my computer without it? I already know how to take files from one to another. Or can I just take the files off the Ubuntu CD?

---

### Post by pelle.k on 2006-09-24
You know, using a slimmed down installation like the one xubuntu provides is not really ideal if you are without internet, because that's where all the good stuff are...
You can however add a cd in synaptic, and i suppose the ubuntu (not xubuntu) cd has the games in it.

Also i would recommend downloading the DVD version of ubuntu, because it contains so much more than a bare installation.

You are also going to have problems updating codecs that will let you play mp3:s and some .avi movies and such. If so, this is the best solution i can give you;
[http://packages.ubuntu.com/dapper/libs/libxine-extracodecs]("http://packages.ubuntu.com/dapper/libs/libxine-extracodecs")
The page let you download that package, and it also lists four (4) dependencies. i _think_ that is all you need. install them by right clicking them and choose "gdebi".

I understand this is a lot to take in, but if you follow these steps carefully you will have something to start with anyway.

---

### Post by heydabop on 2006-09-24
Thanks, I know slimmed Xubuntu wasn't the best choice, but it was the only choice for my computer. My computer stinks. Although, I never thought of the alternate install for Ubuntu...... still probably wouldn't work on my computer.

---

### Post by DJ Wings on 2006-09-24
Xubuntu is perfectly OK for gaming machines or machines with older hardware. Add the CD to Synaptic by going to Settings > Repositories, and clicking "New". For URI, type "cdrom: Ubuntu*" (NO QUOTES, regex might not work. Correct me...). Then, click Refresh, and mark gnome-games (click OK). Click "Apply". That's how you install packages in Synaptic ("mark gnome-games", etc).

---

### Post by heydabop on 2006-09-24
I went to repositories and there is no "new". Also, I've tried adding a CD to synaptic, but I still couldn't find a package titled gnome-games.

---

### Post by heydabop on 2006-09-24
I've found out that you can add downloaded packages to synaptic, so I'm downloading the gnome-games package right now and when it's done I'll see if it works.

---

### Post by pelle.k on 2006-09-24
Did it ask for the cd or maybe "process it for a while"? (I suppose of course that you did "update" synaptic...)
If it still didn't work. Do this
```
cat /etc/apt/sources.list
``` in a terminal, paste it in this thread, and i will see if you added the cd correctly :)

---

### Post by heydabop on 2006-09-24
Ok, I'll do that, after I try to install this .deb file that should be for the games.

---

### Post by heydabop on 2006-09-25
It said ```
#
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted


deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by heydabop on 2006-09-25
One of the packages needed for gnome-games has a depenability problem with libc6 but I already have libc6 installed.

---

### Post by pelle.k on 2006-09-25
well, looks fine to me. put you ubuntu cd in the drive and search for games in synaptic. Doesn't that work? What happened when you tried to install gnome-games?

---

### Post by heydabop on 2006-09-25
It doesn't work, and gnome-games has way to many dependencies.

---

### Post by heydabop on 2006-09-26
So what should I do, I tihnk I could install it if I got all the packages it needed (which would take a heck of a long time). Except for that libc6 problem....

---

### Post by pelle.k on 2006-09-26
I dont get it, your cd is is sources.list, and you say you have "updated" synaptic. If so, gdebi package installer should resolve those dependencies from your "ubuntu" cd. You really shouldn't have to download them. (or manually install them either...)
I only told you to download a few things (libxine-extracodecs) because those werent on the cd.
The dependencies for gnome-games _is_ located on the cd. So if you want, you can install them manually from there, but in practise you shouldn't have to...

---

### Post by heydabop on 2006-09-26
Oh. This is tougher than it should be. Although I think I just got an idea.

---

### Post by heydabop on 2006-09-26
I tried to add a .deb file to synaptic, but it didn't work.

---

