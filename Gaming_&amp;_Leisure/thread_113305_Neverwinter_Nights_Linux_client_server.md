---
title: "Neverwinter Nights Linux client server"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by catalytic on 2006-01-06
Hi there I'm new to linux and I have just installed the neverwinter linux client as per the instruction on the bioware site [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html).

I can't get it to work. Can somone please explain how I run the game? Do I need a previous installation of the game or is the linux client the full game??

Alternatively could someone suggest a game with the same specifications that will work for me?

Thanks

---

### Post by kaamos on 2006-01-06
If you followed the instructions on the site, then you have the full game.

You run the game with "./nwn" when in the directory where you installed it to. I also suggest you do this (this is assuming you installed to /home/username/games/nwn, change path to yours.)
```
cd /home/username/games
chmod +rx nwn -R
```
This fixes the permission proplems the game often has.

---

### Post by catalytic on 2006-01-06
I'm logged in as root, I created a seperate directory for NWN.

So do I move them to a different place then try that command?

Sorry this is all totally new to me..

---

### Post by catalytic on 2006-01-06
[QUOTE=kaamos]If you followed the instructions on the site, then you have the full game.

You run the game with "./nwn" when in the directory where you installed it to. I also suggest you do this (this is assuming you installed to /home/username/games/nwn, change path to yours.)
```
cd /home/username/games
chmod +rx nwn -R
```
This fixes the permission proplems the game often has.[/QUOTE]
I moved the files to suggested directory and this is what I get
No such file or directory

OK I deleted what I did and I'll start again... I have the nwresources129.tar.gz nwclient129.tar.gz English_linuxclient166_orig.tar.gz 

Where am I meant to extract them to?

Thanks

---

### Post by kaamos on 2006-01-06
I don't think running nwn as root will work. And I hope youre not logged in as root in gnome! ;) 

Just log in with a user account and adjust the paths according to your install. Like this (also owns the files to user):
```

sudo chown user:user /where/you/installed/nwn -R
sudo chmod +rx /where/you/installed/nwn -R

```
user = your username
/where/you/installed/nwn = path to you nwn directory

---

### Post by leech on 2006-01-06
[http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

Here's this Howto for the Platinum edition.  Which version of Neverwinter Nights do you have?

Leech

---

### Post by catalytic on 2006-01-06
[QUOTE=leech][http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

Here's this Howto for the Platinum edition.  Which version of Neverwinter Nights do you have?

Leech[/QUOTE]
I'm installing the Linux client.

---

### Post by catalytic on 2006-01-06
I have extracted the resource and client files to /home/username/NWN

It says I have to run the install file, it won't run. I have tried running through the terminal, but I don't know what command it is.

I have tried :

run fixinstall

sh fixinstall

sudo apt-get

This is what I get when I type in run ./nwn
bash: run: command not found


sudo dpkg -i

Can someone please help me? I'm sorry if this is a dumb question, but I'm totally new to linux.

---

### Post by leech on 2006-01-07
[QUOTE=catalytic]I'm installing the Linux client.[/QUOTE]

I know that, my question was which edition of the game are you trying to install.  There is the original version, and then two expansion packs separate, then there is a Gold edition (which has the original and the Shadows of Undertide) and then there is the Platinum which has the Shadows of undertide and Hordes of the underdark, and this is the HOWTO that I wrote.  The newest version is the Diamond edition, which has all of the Platinum edition and the Kingmaker module.

Unfortunately for the Diamond edition, the Kingmaker module can't be installed in Linux.  If you have the Platinum, follow my Howto, if you have any of the other versions, Ravage has created installers for them.  [http://www.icculus.org/~ravage/](http://www.icculus.org/~ravage/)

Leech

---

### Post by catalytic on 2006-01-08
The linux client, I don't have a cd of the game. I grabbed the original update. This is the file I downloaded to install the game is nwclient129.tar.gz

---

### Post by impact201 on 2006-01-08
Not meaning to hijack your thread, but I figured it would be best to keep the NWN questions together.

I did the same thing as you, downloading the resources/binaries/1.66 update from bioware.  I'm pretty sure I managed to get everything installed right.  I also did the chmod on nwn to fix permissions, and ran fixinstall.

I'm not sure what info I might need to post, as I'm a linux newbie also :)  Just installed  Ubuntu yesterday.  But here is the message I am getting:

```
jason@jason:~/nwn$ ./nwn
./nwmain: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory
jason@jason:~/nwn$

```

I managed to locate that file in /usr/lib, and it turns out to be a link to shared library libXxf86vm.so.1.0.0, and I don't have user access to either one.  I also tried sudo ./nwn instead, with the same error message.

Any suggestions?  Thanks!

---

### Post by leech on 2006-01-09
Try running 'sudo dpkg-reconfigure libxxf86vm1' from a terminal.  That's really quite strange.  Never heard of that one before.

You could also tell us what 'ls -l /usr/lib/libXxf86vm.so.1.0.0' shows us.

Leech

---

### Post by impact201 on 2006-01-09
I tried the reconfigure...didn't seem to help at all.  Same error message as before.

Here's the result of what you asked for:

```
jason@jason:~/nwn$ sudo dpkg-reconfigure libXxf86vm1
jason@jason:~/nwn$ ./nwn
./nwmain: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory
jason@jason:~/nwn$ ls -l /usr/lib/libXxf86vm.so.1.0.0
-rwxrwxrwx  1 root root 20032 2005-07-24 08:46 /usr/lib/libXxf86vm.so.1.0.0
jason@jason:~/nwn$ ls -l /usr/lib/libXxf86vm.so.1
lrwxrwxrwx  1 root root 19 2006-01-07 11:56 /usr/lib/libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
jason@jason:~/nwn$

```

On another note, I tried using the Howto for NWN Platinum edition (which is what I have) that I found on the forum (and now see in your sig, heh), to install using the provided CD's.  It was working okay, until it came time to switch from disk 2 to disk 3.  My CD-ROM drive was locked, and the system would not release it.  Even after closing the terminal that was running the script.  I could not open my CD drive until after a reboot, so I decided to download the 1.1GB resource file from Bioware and try my luck with their method.

I'm in no rush really, so am more than happy to try getting this fixed step by step.  :)  If nothing else, it should provide me a better knowledge of my new Linux system.

---

### Post by akurashy on 2006-01-09
im going to be playing online soon on it (im going to be ordering neverwinter nights gold edition ) im playing the isos, which im just following the quests (mostly entertainming i say)

---

### Post by leech on 2006-01-09
[QUOTE=impact201]I tried the reconfigure...didn't seem to help at all.  Same error message as before.

Here's the result of what you asked for:

```
jason@jason:~/nwn$ sudo dpkg-reconfigure libXxf86vm1
jason@jason:~/nwn$ ./nwn
./nwmain: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory
jason@jason:~/nwn$ ls -l /usr/lib/libXxf86vm.so.1.0.0
-rwxrwxrwx  1 root root 20032 2005-07-24 08:46 /usr/lib/libXxf86vm.so.1.0.0
jason@jason:~/nwn$ ls -l /usr/lib/libXxf86vm.so.1
lrwxrwxrwx  1 root root 19 2006-01-07 11:56 /usr/lib/libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
jason@jason:~/nwn$

```

On another note, I tried using the Howto for NWN Platinum edition (which is what I have) that I found on the forum (and now see in your sig, heh), to install using the provided CD's.  It was working okay, until it came time to switch from disk 2 to disk 3.  My CD-ROM drive was locked, and the system would not release it.  Even after closing the terminal that was running the script.  I could not open my CD drive until after a reboot, so I decided to download the 1.1GB resource file from Bioware and try my luck with their method.

I'm in no rush really, so am more than happy to try getting this fixed step by step.  :)  If nothing else, it should provide me a better knowledge of my new Linux system.[/QUOTE]

Nautilus should automount the disks, and if you're not in /media/cdrom in your terminal that you're running the script from, you should be able to just right click on the icon on your desktop and select eject.  I'm guessing that Nautilus is just locking the disk in your drive.  Possibly something to add to the howto.

Leech

---

### Post by leech on 2006-01-09
[QUOTE=akurashy]im going to be playing online soon on it (im going to be ordering neverwinter nights gold edition ) im playing the isos, which im just following the quests (mostly entertainming i say)[/QUOTE]

I think the Gold and Platinum are about the same price, aren't they?  If that is the case, I would definitely order the Platinum.  It comes with a nice manual and the Diamond edition comes with the Kingmaker that doesn't currently work in Linux (unless you order it from the store).

The Gold edition only has the Shadows of Undertide and the original Campaign.  The Platinum comes with the Original, SoU and Hordes of the Underdark.

Leech

---

### Post by akurashy on 2006-01-09
Good news folks, bought my copy today

[FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]  Quantity : 1 [/FONT][/COLOR][/FONT]    [FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]Product  Number : 001NEVG[/FONT][/COLOR][/FONT]    [FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]Product  : Neverwinter Nights Gold[/FONT][/COLOR][/FONT]    [FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]Price  Each : $19.90[/FONT][/COLOR][/FONT]    [FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]Discount  : 0.00%[/FONT][/COLOR][/FONT]    [FONT=Arial, Helvetica, sans-serif][COLOR=#000000][FONT=Arial]Total  : $19.90[/FONT][/COLOR][/FONT]
D: i will be playing online soon :)

Leech - I wish i was a money machine, but i just need the original and SoU :)i can get hordes later :)

---

### Post by leech on 2006-01-09
No problem wasn't quite sure how much the Gold was selling for.  So the price breaks down like so...

Gold $20
Diamond $30
Platinum $40

I hear ya about the money thing....  I've been unemployed for far too long.....

Leech

---

### Post by akurashy on 2006-01-09
[quote=leech]No problem wasn't quite sure how much the Gold was selling for.  So the price breaks down like so...

Gold $20
Diamond $30
Platinum $40

I hear ya about the money thing....  I've been unemployed for far too long.....

Leech[/quote]

well im 17, so.. im not even employed lol @_@

---

