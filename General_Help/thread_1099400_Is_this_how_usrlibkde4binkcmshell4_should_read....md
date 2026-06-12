---
title: "Is this how /usr/lib/kde4/bin/kcmshell4 should read..."
date: 2009-03-18
forum: General Help
---

### Post by ozguitarplayer on 2009-03-18
I can't setup file sharing because kcmshell4 is missing

this is how the file reads from terminal 
nigel@ubu8:~$ sudo nano /usr/lib/kde4/bin/kcmshell4

GNU nano 2.0.7 File: /usr/lib/kde4/bin/kcmshell4
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@&#1028;^D^H4^@^@^@l^H^@^@^@^@^@^@4^@ ^@^$
^@^@^@  ^@^@^@^M^@^@^@^A^@^@^@^@^@^@^@^C^@^@^@^E^@^@^@^D^@^@^@^G^@^@^@^@^Q^P^@&#65533;$
^@^@^@&#65533;^@^@^@^K^@^@^@^P^@^@^@^U^@^@^@^@^@^@^@^C^@^@^@d&#65533;^D^H^B^@^@^@^X^@^@^@^T^@$

I don't know but it looks weird to me....anyone got any suggestions?

---

### Post by heindsight on 2009-03-18
Well, that's an ELF (Executable and Linkable Format) binary file. ELF is the executable file format used by linux (and most other Unix-like operating systems).

Looking at the contents of a binary file like that, won't tell you much though. Besides, if you can open the file, then it's obviously not missing.

What exactly was the error message you got?

EDIT:
I should add, that it's generally a bad idea to open binary files like that in text editors. Not only will you not get any useful information by looking at the file contents, but if you were to accidentally modify and save the file, you'd break it...

---

### Post by ozguitarplayer on 2009-03-18
When I try to configure the file shareing properties of a folder I get a small window:

Run as root - KDE su
Command: kcmshell4 'fileshare'
Password:

I fill in the password and get another small window;

Sorry -KDE su
Command 'kcmshell4 'fileshare" not found

---

### Post by heindsight on 2009-03-18
It looks to me as if kcmshell4 is not on your PATH.
Try opening a terminal window and do:
```
which kcmshell4
```
If that doesn't produce any output, then kcmshell4 is not on your path.

I'm afraid I don't know much (anything) about KDE and where it puts various files or what the preferred method of running various KDE commands are. However, I suppose the solution to your problem would be to either add the directory containing kcmshell4 to your PATH or to create a symbolic link from a directory already on your PATH to kcmshell4.

---

### Post by ozguitarplayer on 2009-03-18
I get this which I guess is close to nothing..

nigel@ubu8:~$ which kcmshell4
nigel@ubu8:~$ 

..may I ask; how do I add the directory containing kcnshell4 to my PATH or create a symbolic link?

..and also..I'm running Hardy Heron as you are, is KDE to do with Kubuntu? 
..and if so why would I get KDE errors that stop me from file sharing?

---

### Post by heindsight on 2009-03-18
> **ozguitarplayer said:**
> I get this which I guess is close to nothing..

nigel@ubu8:~$ which kcmshell4
nigel@ubu8:~$ 

..may I ask; how do I add the directory containing kcnshell4 to my PATH or create a symbolic link?

..and also..I'm running Hardy Heron as you are, is KDE to do with Kubuntu? 
..and if so why would I get KDE errors that stop me from file sharing?

To add a directory to your PATH, you'll have to edit ~/.profile and add a line like:
```
export PATH="${PATH}:/directory/added/to/path
```
then log out and log back in again.

To create a symbolic link, open a terminal window and do:
```
cd /usr/local/bin
sudo ln -s /path/to/kcmshell4 kcmshell4
```
I /usr/local/bin should be on your PATH...

KDE is a desktop environment - the default desktop environment in Kubuntu (as opposed to GNOME which is the default in Ubuntu --- although it is also possible to have KDE installed on plain Ubuntu or GNOME installed on Kubuntu).

The reason you're getting errors is that you're trying to run an app that is not on your PATH without giving the full path to the app.

---

### Post by ozguitarplayer on 2009-03-18
thanks heinsight,
I tried the symbloic link option and got....

nigel@ubu8:~$ cd /usr/local/bin
nigel@ubu8:/usr/local/bin$ sudo ln -s /path/to/kcmshell4 kcmshell4
ln: creating symbolic link `kcmshell4': File exists
nigel@ubu8:/usr/local/bin$ 

was I to type in ~/.profile if so I got..
nigel@ubu8:~$ ~/.profile
bash: /home/nigel/.profile: Permission denied
nigel@ubu8:~$ 

tried add path to directory, I figured that I had to replace some info in that code line but didn't know exactly what to replace. I tried a couple of thing and only got
>
as a response (obviously I'm new to this)


Getting back to KDE...how would I have ended up with KDE instead of Gnome as my desktop environment? and can if it can be changed back to Gnome would it make things easier?
I've seen KDE and this desktop still looks like Gnome, I haven't installed
KDE on Gnome

---

### Post by heindsight on 2009-03-18
> **ozguitarplayer said:**
> thanks heinsight,
I tried the symbloic link option and got....

nigel@ubu8:~$ cd /usr/local/bin
nigel@ubu8:/usr/local/bin$ sudo ln -s /path/to/kcmshell4 kcmshell4
ln: creating symbolic link `kcmshell4': File exists
nigel@ubu8:/usr/local/bin$ 

Apparently /usr/local/bin/kcmshell4 already exists, which would seem to indicate that /usr/local/bin is not in your path. By the way, I should probably have mentioned before, you need to replace the /path/to/kcmshell4 in that command I gave with the actual path to kcmshell4 (from the title of this thread I guess that would be /usr/lib/kde4/bin/kcmshell4)

> **ozguitarplayer said:**
> 
was I to type in ~/.profile if so I got..
nigel@ubu8:~$ ~/.profile
bash: /home/nigel/.profile: Permission denied
nigel@ubu8:~$ 

tried add path to directory, I figured that I had to replace some info in that code line but didn't know exactly what to replace. I tried a couple of thing and only got
>
as a response (obviously I'm new to this)


You have to **edit** ~/.profile and add that line to it (yes you do have to modify it too, replace /directory/added/to/path with the actual directory you want to add to PATH).

Based on the error you got trying to create the symbolic link, I suspect all you need to do is add /usr/local/bin to your PATH, so do:
```
gedit ~/.profile
```
of course you can replace gedit with your favourite text editor.
Add the following line to the file:
```
export PATH="${PATH}:/usr/local/bin
```
Save the file, close the text editor, log out and log back in.
You should now be able to run kcmshell4 as you were originally trying to do.

> **ozguitarplayer said:**
> 
Getting back to KDE...how would I have ended up with KDE instead of Gnome as my desktop environment? and can if it can be changed back to Gnome would it make things easier?
I've seen KDE and this desktop still looks like Gnome, I haven't installed
KDE on Gnome

I've no idea how you could have ended up with KDE if you didn't install it yourself. Since kcmshell4 is a KDE4 app and since you have a directory like /usr/lib/kde4 I can only assume that you must have somehow installed KDE4 (or at least parts of it) at some point. The fact that you were trying run kcmshell4, using kdesu to set up your file sharing, just led me to assume that you were running KDE4...

To be honest, I don't know what KDE looks like. If you're running GNOME though, you'll find an entry "About Gnome" in the System menu. If you don't have that then maybe you are running KDE.

Regarding setting up file sharing (assuming you mean setting up Samba to share directories with windows machines), I'm afraid I don't really how to do it from either GNOME or KDE. I'm used do it manually by editing /etc/samba/smb.conf. You may want to have a look at this though: [uwiki]SettingUpSamba[/uwiki]

---

### Post by ozguitarplayer on 2009-03-18
If I was a bit more clever I would add a screen shot of this however..when I run that gedit opens with 

Could not open the file /usr/lib/kde4/bin/kcmshell4.
gedit has been unable to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

the character coding is Current Locale (UTF-8) and the only other option in the drop down box is Western ISO.
If gedit is unable to detect character coding could this have something to do with the jumble that I oroginally posted?

Definately in Gnome, any ideas why I'm dealing with kde issues?

---

### Post by heindsight on 2009-03-18
> **ozguitarplayer said:**
> If I was a bit more clever I would add a screen shot of this however..when I run that gedit opens with 

Could not open the file /usr/lib/kde4/bin/kcmshell4.
gedit has been unable to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

the character coding is Current Locale (UTF-8) and the only other option in the drop down box is Western ISO.
If gedit is unable to detect character coding could this have something to do with the jumble that I oroginally posted?


Once again, don't try to open a binary file with a text editor. If you want to add a directory (/usr/local/bin) to your PATH, then edit **~/.profile** and add a line like
```
export PATH="${PATH}:/usr/local/bin"
```

> **ozguitarplayer said:**
> Definately in Gnome, any ideas why I'm dealing with kde issues?
You're not having KDE issues so much as you're having issues with your PATH. You're trying to use KDE apps (which aren't in your PATH) to set up shared folders.

Since you're using GNOME, I don't understand why you're trying to use KDE apps for this anyway. Just follow the instructions in that link I posted before. I'd recommend reading the whole thing, but if you want to share directories using Samba, the most important part is:
> Ubuntu 8.04 And Later

For Ubuntu 8.04 (Hardy) and later, shared folders are created directly from the folder. Browse to the location of the folder you would like to share, right-click the folder, and choose Sharing Options. Click the Share this folder check box, and click Install Services. Enter your password, and the Samba server packages will be downloaded and installed.


---

### Post by ozguitarplayer on 2009-03-18
I'm getting out of my depth here..well have been for a while...I understood in your second last that reply that I was to edit it with an editor of my choice....

I don't know how to treat this...edit ~/.profile...it doesn't work in terminal and if I extented with /usr/lib/kde4/bin/kcmshell4 I get permission denied, and I'm not to use gedit....it's my lack of understanding that is the problem....you patience is
commendable

This all came about when I put Ubuntu 8.10 onto another pc and wanted to share files so I thought I had to go file>properties>share to be able to share....but thats where I'm told that kcmshell4 fileshare cannot be found

I've got windows on other computers and can share Ubunut-Windows-Ubuntu with Samba
It's Ubuntu-Ubuntu I need to setup..

---

### Post by heindsight on 2009-03-24
> **ozguitarplayer said:**
> I'm getting out of my depth here..well have been for a while...I understood in your second last that reply that I was to edit it with an editor of my choice....

I don't know how to treat this...edit ~/.profile...it doesn't work in terminal and if I extented with /usr/lib/kde4/bin/kcmshell4 I get permission denied, and I'm not to use gedit....it's my lack of understanding that is the problem....you patience is
commendable

Of course you can use gedit. I said "you can replace gedit with your favourite text editor." meaning that if you have some particular text editor that you prefer using (eg vi or nano) then you could use that instead of gedit.

Which editor you use is irrelevant, the point is that to modify your PATH environment variable, you should edit ~/.profile. 

> **ozguitarplayer said:**
> 
This all came about when I put Ubuntu 8.10 onto another pc and wanted to share files so I thought I had to go file>properties>share to be able to share....but thats where I'm told that kcmshell4 fileshare cannot be found

That's rather strange. I can only guess at why this could be happening. Perhaps you installed (and are using) some KDE based file browser (in GNOME) without having a full KDE installation. If this is the case, it may be that the KDE based file browser is trying to run kcmshell4 to configure sharing, but that doesn't work because you don't have a full KDE installation.

Try using the GNOME default, nautilus file browser by running (in a terminal or by pressing Alt+F2):
```
nautilus ~
```
then browse to the directory you want to share, right click and go to "Properties>Share"

> **ozguitarplayer said:**
> 
I've got windows on other computers and can share Ubunut-Windows-Ubuntu with Samba
It's Ubuntu-Ubuntu I need to setup..

If you already have your samba server set up and you can access your shares from a windows machine, then you shouldn't need to do anything more to be able to access them from an ubuntu machine.

---

### Post by ozguitarplayer on 2009-03-24
thanks heindsight,
since we last spoke re-read a lot of your replies and have managed to sort a number of issues, mostly to do with foolishness on my part.

I can open files that are on the second Ubuntu pc, howver I can't open files that are on the main Ubuntu pc from the second pc.
The files are recognized yet when I cilck to open them I get a small password window 
asking for...
Username   nigel       (already filled in but changable)
Domain     WORKGROUP   (already filled in but changable) 
Password               (empty) 

It doesn't matter what combimation of info I type in the window just reappears again
..so close yet still not happening.

I get confused at times with the word Windows does it refer to Microsoft or is it sometimes something else, which leads me to ask...
Is samba only needed when sharing with Windows (Microsoft) or is is needed for Ubuntu - Ubuntu sharing also?

---

### Post by heindsight on 2009-03-25
> **ozguitarplayer said:**
> thanks heindsight,
since we last spoke re-read a lot of your replies and have managed to sort a number of issues, mostly to do with foolishness on my part.

I can open files that are on the second Ubuntu pc, howver I can't open files that are on the main Ubuntu pc from the second pc.
The files are recognized yet when I cilck to open them I get a small password window 
asking for...
Username   nigel       (already filled in but changable)
Domain     WORKGROUP   (already filled in but changable) 
Password               (empty) 

It doesn't matter what combimation of info I type in the window just reappears again
..so close yet still not happening.

Unfortunately I don't have much experience connecting to shares that require a password, but you should be able to just give your normal username and password (the username/password combination you use on the machine you're connecting to).

> **ozguitarplayer said:**
> I get confused at times with the word Windows does it refer to Microsoft or is it sometimes something else, which leads me to ask...
Is samba only needed when sharing with Windows (Microsoft) or is is needed for Ubuntu - Ubuntu sharing also?

When I said "windows machine" i meant a machine running MS Windows yes. 
Samba is a free implementation of SMB/CIFS, the protocol used by MS Windows to share files and printers over a network. 

As far as I know, samba is the only option for allowing MS Windows machines access to files or printers on your Ubuntu machine.

Since Ubuntu comes with the samba client software installed by default, you can also use samba to share files and printers with other Ubuntu machines. This is probably the easiest option, especially if you already have samba set up to share with MS Windows machines. However, there are also various other options for allowing other Ubuntu machines access to  files or printers on an Ubuntu machine. For example, you can use CUPS to allow other Ubuntu machines access to your printer and you can use NFS (or any of a number of other network filesystems) to allow other Ubuntu machines access to files.

---

### Post by ozguitarplayer on 2009-03-25
Hey..I wasn't refering only to you re the windows word it's something I come across often, it just made me think that sometimes it refered to something else.....on the main Ubuntu pc I use my user and password to access the manin Ubuntu pc. On the second pc I try the user and password however without any luck, I cannot acces the main computer....keeps asking for the password

maybe I'll look at NFS..

---

### Post by heindsight on 2009-03-26
> **ozguitarplayer said:**
> on the main Ubuntu pc I use my user and password to access the manin Ubuntu pc. On the second pc I try the user and password however without any luck, I cannot acces the main computer....keeps asking for the password

Unfortunately I don't have any experience with password access to samba servers. I only use samba to provide read-only guest access (ie no password needed) to my music collection to everyone on my home lan.

I'm sure someone on these forums can help you to fix it though. Perhaps you should consider starting a new thread for this problem - authentication problems with samba are quite far removed from the original topic of this thread... ;)

> **ozguitarplayer said:**
> maybe I'll look at NFS..
I should just warn you that NFS is a bit more tricky to set up properly and work with than Samba. [uwiki]SettingUpNFSHowTo[/uwiki] gives quite a good howto for setting up NFS though.

---

### Post by ozguitarplayer on 2009-03-26
Hey, I started a new thread about 10 minutes before I recieved you email :-), didn't realise how far this one drifted off course...

Just to finish..can now access all folders..so things have come a long way..the only issue remaining is not being able to change permissions....

Thanks for all your help heinsight

---

