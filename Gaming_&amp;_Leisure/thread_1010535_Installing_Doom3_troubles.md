---
title: "Installing Doom3 troubles"
date: 2008-12-13
forum: Gaming &amp; Leisure
---

### Post by GreenwoodGuy65 on 2008-12-13
Hi all

I am a noob Ubuntu user and want to try out Doom3. I have read the thread here on installing Doom3 but have come across this error

bladerunner@bladerunner-desktop:~/Desktop$ sudo sh doom3-linux-1.3.1.1304.x86.run
Verifying archive integrity... All good.
Uncompressing DOOM 3.............................................................................................
./setup.sh: 279: /home/bladerunner/.setup7277: not found
./setup.sh: 290: /home/bladerunner/.setup7277: not found

I don't know what the last two lines mean. 

Any help would be great!

Thanks!

---

### Post by linuxguymarshall on 2008-12-13
I wrote the article you talked about and I have to ask one thing


[LIST=1]
[*]Did you try the scripts?
[/LIST]

---

### Post by tommcd on 2008-12-14
Download doom3-linux-1.3.1.1304.x86.run from here:
[ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)
and run it with sudo.
It will install to /usr/local/games with a symlink to /usr/bin so you can run the game. Then just copy all the pk4 files from the Doom3 install CDs to /usr/local/games/doom3/base. You can the run "doom3" from terminal to play the game.
You could also run the Doom3 install script without sudo to install it to your /home directory. Then just copy the pk4 files to the ~/doom3/base directory.

---

### Post by linuxguymarshall on 2008-12-14
> **tommcd said:**
> Download doom3-linux-1.3.1.1304.x86.run from here:
[ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)
and run it with sudo.
It will install to /usr/local/games with a symlink to /usr/bin so you can run the game. Then just copy all the pk4 files from the Doom3 install CDs to /usr/local/games/doom3/base. You can the run "doom3" from terminal to play the game.
You could also run the Doom3 install script without sudo to install it to your /home directory. Then just copy the pk4 files to the ~/doom3/base directory.

You don't need to copy ALL the pk4 (3s?) to the directory. Only the listed ones.

---

### Post by GreenwoodGuy65 on 2008-12-14
I have the latest linux binary downloaded from the ID ftp server. I don't understand what these two lines mean

./setup.sh: 279: /home/bladerunner/.setup7277: not found
./setup.sh: 290: /home/bladerunner/.setup7277: not found

Is the bin file I downloaded corrupted or am I missing something else?

Thanks

---

### Post by GreenwoodGuy65 on 2008-12-14
I have the latest linux binary downloaded from the ID ftp server. I don't understand what these two lines mean

./setup.sh: 279: /home/bladerunner/.setup7277: not found
./setup.sh: 290: /home/bladerunner/.setup7277: not found

Is the bin file I downloaded corrupted or am I missing something else?

Thanks

---

### Post by GreenwoodGuy65 on 2008-12-14
Opps, sorry about that double reply!

---

### Post by linuxguymarshall on 2008-12-14
It means that the folder does not exist.

Try the scripts 

[https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)


First section

---

### Post by GreenwoodGuy65 on 2008-12-16
I ran the script and the install seemed to go okay, until I was asked to insert Disk 2 and run the second script. It didn't do anything and I looked at the terminal window and it was stating something about one of the pak files.

I tried a few times and then tried to run the .run file from terminal and this time the installer ran no problem! Not sure why it didn't run the first time I tried it, though it may have something to do with the fact that I know NOTHING about Linux/Ubuntu!

The install went fine, the only problem I have now, and with all the games installed, is that there is no sound, although when I tried an audio disk, I was able to play it no problem.

Any ideas why I have no audio in any of games, besides Doom3?

Thanks!

---

### Post by tommcd on 2008-12-17
> **GreenwoodGuy65 said:**
> 
The install went fine, the only problem I have now, and with all the games installed, is that there is no sound, although when I tried an audio disk, I was able to play it no problem.
Any ideas why I have no audio in any of games, besides Doom3?


Try closing all other programs that may use sound, including firefox. 
Go through the configuration in the Doom3 game and try the different options for sound until you get one that works. If I remember correctly, you need to use OSS instead of ALSA in Doom3. 
Try launching Doom3 from the terminal like this:
```
doom3 +set s_driver oss
``` 
or as explained [here]("https://help.ubuntu.com/community/Doom3")
```
doom3  +set s_driver oss +set s_numberOfSpeakers 2
```
It has been a few Ubuntu versions since I installed Doom3, but if I remember correctly, I sometimes had to close out of the game and run:
```
killall esd
```
to get the sound going in Doom3. I'm not sure if this still applies with the new pulse audio though. So try the other options first.

---

### Post by GreenwoodGuy65 on 2008-12-17
Thanks,

I will try that and see if it works

---

