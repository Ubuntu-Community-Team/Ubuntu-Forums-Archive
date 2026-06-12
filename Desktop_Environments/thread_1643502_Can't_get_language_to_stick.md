---
title: "Can't get language to stick"
date: 2010-12-12
forum: Desktop Environments
---

### Post by davidgroos on 2010-12-12
I'm using Maverick at my house.  While our system is based in English, we need Spanish quite often.  Well, Right now, I've got some issues on it:
1.  Some of my menu items are in English, others in Spanish.  
2.  In my home directory I've got a folder called "Desktop" (with a folder icon) and another called "Escritorio"--desktop in Spanish (and it uses the desktop icon).  
3.  When I log in none of the content in my Desktop directory is visible on the desktop.
I'm pretty sure the problems are related to my locale issue.

When I type locale the output is:
~$ locale
LANG=en_US.utf8
[COLOR="Red"]LANGUAGE=en_US:es_GT:en[/COLOR]
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

I"ve tried to change the language by editing /etc/default/locale and /etc/environment to use LANGUAGE="en_US:en".  I then entered the command export LANGUAGE=en_US:en and upon typing the command 'locale', it would show LANGUAGE=en_US:en, however upon restart it would be back to the original LANGUAGE=en_US:es_GT:en and the above mentioned problems.

Please help before I ruin my computer in my effort to fix it :)

---

### Post by davidgroos on 2010-12-12
While there are several problems, the main one I'm concerned with is getting the locale to update correctly.

I should also have mentioned, I've used both System--> Administration--> Language Support and 
:~$ sudo dpkg-reconfigure locales
:~$ sudo locale-gen en_US.UTF-8
:~$ sudo update-locale LANG=en_US.UTF-8

Help?

---

### Post by davidgroos on 2010-12-13
Solved this between google, posters of other threads, and I...

In addition to doing the things above, you have to do 2 more things...

THING 1
You have to edit your .profile config file in your home directory:
```
gedit ~/.profile
```
Where I saw that each time I logged in, this command was being run: "export LANGUAGE="en_US:es_GT:en"" so that was a problem!  I changed that line to: "export LANGUAGE="en_US:en"" (without the outermost quotes) and saved it. 

THING 2
You have to edit your ./config/user-dirs.dirs config file:
```
gedit ~/.config/user-dirs.dirs
```
so that it has the proper names for your files--this config file tells what the different home directories should be called. I had some lines that read something like:   The configuration part of the file on page looks like this: XDG_DESKTOP_DIR="$HOME/Escritorio" so that was wrong!  Upon changing them to their English versions it said:
> XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

So, upon a restart (probably could have just logged in/out) everything worked!  All menus and sub-menus are in English again! (ANd didn't ruin computer!)

---

### Post by Krytarik on 2010-12-13
Well done davidgroos! And thanks for posting your solution back here!!

I read your post yesterday, and I had not any clue about it, not at least because I not wanted to screw my system up by trying to install an additional language.;)

---

### Post by Zilvador on 2011-02-09
Thank you indeed. This was just what I needed, it seems :).

---

### Post by owiknowi on 2011-03-12
thanks very much and muchos gracias!
had the same troubles here and you've solved it.

---

