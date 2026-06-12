---
title: "[SOLVED] Installing Vendetta Online....Ubuntu Gamers Arena"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by RadarBat on 2008-06-13
I am sorry but the below code did not work installing Vendetta Online:
```
mkdir ~/bin
cd ~/Desktop
sh vendetta-linux-amd64-installer.sh
rm -rf ~/bin
```
Nor does the command in this:
> Name: Vendetta Online
Command: /home/USERNAME/.vendetta/update.rlb
Comment: Vendetta Online is a 3D space combat MMORPG for Windows, Mac and Linux.
Icon: ~/.vendetta/vo.png
But what did was not using the "rm" code and using the command:
/home/USERNAME/bin/vendetta

What does the "rm" command do in this instance?
Nice game, by the way....Ben

---

### Post by cogadh on 2008-06-13
The "rm" command is the remove command i.e. it deletes the directory. I believe the ~/bin directory is just a temporary directory used during the install and can be deleted once the install is complete. After the game is installed, it is found in ~/.vendetta. Did you try running those commands all at once, or did you run each one individually as you are supposed to do?

The second part is not actually a command, that is the information you need to copy/paste into Alacarte to create the Applications menu entry for the game. You need to replace the "USERNAME" with your actual user name.

---

### Post by Perfect Storm on 2008-06-14
Aye. You have to make the bin in your home folder to install VO, thereafter the guide tell you to delete it as you don't need it anymore.
The reason why making the bin is that the installer will loop endlessly if it can't find it (a bug).

---

### Post by RadarBat on 2008-06-14
Where is "/.vendetta"? I cannot find it on my HDD. I tried the "whereis" command, but no luck.
How do I uninstall VO? It's not in Add/Remove....?

---

### Post by Vadi on 2008-06-14
Afraid it's not in Add/Remove. Very few commercial software is in there atm.

---

### Post by cogadh on 2008-06-14
> **RadarBat said:**
> Where is "/.vendetta"? I cannot find it on my HDD. I tried the "whereis" command, but no luck.
How do I uninstall VO? It's not in Add/Remove....?
It's not "/.vendetta", it's "~/.vendetta". It is a hidden directory in your home directory ("~/" is terminal shorthand for your home directory). In order to see it, you need to show hidden files in the file browser first. Uninstalling it is as simple as deleting the ~/.vendetta directory and manually deleting the menu entries.

---

### Post by Sammi on 2008-06-14
> **RadarBat said:**
> I am sorry but the below code did not work installing Vendetta Online:
```
mkdir ~/bin
cd ~/Desktop
sh vendetta-linux-amd64-installer.sh
rm -rf ~/bin
```What happens when you run those commands?

What output do you get in the terminal?

We can't be sure what happened before we see the output.

---

### Post by RadarBat on 2008-06-16
Thank you for trying to help me. That code **does** work. I was doing something? wrong....Ben

---

### Post by Sammi on 2008-06-17
Well then everything is just peachy :D

---

### Post by reysol48 on 2008-08-31
Ok this all i get when try to installl the game

pedro@pedro-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
pedro@pedro-desktop:~$ mkdir bin
pedro@pedro-desktop:~$ sh ./vendetta-linux-ia32-installer.sh
sh: Can't open ./vendetta-linux-ia32-installer.sh
pedro@pedro-desktop:~$ chmod +x vendetta*
chmod: cannot access `vendetta*': No such file or directory
pedro@pedro-desktop:~$ chmod +x vendetta
chmod: cannot access `vendetta': No such file or directory
pedro@pedro-desktop:~$ sh ./vendetta-linux-ia32-installer.sh
sh: Can't open ./vendetta-linux-ia32-installer.sh
pedro@pedro-desktop:~$ cd ~/desktop
bash: cd: /home/pedro/desktop: No such file or directory
pedro@pedro-desktop:~$ sh ./vendetta-linux-ia32-installer.sh
sh: Can't open ./vendetta-linux-ia32-installer.sh
pedro@pedro-desktop:~$ 


so any idea what i am doing wrong?

---

### Post by Perfect Storm on 2008-08-31
> pedro@pedro-desktop:~$ cd desktop

Linux is case sensitive. It's **Not** cd desktop
but **cd Desktop**.

> pedro@pedro-desktop:~$ sh ./vendetta-linux-ia32-installer.sh
sh: Can't open ./vendetta-linux-ia32-installer.sh

chmod +x the file first.

---

### Post by tugalsan on 2009-10-26
hi, i used the below code and it worked.

sh installVendetta.sh

then 
/home/me/bin/v
as install directory

but how can i uninstall it. I could not see it on Synaptics Manager. And the file on /home/me/bin/v/vendata/* is in kbs like a link file in windows. any ideas appricated. :(

---

### Post by AgentZ86 on 2009-12-21
Is this still a problem for people ?

I'm using Ubuntu 64 9.10

All I did was download the vendetta file,
Went to my download folder 
Right click the file and select properties
Go to the Permissions Tab
Select or put check mark next to - Execute: Allow Executing file as a program = aka (make it executable) 
and then clicked on the file and select RUN

It installed perfectly

It ask things like do I want to create a .bin file (y)
install (y) etc. very simple to install on it's own. Just use the default or select yes.

I then navigate to the bin file in my home directory, and right click the file to create a link to the game file, move the link to my desktop
Then just click the file and it loads up everytime. 

I am having sound quality problems currently, but only partial sound problem. I think related to 9.10 sound system
It works but after a while it gets crackly and starts flaking out on me.

I'm was looking for a solution for the sound problem and saw this, figured I would post in case it may be helpful for anyone.

I hope everyone gets it working it's a nice game maybe the best linux game I've found so far.

---

### Post by Sealbhach on 2010-03-06
> **AgentZ86 said:**
> 

I am having sound quality problems currently, but only partial sound problem. I think related to 9.10 sound system
It works but after a while it gets crackly and starts flaking out on me.

I'm was looking for a solution for the sound problem and saw this, figured I would post in case it may be helpful for anyone.


EDIT: There's been an in-game update which seems to have sold the sound problems. 

.

---

### Post by AgentZ86 on 2010-03-09
> **Sealbhach said:**
> EDIT: There's been an in-game update which seems to have sold the sound problems. 

.

Thanks

---

### Post by AgentZ86 on 2010-05-01
> **Sealbhach said:**
> EDIT: There's been an in-game update which seems to have sold the sound problems. 

.

I'm not sure it's related, but it seems that the video ad sound is very choppy since the in game updates.

I cannot seem to play the game anymore because it's unplayable.

I still believe it's related the the sound topic.

At once I used to add a line into the config.ini of vendetta 
[alsa]
periods = 1024

And that use to solve all my sound cracklings and video choppiness of the game.

But now I can't really get past the login screen because it's sooooo laggy that the mouse sort of moves a pixel at a time just to navigate to the login or quit areas.

However, while i'm moving my mouse etc. the sound it working well LOL

Oh well I don't know what else to do with it, I'm sure it's pulseaudio related but I can't be sure.

---

