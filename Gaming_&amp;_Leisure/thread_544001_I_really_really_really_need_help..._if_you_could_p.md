---
title: "I really really really need help... if you could please..."
date: 2007-09-05
forum: Gaming &amp; Leisure
---

### Post by widjidilii on 2007-09-05
Hi, thank you to all who read this and/or respond with a helpful guide.
Today is my first day running Ubuntu, and to be honest, I'm not sure which I am running: Fiesty/Edgy/Etc.. but what I do know is, I'm glad I made the switch from Windows XP Home to Ubuntu XYZ so-to-speak.  Nonetheless, what I am trying to do is install Windows based games onto my Ubuntu laptop.  For example(s)...
a) World of Warcraft
b) America's Army
c) Diablo II + Lord of Destruction
The problem is, I do not know how to install this 'Wine' software to run the games.  I honestly have looked all around for guides, even YouTube,  but all of the guides are outdated for the newest 'Wine' update.  Plus, I am 'noob' if you will...So, out of sheer frustration, I created this forum account name so I could muster up some help from all you experienced  'Wine' users, and/or gamers.  Thanks so much for your cooperation and help... even if I don't get any--I appreciate you reading my thread.

---

### Post by quadomatic on 2007-09-05
Installing WINE:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Installing games:

[http://appdb.winehq.com](http://appdb.winehq.com)

Search for the game you're looking to install. Here are links for the games you mentioned.

[http://appdb.winehq.org/appview.php?iVersionId=8903](http://appdb.winehq.org/appview.php?iVersionId=8903) - WoW
[http://appdb.winehq.org/appview.php?iVersionId=6547](http://appdb.winehq.org/appview.php?iVersionId=6547) - America's Army (I thought there was a linux version...)
[http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49) - Diablo II
[http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315) - Diablo II Lord of Destruction

Read this thread too, it helps a lot:

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

Reading the WINE documentation will probably help too:

[http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index)

Good Luck, and welcome to the world of Ubuntu!

BTW: If you want to know what version of Ubuntu you're running, on the menu bar on your screen, go to System>About Ubuntu

If you downloaded Ubuntu from Ubuntu.com, you're probably running 7.04 Feisty Fawn, which is the newest version

---

### Post by widjidilii on 2007-09-05
Thank you for your initial help, and quick response! However, what I still am unsure about is the howto of installing wine.  The thing is, I've don't understand the 'terminal' codes and everything and I just get lost easily.  I do, and have, copy/pasted the fiesty (which I found out I am running, thanks to you) codes into my terminal and hit ENTER, but it immediately follows with a 'Password:' text...

I do appreciate all of your help. 
If you can guide me on the Wine setup I would be so grateful. 

-Widjidilii

---

### Post by anjilslaire on 2007-09-05
When you are prompted for "password", put in your system account password and press ENTER. Its a security feature to prompt for your permission whenever you're making system changes (like installing software).

---

### Post by quadomatic on 2007-09-05
Ah, so you're not familiar with the terminal yet. Don't worry, you'll get used to it in time. Hopefully these pages will help:

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)
[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by widjidilii on 2007-09-05
Thank you to both of you (again.) I appreciate it.  I'll take a look into what both of you said. 

-Widjidilii

---

### Post by widjidilii on 2007-09-05
How do I name the path of my WoW files directory?

I have a folder on my desktop called: WoWFiles having the copied files from the CD. But when I have to continue further in the installation process and add to the terminal code I have to insert these two codes:

cd /<path-to-directory>/
wine Installer.exe

But replace <path-to-directory>/ with the actual path.  How would I do that?

---

### Post by hikaricore on 2007-09-05
> cd ~/Desktop/WoWFiles
wine Installler.exe

When logged in to an account under Linux, **~** will always represtent your home directory which is at: /home/username (username obviously being your username)

The Desktop folder lives here along with any configuration files.
Most configuration files are hidden from normal file browser view with their name prefixed with a **.** for example **.wine** is where WINE stores it's configuration and data files.

Upon installation your WoW files will be located at: **~/.wine/drive_c/Program\ Files/World\ of\ Warcraft** (aka *"~/.wine/drive_c/Program Files/World of Warcraft"*)

The \ trailing slashes are used to tell the CLI (terminal) interface that you are using a special character in this case a **space**, otherwise it will assume that the next word is the next part of the command.
To avoid this obviously use trailing slashes prefixing a **space** or just put the entire directory in quotes.

> cd "~/.wine/drive_c/Program Files/World of Warcraft"

is the same as

> cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft

Thought it might help to know where your files will be going in case you need to know where to put any mods.  ^_^

---

