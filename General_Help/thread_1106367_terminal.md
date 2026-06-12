---
title: "terminal"
date: 2009-03-25
forum: General Help
---

### Post by 762sks on 2009-03-25
ok i am fairly new to linux/ubuntu right! and so far i really like what i see. i am finally able to set up ubuntu on my second system. got it working and i seem to have a video problem, search for a solution and i think i got it licked!! 

anyways, so like alot of you i have used windows for many, many , many years. and part of that was using msdos. now i know linux has the terminal right. but is there some documentaion somewhere that tells you how to use this thing??? 

not that i havent used it, but most all of my use is coping what i see here and pasting it into the terminal. 

so thats kinda my question, for example in msdos if i wanted to change dir i would type like cd:\\ whatever right. 

also i think this (meaning ubuntu) would really take off if it you guy were to make alot of it similar to windows and maybe offer documentaion to help new people like commands for the terminal. 

i ecently setup samba on my machine, but wouldnt it be easier for everyone if they had a windows that you could just click different options to change what they wanted, like directories. or just make it like windows where you can just right click on the folder and goto sharing and click share. i know it probably takes alot to do, but like i said the more windows like this is the quicker it will take off. 

seems to me that alot of what you want to do is done through the terminal. say for example if i goto nvidias website and download the latest drivers right. nvidia says that it an executable file. if so then why should i have to run it from terminal? cant i just double click it and be able to run it?

and no im not bitching incase someone was thinking it. i love this operating system and i hope it continues to grow. hopefully these ideas will help. 



Thanks 

Neil

---

### Post by kryptikos on 2009-03-25
Hi Neil,

Welcome to Linux Country. Some of the features you are talking about are already included. You can associate files and 'executables' just as in Windows. There is a lot to explore. Learning the command line just makes you a better and more powerful user (in my opinion). It's like learning to drive a standard. Anybody can drive an automatic, but if you can drive a standard you can drive anything. The terminal is your standard. Plus often (once you get used to commands) it is faster to just type what you are looking for then moving the mouse to an icon, click, wait for window to pop up, move mouse to menu, click, wait for sub-menu...oh wait, moused over to far and lost sub-menu, reclick, click...well you get what I mean. :)  so with time (and it can be frustrating just don't lose hope, hit the boards often, you'll find most everyone is very friendly and helpful) you will master the terminal. 

Reference your question here are a few links that may help you get familiar with it: 

[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

[http://www.freesoftwaremagazine.com/articles/command_line_intro]("http://www.freesoftwaremagazine.com/articles/command_line_intro")

If you want real nitty gritty and insomnia-cure reading check this HOWTO:

[http://tldp.org/HOWTO/Text-Terminal-HOWTO.html]("http://tldp.org/HOWTO/Text-Terminal-HOWTO.html")

Best of luck! Again welcome :)

---

### Post by kestrel1 on 2009-03-25
This might help a little with the terminal commands: [https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)
A few of the terminal commands are similar or the same as DOS. If you want to change to a directory you would use ```
cd /dirname
```

---

### Post by kanikilu on 2009-03-25
> **762sks said:**
> anyways, so like alot of you i have used windows for many, many , many years. and part of that was using msdos. now i know linux has the terminal right. but is there some documentaion somewhere that tells you how to use this thing??? Just about every command has a detailed manual (man page). To view the page for cd for example, type **man cd** (hint, press q to exit when you're done)

> also i think this (meaning ubuntu) would really take off if it you guy were to make alot of it similar to windows and maybe offer documentaion to help new people like commands for the terminal.  
"Similar to windows" is a very subjective (and polarizing) statement. If you have more specific suggestions for improvement, check out the Ubuntu Brainstorm:

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Also, there is **tons** of documentation, for example:

man pages
[https://help.ubuntu.com/](https://help.ubuntu.com/)
System > Help and Support (in the default Ubuntu Gnome desktop)
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/) <-- free book
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

etc...

> i ecently setup samba on my machine, but wouldnt it be easier for everyone if they had a windows that you could just click different options to change what they wanted, like directories. or just make it like windows where you can just right click on the folder and goto sharing and click share. i know it probably takes alot to do, but like i said the more windows like this is the quicker it will take off. Check out the nautilus-share package...

---

### Post by evilaim on 2009-03-25
Well, let me start by saying none of my comments are 'snotty' or anything so please don't take it wrong.

Now, if you would search google, there are over a million tutorials on how to use ubuntu CLI (Command Line interface).  And I don't think many Linux users would agree that this interface needs to be more like windows.  Especially Dos.  If you'd like some good tutorials I could link you, or you could just google.

Samba does have a GUI, it isn't installed with samba because not everyone likes GUI's.  I find them to use up resources which is a waste.

[http://ubuntuforums.org/showthread.php?t=222725](http://ubuntuforums.org/showthread.php?t=222725) <-- That's a web based editor for samba.  Pretty easy to use.

[http://ubuntuforums.org/showthread.php?t=387598](http://ubuntuforums.org/showthread.php?t=387598) <-- and that's for the CLI for beginners.

I hope this helps.

-Evil

---

### Post by ibuclaw on 2009-03-25
> **762sks said:**
> 
anyways, so like alot of you i have used windows for many, many , many years. and part of that was using msdos. now i know linux has the terminal right. but is there some documentaion somewhere that tells you how to use this thing???
The command:
```
man
```
Is your friend... it is the gateway to all the documentation for all commands available on your machine.

ie:
```
man samba
```
For other samba worries, there is a GTK App for Managing Samba servers.
```
sudo apt-get install gadmin-samba
```
And go to "**Applications->System Tools**" and you'll see it there.

Also, be sure to check out the Free [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/").

Regards
Iain

---

### Post by mb_webguy on 2009-03-25
Making the Linux terminal more like the MS-DOS command prompt isn't going to happen, partly because the basic Linux commands have been around a lot longer.  Linux is essentially an open-source version of Unix, which has been around since 1969.  There are plenty of [tutorials and reference guides]("http://ubuntuforums.org/showpost.php?p=990636&postcount=1") for the terminal.

As for file sharing via Samba... You can do exactly what you're talking about.  Just open the file manager, right-click on a folder, and select Sharing Options.  If you don't have Samba installed the first time you tried this, the system will install and configure Samba for you.  If you installed Samba using a different method, you did it the hard way.

You can do almost anything you want in Ubuntu using the GUI.  You can simply do it faster and with more options in the terminal if you know the commands to use.  The reason you see a lot of terminal commands in HowTos and forum posts is that it's a lot easier to tell someone to enter a command or two in the terminal than it is to say "Click here, now click here, now click here, now click here..."  Also, the terminal is the same regardless of what desktop environment you're using.  Since Ubuntu has several different desktop environments available (Gnome for Ubuntu, KDE for Kubuntu, Xfce for Xubuntu) and can be highly customized (such as by using a windows manager like Openbox instead of a full desktop environment), terminal commands are the best way to provide solutions that are applicable to any system.

The simple answer is that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"), will never be Windows, and shouldn't be Windows.  The goal of the Linux community is to create the best operating system possible, and you can't do that by slavishly copying another operating system that many people consider inferior.  Personally, I think that Ubuntu is already easier to use than Windows for completely new users.  The desktop environments are better organized, it's much easier to install software (using repositories), and you don't have to worry about running anti-virus and anti-spyware applications. It's only really difficult for former Windows users who expect everything to work the same as in Windows.

---

### Post by kestrel1 on 2009-03-25
> The simple answer is that Linux is not Windows, will never be Windows, and shouldn't be Windows. The goal of the Linux community is to create the best operating system possible, and you can't do that by slavishly copying another operating system that many people consider inferior. Personally, I think that Ubuntu is already easier to use than Windows for completely new users. The desktop environments are better organized, it's much easier to install software (using repositories), and you don't have to worry about running anti-virus and anti-spyware applications. It's only really difficult for former Windows users who expect everything to work the same as in Windows.
I go along with all of this, it is basically easier to use Linux for first timers. It is the ex Windows users that find it harder to think outside of the the Windows box. I used to be one of them, even though I still have to use Windows for my job, I much prefer to work on a Linux machine when I can.

---

