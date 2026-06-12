---
title: "Problems trying to patch a linux (non wine) install of UT2004"
date: 2007-01-28
forum: Gaming &amp; Leisure
---

### Post by Doctoxic on 2007-01-28
Hi

I have installed UT2004 with the linux sh installer from my DVD and it works fine on Edgy.

I have downloaded the linux patch "ut2004-lnxpatch3369-2.tar.bz2" but it doesn't come with any instructions on how (or where) to install it.

If i unzip it its just some folders which i copied to the UT2004 folder in my home directory - but this doesn't seem to make any difference - it still says its the old version

i have done a search of these forums and there were several that referred to patching but they all seemed to refer to copying stuff to /usr/local/games/ut2004 - but i don't have any UT2004 files at that location.

Any idea what i should be doing to install the patch?

many thanks

Doc

---

### Post by MetalMusicAddict on 2007-01-28
If you installed the game to your home folder (incorrect) thats where you will put the patched files.

**/usr/local/games/ut2004** Is where the game *should* get installed. Run the installer as root. Use **sudo** in front of the command. Thats also where the patched files will go.

---

### Post by Doctoxic on 2007-01-28
thanks MetalMusicAddict

ok - if all fails i will re-install

but if its just a question of copying files i don't understand why it didn't work when i extracted to the UT folder in my home folder - or should i have done something else?

Doc

---

### Post by Doctoxic on 2007-01-28
fixed it
i extracted the files and then copied them across, rather than extract them direct - not sure why this worked and an extract didn't......

are all the patchs/mods etc just a question of copying files to the UT2004 folder?

thanks

Doc

---

### Post by Doctoxic on 2007-01-28
another question

i am now trying to install Alien Swarm - i extraced and then copied the files to my UT dir but get these messages when trying to run it:

voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ ./Alien-Swarm-Linux
bash: ./Alien-Swarm-Linux: Permission denied
voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ sudo ./Alien-Swarm-Linux
Password:
sudo: ./Alien-Swarm-Linux: command not found
voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ 


it doesn't appear as a mod in the Community menu either - i assume this is a permission problem but it won't even run using sudo

what am i doing wrong here?

many thanks

Doc

---

### Post by perky on 2007-02-03
Linux needs files to have an executable flag for them to be able to run.

Try
```

chmod +x Alien-Swarm-Linux

```
Or if you prefer nautilus, right click on the file -> properties -> permissions -> tick "allow executing file as a program".

Hope it's something as simple as that!


> **Doctoxic said:**
> another question

i am now trying to install Alien Swarm - i extraced and then copied the files to my UT dir but get these messages when trying to run it:

voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ ./Alien-Swarm-Linux
bash: ./Alien-Swarm-Linux: Permission denied
voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ sudo ./Alien-Swarm-Linux
Password:
sudo: ./Alien-Swarm-Linux: command not found
voteslave@voteslave-desktop:~/ut2004/AlienSwarm$ 


it doesn't appear as a mod in the Community menu either - i assume this is a permission problem but it won't even run using sudo

what am i doing wrong here?

many thanks

Doc

---

### Post by xtc69 on 2009-04-27
plz help me im a noob to ubuntu  but im trying to lose windoes i have ut2004 all setup and im trying to patch it to 3396   i cant put the ut2004 as there a permission problem :( i have the patch on my desktop as well as ut2004.megapack-english-3.run  plz any 1 as i dont want to give up

---

### Post by Gillen on 2009-04-27
Hi,

The 3369.1 patch is here [http://files.filefront.com/UT2004+v33691+Linux+Hotfix+Patch/;4465771;/fileinfo.html](http://files.filefront.com/UT2004+v33691+Linux+Hotfix+Patch/;4465771;/fileinfo.html) The Megapack is here [http://0day.icculus.org/ut2004/ut2004megapack-linux.tar.bz2](http://0day.icculus.org/ut2004/ut2004megapack-linux.tar.bz2) I am not sure if the mega pack contains 3369.1.
It is probably not the Linux way but I always installed the game in my home directory /home/name/Games/ut2004 I then extract the above archives to my desktop them move them into my ut2004 folder (Megapack first), merge and replace. 
3369.1 was the last Linux patch I think 3369.2 is for the Mac.

Hope this helps.

Steven.

---

### Post by PureLoneWolf on 2009-06-12
Something that could be useful for patching in the future.

[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

The link contains a .run file for various mods and patches (including the megapack) - No hassles and worked first time for me

Might be useful to others

---

### Post by u235sentinel on 2009-06-12
I had the same problem with upgrading the game until I realized I needed top just copy the files over my install.  It was somewhere under /usr/local I think and after copying everything over I was good to go.

I've noticed 3369 is FAR more stable and I've played for many hours online.  Great game guys.  Now if only UT3 would come out then I'd buy it :D

---

