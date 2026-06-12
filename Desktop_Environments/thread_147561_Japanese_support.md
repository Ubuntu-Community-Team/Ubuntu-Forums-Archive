---
title: "Japanese support"
date: 2006-03-14
forum: Desktop Environments
---

### Post by dpaint4 on 2006-03-14
Okay, you guys are going to know the answer to this, so I'm asking YOUUUUU! I could possibly find the answer in this thread but seeing as how it's 167 pages long and the search points me to the first page of it, I've given up reading the whole thing.

Here's the deal. I need support for Japanese file names in my OS. I have downloaded and installed the international packages from Synaptic, and I've added the options to my input methods. So far I can't figure out how to make Anthy do anything at all. I don't even know where it is.

And mostly I have some zip files, and when I decompress them with Archive Manager, it does not handle the UTF file names at all. Just markes them as incorrectly encoded.  Only they're not. It's just that the names of the files are not Western.

I know Ubunutu is somewhat popular in Japan and that there's a Japanese distribution of it, so I'd think that Japanese input and file names would be easier to add to the English distro than it has currently turned out to be.

Please give me any advice you've got.

Thanks.

---

### Post by ubuntu27 on 2006-03-20
[QUOTE=dpaint4]Okay, you guys are going to know the answer to this, so I'm asking YOUUUUU! I could possibly find the answer in this thread but seeing as how it's 167 pages long and the search points me to the first page of it, I've given up reading the whole thing.

Here's the deal. I need support for Japanese file names in my OS. I have downloaded and installed the international packages from Synaptic, and I've added the options to my input methods. So far I can't figure out how to make Anthy do anything at all. I don't even know where it is.

And mostly I have some zip files, and when I decompress them with Archive Manager, it does not handle the UTF file names at all. Just markes them as incorrectly encoded.  Only they're not. It's just that the names of the files are not Western.

I know Ubunutu is somewhat popular in Japan and that there's a Japanese distribution of it, so I'd think that Japanese input and file names would be easier to add to the English distro than it has currently turned out to be.

Please give me any advice you've got.

Thanks.[/QUOTE]

I don't know about how to solve our problem [I'm also having the same problem] but, we have a HOPE.

Dapper will have a better Asian character support :)

Mark Shuttleworth, the Ubuntu's Founder said, quote:

After the Asia business tour I realised that we need to improve our
support for Chinese, Japanese, Korean and other Asian fonts,
translations, input methods and supporting tools. We are pulling
together a crack team to work on that next week, and I would like to
land their changes in Dapper. These countries are growing their adoption
of technology at a very high speed and it would be great to offer them a
compelling alternative to the traditional route of proprietary software."

Source:
[https://lists.ubuntu.com/archives/ubuntu-art/2006-March/000734.html](https://lists.ubuntu.com/archives/ubuntu-art/2006-March/000734.html)


So, wait for Dapper Drake!! ;) 

ark Shuttleworth proposes six-week delay for Dapper release in order to improve Ubuntu Dapper Drake:

[http://ubuntuforums.org/showthread.php?t=142536](http://ubuntuforums.org/showthread.php?t=142536)

---

### Post by fonggiding on 2006-04-15
The answer is supper simple if you don't mind installing ubuntu-jp.  I am on it now. As long as you have no reservations with re-installing I think that it is the easiest way to do it.

---

### Post by ubuntu27 on 2006-04-18
[QUOTE=fonggiding]The answer is supper simple if you don't mind installing ubuntu-jp.  I am on it now. As long as you have no reservations with re-installing I think that it is the easiest way to do it.[/QUOTE]

Yeah either install [Japanese Ubuntu](http://www.ubuntulinux.jp/) or wait for Dapper Drake :D

---

### Post by Kaneda on 2006-05-18
Is it possible to log in using various languages using Japanese Ubuntu?  I too have the filename problem, and I'm assuming the difference is the support of unicode file names as opposed to specifically Japanese right?   Therefore in Japanese Ubuntu, one could view Korean file names as well?  Please correct me if I'm wrong.

Also, in Japanese Ubuntu, is it possible to log in in English (or other languages) like you can log in in Japanese with normal Ubuntu?

Thanks!

---

### Post by Stormbringer on 2006-05-18
[QUOTE=dpaint4]I need support for Japanese file names in my OS.[/QUOTE]

Actually I have several files having Japanese filenames (mixture of Katakana/Hiragana/Kanji) stored on my hard drive(s); and it worked right out of the box.

System is set to en-US.UTF8 / de-AT:en, hard drives are ext3 formatted.

Copying these files to an external USB-HDD (FAT32) works great (Windows displays them correctly - however, Asian language support needs to be installed), and copying the files to an smb-share of a Windows XP Workstation works as great as well.

Shouldn't be a problem at all if the system locale is set to <whatever>.UTF8.

Storm.

---

### Post by Kaneda on 2006-05-18
Well, I tried typing locale -a in the terminal, and it looks like everything is set to <whatever>.utf8.

All my Japanese files come up as question marks (they do show properly in Japanese when I look in windows, however).

---

### Post by Stormbringer on 2006-05-18
In a terminal type "export" ... what values does

- LANG=
- LANGUAGE=

show?

---

### Post by ubuntu27 on 2006-05-18
System menu / Administration/ Language Selector


and select the languege that you want it to "support" 

In Breezy Asian language support is limited... but hope it does help you.

---

### Post by Sef on 2006-05-18
I would wait to upgrade to Dapper.  It's easy to set it up, so you can log in as either English or Japanese session and easy to switch between the japanese and English typing.

---

### Post by dmizer on 2006-05-18
okay ... i have ubuntu breezy and japanese support.  there's lots of questions in this thread so if i miss something please let me know.

first of all.  once you install anthony, you should be able to view all japanese input in your english distribution.  even in your terminal.  but just in case, make usre you have the japanese fonts installed. ie: language pack gnome ja (you can find it in synaptec, or just apt-get install language-pack-gnome-ja, and it should install all the necessary dependencies.  but just in case, below is a capture of my japanese package list in synaptic:

never tried export before, so i did it on my box.  looks like even with english utf-8, i can still read japanese in my terminal.
```
dmizer@injapan:~/work/translations$ export
declare -x ALLTRAY_SPY_WINDOW="44040195"
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-Ej2BXBsQD5,guid=fc0b6d44da4de47c1f2388e7708f0100"
declare -x DESKTOP_SESSION="gnome"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="gnome"
declare -x GDM_LANG="en_US.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-e5Y4SY/socket"
declare -x GTK_IM_MODULE="uim"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/dmizer/.gtkrc-1.2-gnome2"
declare -x HOME="/home/dmizer"
declare -x LANG="en_US.UTF-8"
declare -x LANGUAGE="en_US.UTF-8"
declare -x LOGNAME="dmizer"
declare -x OLDPWD="/home/dmizer/work"
declare -x PATH="/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games"
declare -x PWD="/home/dmizer/work/translations"
declare -x SESSION_MANAGER="unix/injapan:/tmp/.ICE-unix/7712"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="7763"
declare -x SSH_AUTH_SOCK="/tmp/ssh-ONePqT7712/agent.7712"
declare -x TERM="xterm"
declare -x USER="dmizer"
declare -x USERNAME="dmizer"
declare -x WINDOWID="46137416"
declare -x XAUTHORITY="/home/dmizer/.Xauthority"
declare -x XMODIFIERS="@im=uim"
dmizer@injapan:~/work/translations$ ls
D-12000.pdf      otcdaihen.htm           QandA.doc
file.doc         Plaswire method jl.doc  technology report.odt
file eng.doc     plaswire outline.doc    &#24179;&#25104;18&#24180;03&#26376;31&#26085;&#12288;&#65329;&&#65313;.doc
otcdaihen_files  plaswire outline.odt
dmizer@injapan:~/work/translations$
```

so, my suggestion here is to make sure that you have all your japanese support packages installed correctly.

more to come ...

---

### Post by dmizer on 2006-05-18
sorry for double post, wanted to make sure i got to everything.

for anthony, once you have it installed, simply right click on a panel and select "add to panel" ... scroll all the way to the bottom under "utility", and select uim applet.  then anthony will show on your panel and you can select japanese input via hiragana or romaji.

note: currently, anthony breaks the gui for cups management in gnome.  there's a fix out there for it, but i haven't applied it yet.

if you want to log into your machine with full japanese support (or any other lanugage for that matter), once you've installed all the needed language packages, log out.  before you enter your un/password, there is a language selection option. scroll through and select &#26085;&#26412;&#35486; (Japanese).  then all your program menus will appear in japanese.

let me know if you have a problem.

wanted to add: for me (not sure if this is true for all systems) anthony was fairly unstable and caused my panels to hang.  i removed it from panel and mapped a key on my keyboard to switch between direct english input and romaji/japanese input.

---

