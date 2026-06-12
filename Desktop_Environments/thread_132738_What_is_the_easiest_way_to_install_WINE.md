---
title: "What is the easiest way to install WINE?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by eric.stone on 2006-02-18
Is it through backports?  If yes, how do I add backports to the repository?
Thanks,
Eric

---

### Post by Mikecore on 2006-02-18
Try reading the Ubuntu wiki

[http://www.ubuntulinux.org/wiki/FrontPage](http://www.ubuntulinux.org/wiki/FrontPage)

has some real nice tuts for noobs

---

### Post by s_h_a_d_o_w_s on 2006-02-18
Install AUTOMATIX (it's a great program) 

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

follow those instructions.

Applications->System tools-> Automatix

once you're in automatix, check the wine checkbox and install it (button on bottom)

it installs.....

There you go. (you can use automatix to install many other programs very easily)

Good luck!!!

---

### Post by JELaVallee on 2006-02-18
[QUOTE=eric.stone]Is it through backports?  If yes, how do I add backports to the repository?
Thanks,
Eric[/QUOTE]

I had it working well for installing IE6... Automatix is the way to go for installing on Breezy.

I've since bit the bullet and paid for VMWare (which I needed for work) and Crossover Office Standard.  Crossover really makes WINE bearable if you're not in the mood for endless tweaking...

cheers,
Etienne

---

### Post by cyborgspiders on 2006-02-18
I just installed Wine on Ubuntu and I want to write down while it's fresh. I have all the repositories open, though there are likely more. I don't know which one has wine? Just copy them all. The bottom of this file will include my repository list. Your repository list is found in /etc/apt/sources.list
Just go at it with a text editor.

Just uncomment all the sources that are there, or add my list to your file.
(see bottom of this document)

Then, using synaptic install wine-dev
OR
command line
$sudo apt-get install wine-dev
should also work. I used synaptic this time. Then at the command line type $wine-dev

wine will configure itself. On Ubuntu Breezy that's it!!! To use wine. Download a suitable program, like winzip, to a separate folder.[http://www.winzip.com/]("http://www.winzip.com/")

mkdir win-exe

then cd /home/user/Desktop/win-exe  if the program is on your Desktop and type
for example:::
wine winzip100.exe
with winzip100.exe in your working directoy. That's it....I just zipped a file with winzip on Linux. What a rush!

note: when it asks you where to install winzip, use the default locations, and don't be afraid of lettin er rip. I was surprised when it asked for the default of c:\Program Files\WinZip
Just use that and it works.

For a list of the applications that you can easily use.....
-------------------
[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php)
--------------------

Hope this saved you some time.......

Greg Magnusson (c) 02-18-2006 MIT license
[http://www.opensource.org/licenses/mit-license.php](http://www.opensource.org/licenses/mit-license.php) 

######################################
UBUNTU REPOSITORY LIST from /etc/apt/sources.list
give each deb-src one line
######################################

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
# Maxed Out Breezy Badger repository file
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

#############################################

may the source be with you \\:D/

---

### Post by claydoh on 2006-02-18
Really, all you need to do is [follow the instructions from wine's website]("http://www.winehq.com/site/download-deb")
You simply have to add a line to your sources.list. this will give you the latest version.

[Wine's application database]("http://appdb.winehq.org/") is a great place for up-to-date info, as many how-to's out there are quite outdated in relation to the newest wine versions

---

