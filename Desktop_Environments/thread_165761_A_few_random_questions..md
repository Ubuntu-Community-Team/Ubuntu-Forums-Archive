---
title: "A few random questions."
date: 2006-04-25
forum: Desktop Environments
---

### Post by yngndrw on 2006-04-25
Hi,

Firstly, I am quite new to Linux. However I am used to doing a lot in the Windows command prompt so that helps me out a lot. To give you an idea about what level I'm at: I have been able to install (From source) Apache and PHP, along with MySQL from a binary and a game server.

I am running Ubuntu Breezy 5.10 standard installation.

1) What is the best method of remote controlling this machine from a different Windows machine ? I need to be able to edit text files.

2) Is there an in-terminal text editor ? I.e. An editor which doesnt require a GUI to run, hence can be run using SSH etc.

3) I seem to have a problem with using 'screens'.
I have a script on my desktop which has the following: (It is run as a non-root user. The owner(s) on the game server filesystem are set as root:yngndrw, so that I can edit files from the GUI. I guess I should really make the server it's own user and group, and just add 'root' and 'yngndrw' to the new group.)
```
cd /srcds
sudo screen -A -m -d -S css-server ./srcds_run -game cstrike -autoupdate -port 27015 +map de_dust +maxplayers 16

```

However when I run 'screen -list' from root, it always says that the screen is 'Dead'. I have found that adding the following line in that same script:
```
sudo screen -x css-server
```
Does fix the problem. Am I doing something wrong because I dont think that I should have to connect to the screen in order to use it.

4) On my other installation, a Windows - Ubuntu dual boot, I have an nVidia graphics card. However When I try and install the nVidia drivers I get 'You are running an X server, please close this blah blah blah.'. How do I do this ?
Also linked to the same thing: When installing the nForce drivers, it says that it needs the Kernal source files but can't find them. I have googled around but I don't know how to get them ?


Thank you for your time.

**Edit:** Oh yes just remembered: For question 1, what port does whatever suggestion that you give require to be open ?

---

### Post by tseliot on 2006-04-25
[QUOTE=yngndrw]4) On my other installation, a Windows - Ubuntu dual boot, I have an nVidia graphics card. However When I try and install the nVidia drivers I get 'You are running an X server, please close this blah blah blah.'. How do I do this ?
Also linked to the same thing: When installing the nForce drivers, it says that it needs the Kernal source files but can't find them. I have googled around but I don't know how to get them ?[/QUOTE]
Follow my guide. I think you're trying to install the drvier with Method 2.
[HOWTO: Latest NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=75074")

---

### Post by yngndrw on 2006-04-25
Thank you for your reply **tseliot**.

I will have a go at that later when I get back from college. After having a quick look through, yes I was attempting Method 2. I think Method 1 will be find for me however.

Cheers. :)

---

### Post by dpm on 2006-04-25
> 1) What is the best method of remote controlling this machine from a different Windows machine ? I need to be able to edit text files. 
I would use either a) ssh (you'll need the openssh server running on your ubuntu machine and an ssh client on the windows machine, putty for example) or b) vnc (you'll need a vnc server on your ubuntu box, like vnc4server and a vnc client on your ubuntu box, ultravnc or tightvnc, for example).

Note that vnc is not encrypted per default, but you can easily tunnel it over an ssh connection if necessary.

You could also use cygwin from windows, start an x server and start gedit remotely over ssh. In this way you could even have a graphical editor if you wanted (note: this should in theory work, although I've never tried it myself from a windows machine).

> 
2) Is there an in-terminal text editor ? I.e. An editor which doesnt require a GUI to run, hence can be run using SSH etc. 
vim, emacs, nano ... you name it. If you come from windows nano might be the easiest option at the beginning. If you need more powerful editors later on (with a steep learning curve, by the way), I would personally give vim and emacs a try, in this order. Note that both vim and emacs have also got graphical versions.

Cheers.

---

### Post by yngndrw on 2006-04-25
Thanks **desp**.

I have just setup SSH and been able to connect to the box with Putty. I'll try Cygwin tomorrow.

After trying Nano, it seems ideal for my needs. I don't think that I would be needing a more powerful editor than that in a while.

Cheers. :)

---

### Post by dpm on 2006-04-25
I'm glad my comments were helpful.

> After trying Nano, it seems ideal for my needs. 
Just a quickie about nano (this drove me mad for some time, because is not so obvious): there is no keyboard shortcut for the "copy" (CTRL+C in Windows) command. Instead you must just cut and paste every time you want to copy something. That is, nano's equivalent to CTRL+C in Windows seems to be  CTRL+K, CTRL+U. Other than that, the nano help  (CTRL+G) is quite nice.

Cheers.

---

### Post by yngndrw on 2006-04-25
Cheers for the heads up. I guess that is because Ctrl+C is taken up for the close command. Will save me the heartache of closing the file I'm working on every time I try and copy something hehe.

---

