---
title: "PLEASE PLEASE tell me how to install wine"
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by Cardmaster91 on 2006-08-13
I am a noob to linux, and i want to play my good ol' windows based games. Can anybody give me a thurough step by step explanation for installing wine, and how to use wine. I have checked many forums, but they all seem to be for more advanced users, because i have absolutely no idea what they talk about.

---

### Post by foolsh on 2006-08-13
sudo apt-get install wine

but wine hasn't even reached version 1 yet and while most application do work most games do not sorry

however it is some where in the version .9 some where which means its really close i keep a window partition on my harddrive just for games.

---

### Post by Cardmaster91 on 2006-08-13
once again, i am a complete noob to linux. im not really shure wat to do with 
sudo apt-get install wine. i put it in the terminal, and got this 

Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

please explain

---

### Post by blackened on 2006-08-14
In the terminal type:
```
sudo gedit /etc/apt/sources.list
```

add the following to the end of the file

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

In the terminal again:

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by Cardmaster91 on 2006-08-14
well... um...
i did wat u said, nothing haped, but i assume wine is on the system. but how do i use it, how can i run games on it, like world of warcraft for example (which is pretty much the only game i play)

i just tried installing steam, it went all good, opened using wine, and there is a icon on the desktop. I click the icon, and this shows up 
"Couldn't display "/home/tony/Desktop/Steam.lnk"."

is there some special way of opening it?

---

### Post by Buffalo Soldier on 2006-08-14
> **Cardmaster91 said:**
> once again, i am a complete noob to linux. im not really shure wat to do with 
sudo apt-get install wine.

Your new best friend is the [Community Documentation](https://help.ubuntu.com/community) for Ubuntu and the [Official Ubuntu Desktop Guide](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html).

From the [Community Documentation](https://help.ubuntu.com/community), what I'd suggest a complete nood to read are:[list]
[*] [Switching to Ubuntu from Windows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

[*] [What is sudo?](https://help.ubuntu.com/community/RootSudo)

[*] [Software Management](https://help.ubuntu.com/community/SoftwareManagement): Installing applications, managing repositories & etc etc.

[*] [Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats): How to install additional codec and WHY it is not included in the default install.

[*] [How to install Wine](https://help.ubuntu.com/community/Wine)

[/list]

---

### Post by Cardmaster91 on 2006-08-14
I took a brief llok over those links, they look pretty good.
Thank you, that should get me started.

---

### Post by patrick295767 on 2006-08-14
Official 
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
 
older version:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
```
dpkg -i debs-dowloaled.deb 
```
 0.9.18 & 0.9.17 are rather ok for some games still
Last version wine: 0.9.19
 
wine tools:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
(for installing word M$)
 
(apt-get -f -y install wine
will give you a non last updated version of wine ; compatibility ? )

--
Concerning a non-free wine: 
crossover weavers
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

---

### Post by Cardmaster91 on 2006-08-14
ok, the code you gave me 

dpkg -i debs-dowloaled.deb 

gives me this response 
dpkg: requested operation requires superuser privilege

i am the only user on this computer, i really have no idea wat its talking about

---

### Post by eqisow on 2006-08-14
In Linux you always run as a 'normal' user, meaning you have no access to anything outside your home directory. This is a security issue. There is, however, a way to temporarily elevate your privelidges to do administrative task such as install software. Be careful, though, because with great power comes great responsibility. If you have root (admin) priviledges, Linux won't even bat an eye before erasing your entire system. (If that's what you tell it to do, of course)

Now, with all of that out of the way, try this:

sudo dpkg -i debs-dowloaled.deb

---

### Post by Cardmaster91 on 2006-08-14
i really am a noob, everytime someone tells me to do something, i get an error. This time, this came up

dpkg: error processing debs-dowloaled.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 debs-dowloaled.deb

---

### Post by Cardmaster91 on 2006-08-14
ok, im gonna make this simple for all of you. All that i really want is to play WoW on ubuntu. I would like a simple step by step instructions for installing and playing wow. Note: i am a new linux user and i have no clue what im doing half the time

---

### Post by patrick295767 on 2006-08-14
;) > **Cardmaster91 said:**
> i really am a noob, everytime someone tells me to do something, i get an error. This time, this came up

dpkg: error processing debs-dowloaled.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 debs-dowloaled.deb

"debs-dowloaled.deb", It was an example 
 
So, to install for instance an older version:
 
You may start an xterm or konsole, then type:

```
cd /tmp
wine --version
sudo whereis wine    # no wine will be found, certainly
wget -N http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.18~winehq0~ubuntu~6.06-1_i386.deb
sudo dpkg -i wine_0.9.18~winehq0~ubuntu~6.06-1_i386.deb
sudo whereis wine    # wine will be found, certainly
wine --version
```

I hope you understand a bit better

It's a more detailed example, with playing user & root rights
root to install programs
users to use the programs 
as said above, for security. 

Dont hesitate to ask questions, this forum is made for sharing knowledge & experience, and we will be glad to help you !

See ya'

---

### Post by eqisow on 2006-08-14
OK, for playing WoW on Ubuntu check [here]("https://help.ubuntu.com/community/WorldofWarcraft"). The page has specific, step by step, instructions for installing Wine and configuring it to play WoW.

Good luck!

---

### Post by Cardmaster91 on 2006-08-14
that page lies, i hate it. this is like the 5th time ive been referd to that page. everytime i get to this part, 

Installing WoW

Copy all of the files from all of the CD's to a directory on your hard drive (overwrite when prompted),**[SIZE="4"][SIZE="6"] then run Install.exe [/SIZE][/SIZE]**or copy the World of Warcraft folder from a Windows installation.

Note: With 0.9.14 - 0.9.18, the installer will appear to hang with cpu @ 100%. Patience! Give it about 5mins, and a dialogue will eventually appear

Need confirmation on if bug exist on 0.9.19


how the hell do u run it!?!?!

p.s. i have tried r-clicking, going to properties > open with  and then click wine. only problem is that "wine" is not in that list

---

### Post by eqisow on 2006-08-14
When you go to 'Open With' click add, then click use custom command and type wine in the box, then click add. Make sure the new option for wine is selected and hit ok.

Alternatively, you can run the installer from the command line by typing 'wine ' (no quotes) and dragging and dropping the Install.exe file to the terminal then hitting Enter.

---

### Post by Cardmaster91 on 2006-08-14
how do u run winecfg?

---

### Post by eqisow on 2006-08-14
Just type winecfg at the command line.

---

### Post by Phantom784 on 2006-08-14
just type winecfg at the command line.  it'll then walk you through setting up wine.  if i recall, you don't even need sudo for it.

btw, i installed wine with automatix as soon as i installed ubuntu.  if you've been using ubuntu for a while, it could screw up your system, but on a fresh or fairly recent install, it should be pretty helpful.

---

### Post by Cardmaster91 on 2006-08-14
i tried that automatix thing, but i had no idea wat to do with it, or how to use it.

---

### Post by alinuxfan on 2006-08-14
alright bud...
use this link [install WoW]("http://ubuntuforums.org/showthread.php?t=120615")
I used the way kid charles did it and installed with NO problems
If any questions arise do a search of the ubuntu forums or google.  there has been many a question asked and most have been answered.  Especially things concerning the basics of Ubuntu or linux in general.
It may take you some time to get it working...just be patient and learn as much about the OS while you are working your way through the install of WoW.
Don't be afraid to get your hands dirty with the CLI and enjoy FOSS.


alinuxfan

---

### Post by Cardmaster91 on 2006-08-14
i've already tried kid charles's directions. i couldnt understand it. And i think im finally getting it installed thanks to eqisow

---

### Post by Cardmaster91 on 2006-08-14
does anybody know how to fix source crc mismatch? it came up both times i tried to install world of warcraft. the first froma copy on the computer, thje second from the disks

---

### Post by eqisow on 2006-08-14
Text in game should be fine.

As far as your error, could you be more specific? I'm not sure exactly what you mean.

---

### Post by Cardmaster91 on 2006-08-14
well, it wont let me copy the text out of the window, but what happend was i was installing, and i window popped up saying something like "source crc mismatch error" i checked blizz support page. didnt really help much tho.

---

### Post by Cardmaster91 on 2006-08-14
ok, well im installing world of warcraft right now, i hope it works. but i have a question about the next step. they say 

Next, add the following to the file WTF/Config.WTF in your WoW directory.

SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"


first of all, do u put that in terminal? or do u put it in a text file?  and how do u get to the wow directory?

---

### Post by Cardmaster91 on 2006-08-14
the same problem came up again. here is exactly what it says


Patch data is bad. (source CRC mismatch: 1875001978/-498909991) (BNUpdate::PTCApply)


the window just pops up during installation. Please help

---

### Post by croak77 on 2006-08-14
> **Cardmaster91 said:**
> the same problem came up again. here is exactly what it says


Patch data is bad. (source CRC mismatch: 1875001978/-498909991) (BNUpdate::PTCApply)


the window just pops up during installation. Please help

Did you download mfc42.dll?

---

### Post by Cardmaster91 on 2006-08-14
i dont recall

---

### Post by croak77 on 2006-08-14
Maybe it will help.

"If patches do not work, you will need to get mfc42.dll from a windows installation ([http://dll-files.com](http://dll-files.com)) and place it in .wine/drive_c/windows/system. You will, however, need a Windows license to use this file."

---

### Post by Cardmaster91 on 2006-08-14
> **croak77 said:**
> Maybe it will help.

"If patches do not work, you will need to get mfc42.dll from a windows installation ([http://dll-files.com](http://dll-files.com)) and place it in .wine/drive_c/windows/system. You will, however, need a Windows license to use this file."

its not the patches, its the installation, and how would u get to .wine/drive_c/windows/system

---

### Post by croak77 on 2006-08-14
Do you have the proper wine installed?

---

### Post by Cardmaster91 on 2006-08-14
i have the latest version of wine

---

### Post by croak77 on 2006-08-14
From the repo or from the wiki how to article? 

wine-0.9.19_wow_i386.deb

---

### Post by Cardmaster91 on 2006-08-14
what?

---

### Post by croak77 on 2006-08-14
From here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

How did you install wine? With apt-get? Did you patch it with the needed patch?

---

### Post by handy on 2006-08-14
I just use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646"), to install Wine, & then [WineTools]("http://www.von-thadden.de/Joachim/WineTools/"), to set Wine up...

---

### Post by Cardmaster91 on 2006-08-14
i did everything up to installing wow. thats when the error message comes up

---

### Post by croak77 on 2006-08-14
So you installed wine-0.9.19_wow_i386.deb or not?

---

### Post by Cardmaster91 on 2006-08-14
> **handy said:**
> I just use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646"), to install Wine, & then [WineTools]("http://www.von-thadden.de/Joachim/WineTools/"), to set Wine up...

i tried automatix, but i had no idea how to use it. Besides, thats not the problem anymore. Im having trouble installing wow

---

### Post by Cardmaster91 on 2006-08-14
> **croak77 said:**
> So you installed wine-0.9.19_wow_i386.deb or not?

idk, i just did what the website said

---

### Post by croak77 on 2006-08-14
Did you copy the all the cd's to a folder on your hard drive?

---

### Post by Cardmaster91 on 2006-08-14
yes, then i ran them, and the error message came up.

---

### Post by croak77 on 2006-08-14
Try downloading these 2 files:

[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

And place them in your /home/your_username/.wine/drive_c/windows/system32/ folder. Open a terminal and use the 'mv' command.

```
mv msvcp60 mfc42 /home/your_username/.wine/drive_c/windows/system32/  
```

---

### Post by Cardmaster91 on 2006-08-14
home/my_username(tony) is not there. there is no folder

---

### Post by croak77 on 2006-08-14
Did you run winecfg from a terminal?

---

### Post by Cardmaster91 on 2006-08-14
no, that step was after installing world of warcraft

---

### Post by croak77 on 2006-08-14
Did you run?

```
 wine /path/to/WOW/cds/Install.exe
```

It might be Installer.exe. It in the folder where you copied you warcraft cd's.

---

### Post by Cardmaster91 on 2006-08-14
no

---

### Post by croak77 on 2006-08-14
I would run winecfg or maybe just wine first. It should create your .wine foldor for you. Then move the dll's to the system32 folder. Then install WOW with wine /path/to/Installer.exe.

---

### Post by Cardmaster91 on 2006-08-14
i ran winecfg in the terminal, and a window came up, what exactly do i do now?

---

### Post by croak77 on 2006-08-14
For now just make sure the Windows Version is set at Windows 2000 and Audio is set to OSS. Hit ok. Then check to see if .wine direstory was created.

From a terminal:

```
 ls /home/your_username/.wine
```

---

### Post by Cardmaster91 on 2006-08-14
it says no such file or directory

---

### Post by croak77 on 2006-08-14
OK. Try downloading this:

[http://prdownloads.sourceforge.net/wine/MozillaControl1712.exe?download](http://prdownloads.sourceforge.net/wine/MozillaControl1712.exe?download)

You might need it anyway. Then install with wine /path/to/MozillaControl1712.exe

---

### Post by Cardmaster91 on 2006-08-14
do i open it with sumthin? or svae to disk?

---

### Post by croak77 on 2006-08-14
Save it to your hard drive then install it with wine.

---

### Post by Cardmaster91 on 2006-08-14
it wants me to pick where mozzila bin directory is

---

### Post by croak77 on 2006-08-14
I got to run. Good luck

---

### Post by Cardmaster91 on 2006-08-14
What!?

---

### Post by handy on 2006-08-15
Have you read this [WOW thread]("http://ubuntuforums.org/showthread.php?t=92367&highlight=world+warcraft")?

Surely every conceivable problem has been covered in great detail, it is a huge thread that has been running since November last year.

---

### Post by Cardmaster91 on 2006-08-15
that one doesnt have the answer to my problem

---

### Post by judgejudy on 2006-08-15
ok i need some help aswell
were to start?..hmmm  ok new to linux but want to move over full time and there is only 1 app i need and thats vintrilo so i can talk to my windows friends having read this post and trying some things from it i got wine to install the vintrilo.exe i used :When you go to 'Open With' click add, then click use custom command and type wine in the box, then click add. Make sure the new option for wine is selected and hit ok.

Alternatively, you can run the installer from the command line by typing 'wine ' (no quotes) and dragging and dropping the Install.exe file to the terminal then hitting Enter: 
this worked for me so it is now installed (i hope) How do i now use vintrilo as in how do i get to the gui/luncher I am useing the gnome desktop

---

### Post by Cardmaster91 on 2006-08-15
u got ventrilo working, cool. ventrilo is a must if u play wow(teamspeak sucks ***)

---

### Post by Cardmaster91 on 2006-08-15
ok, i dl ventrilo, and when i click the desktop icon, nothing happens. Its set to open with wine.

---

### Post by judgejudy on 2006-08-15
no i havent got ventrilo working :( and as for wine i dont have a icon for it and when i right click its not on that list i am about to give up on linux because of this everything is so hard to do. all this sudo this and sudo that crap all i want is the app to work like windows we may all dislike m$ but you dont need to be a progamer to get anything to work dbl click the .exe and it works so plz plz can someone help a nube out with a walkthrough/how to with wine and gnome/ubuntu thanks for your help

---

### Post by judgejudy on 2006-08-15
ok found a walkthrough can now find my .wine foulder but every time i try and set up wine i get this


Crory@rory-ubuntu:~$ winecfg
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
Creating link /home/rory/.kde/socket-rory-ubuntu.
can't create mcop directory
do i need the kde desktop?

---

