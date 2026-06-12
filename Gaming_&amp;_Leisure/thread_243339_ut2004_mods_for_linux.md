---
title: "ut2004 mods for linux?"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by ezek on 2006-08-24
hey, im going to buy ut2004 for linux off of tuxgames.com because i cant find any in stores and i was wondering if all of the mods work for linux. thanks for all the help.:biggrin:

---

### Post by Perfect Storm on 2006-08-25
Check: [http://doc.gwos.org/index.php/Unreal_Tournament_2004_Expansions](http://doc.gwos.org/index.php/Unreal_Tournament_2004_Expansions)

and 
here: [http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11](http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11)

---

### Post by Relic2K on 2006-08-25
The link below is the best link for Native Linux Gaming and UT2004 MODS;
[http://liflg.org/?catid=6](http://liflg.org/?catid=6)

I will warn you though, sometimes they get careless when they are making their installers and it ends up braking the game/mods (it has happened to me) you may want to check the forums first to see which UT2004 MODS people have been having problems with !! I use to make my own installers so I do know what I am talking about. Stay away from the ones that have reported probles. I Just installed the "StrikeForce" MOD last night and that one was okay. The other ones I can't speak for.

---

### Post by stuart.crouch on 2006-08-29
Does anyone have a guide for getting a mod working in linux ut2004?

Im trying to get the mod I wrote a while ago up and running (trying to move away from windows), and I just copied everything from my windows partition to /usr/local/games/ut2004

The mod is Action Unreal Tournament (not many websites left covering it now, just a forum really).  It installs to /Action, so I thought it would be as simple as just moving the files from /Action to the linux partition.

When I enter ut2004 -mod Action on the command line, the default ut2004 loads, and I dont see any mod information anywhere.

Anyone got any suggestions?

Thanks in advance
--
Stuart "Payback" Crouch

---

### Post by justin whitaker on 2006-08-29
> **stuart.crouch said:**
> Does anyone have a guide for getting a mod working in linux ut2004?

Im trying to get the mod I wrote a while ago up and running (trying to move away from windows), and I just copied everything from my windows partition to /usr/local/games/ut2004

The mod is Action Unreal Tournament (not many websites left covering it now, just a forum really).  It installs to /Action, so I thought it would be as simple as just moving the files from /Action to the linux partition.

When I enter ut2004 -mod Action on the command line, the default ut2004 loads, and I dont see any mod information anywhere.

Anyone got any suggestions?

Thanks in advance
--
Stuart "Payback" Crouch


What are the folders underneath /Action? 

Some mods launch via the -mod (Mod name) command, others have to be activated via the Community Tab. I can't remember if Action is one of those or not.

---

### Post by stuart.crouch on 2006-08-29
I just got the mod to work by using sudo :D:D:D

So Im now 100% certain its a permissions/ownership problem from copying the files off my windows partition.  Can you help me set this up so that I can launch the mod without using sudo?

This is the contents of the ut2004 directory

```

drw-rw-rw- 18 stuart root      4096 2006-08-29 21:15 Action
drwxr-xr-x  2 root   root      4096 2006-08-27 22:49 Animations
drwxr-xr-x  6 root   root      4096 2006-08-26 19:05 Benchmark
drwxr-xr-x  2 root   root      4096 2006-08-26 19:05 ForceFeedback
drwxr-xr-x  2 root   root      4096 2006-08-27 22:49 Help
drwxr-xr-x  2 root   root      4096 2006-08-26 19:05 KarmaData
drwxr-xr-x  2 root   root      4096 2006-08-26 19:05 Manual
drwxr-xr-x  2 root   root      4096 2006-08-27 22:50 Maps
drwxr-xr-x  2 root   root      4096 2006-08-27 22:50 Music
-rw-r--r--  1 root   root   9093246 2006-08-26 19:07 openal_sources.tar.bz2
-rw-r--r--  1 root   root     12391 2006-08-26 19:07 README.linux
-rw-r--r--  1 root   root   2836567 2006-08-26 19:07 sdl12_sources.tar.bz2
drwxr-xr-x  2 root   root      4096 2006-08-27 22:50 Sounds
drwxr-xr-x  2 stuart stuart    4096 2005-11-23 21:57 Speech
drwxr-xr-x  2 root   root      8192 2006-08-27 22:50 StaticMeshes
drwxr-xr-x  3 root   root     24576 2006-08-27 22:50 System
drwxr-xr-x  2 root   root     12288 2006-08-27 22:50 Textures
-rwxr-xr-x  1 root   root      1266 2006-08-26 19:07 uninstall
-rwxr-xr-x  1 root   root      1251 2006-08-26 19:01 ut2004
-rw-r--r--  1 root   root     16223 2006-08-26 19:07 UT2004_EULA.txt
-rw-r--r--  1 root   root     20694 2006-08-26 19:01 ut2004.xpm
drwxr-xr-x  5 root   root      4096 2006-08-26 19:05 Web

```

If I try to view the Action directory I get this

```

stuart@stuart-desktop:/usr/local/games/ut2004$ cd Action
bash: cd: Action: Permission denied

```

as root (sudo su) I can see that everything is there

```

drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 Animations
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autBreakables
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autEffects
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autEngine
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autGame
-rw-rw-rw- 1 stuart root 63286 2006-08-27 23:15 aut.ico
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autInterface
-rw-rw-rw- 1 stuart root  2012 2006-08-27 23:15 aut patch change log.txt
drw-rw-rw- 4 stuart root  4096 2006-08-27 23:15 autWeapons
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 Help
drw-rw-rw- 3 stuart root  4096 2006-08-27 23:15 manual
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 Maps
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 music
-rw-rw-rw- 1 stuart root  9478 2006-08-27 23:15 Readme.txt
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 Sounds
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:15 StaticMeshes
drw-rw-rw- 2 stuart root  4096 2006-08-29 21:12 System
drw-rw-rw- 2 stuart root  4096 2006-08-27 23:16 Textures
-rw-rw-rw- 1 stuart root   196 2006-08-27 23:16 UT2K4Mod.ini

```

The action directory has my name on it because I tried to chown it to me in the hopes that would make it work.  It didnt :(

Any help would be greatly appreciated

---

### Post by stuart.crouch on 2006-08-30
Someone is having the same problems with SAS. I've linked to the thread incase it gets resolved there rather than here.

[http://www.ubuntuforums.org/showthread.php?p=1440251](http://www.ubuntuforums.org/showthread.php?p=1440251)

---

### Post by crane on 2006-08-30
Do you have anyother mods working? You could try putting the mod in your home directory.
~.ut2004.
 Just a suggestion.
 Also make sure you have all the patches installed as well.
[Ubuntu Gamers Arena UT2004 How-to]("http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63")

 I think I have a couple of mods intalled on mine. I will check it out when I get home today.

---

### Post by justin whitaker on 2006-08-30
> **stuart.crouch said:**
> When I enter ut2004 -mod Action on the command line, the default ut2004 loads, and I dont see any mod information anywhere.

Stuart, I was looking at Killing Floor last night, and the linux command code to start is:

ut2004 -mod-KF.

Try -mod-Action and see what happens.

---

### Post by stuart.crouch on 2006-08-31
Hi, as I said. The mod works, but only if I run it as sudo.

So ut2004 -mod=Action **doesnt** work (bad mod is the returned message)
sudo ut2004 -mod=Action _DOES_ work

The problem isnt the mod, its the permissions that have been given to the directories and files (I assume because I copied the project from my windows partition).

Others have suggested I "re-install" the mod, which Im sure would fix everything except for one thing... This mod is one that I've been writing, there is no installer and the only way to install it on linux is to copy it from windows :)

You can see the dilema Im in :(.  I'll try putting the mod in ~/ut2004/Action tonight and see if that works - although it seems an odd solution as the game itself works without being in a home directory.

If you have any suggestions on how to sort the permissions out then I'd be greatful.

---

### Post by justin whitaker on 2006-08-31
> **stuart.crouch said:**
> The problem isnt the mod, its the permissions that have been given to the directories and files (I assume because I copied the project from my windows partition).


That's right. I've copied things over from an NTFS drive, and the permissions were set to root by default. I had to login as root and change the permissions (you can do this through terminal, or actually login as root...up to you). Annoying.

> Others have suggested I "re-install" the mod, which Im sure would fix everything except for one thing... This mod is one that I've been writing, there is no installer and the only way to install it on linux is to copy it from windows :)

You have been writing it? Cool! I played around with the Action mod a while back, but I thought development had stopped....

> You can see the dilema Im in :(.  I'll try putting the mod in ~/ut2004/Action tonight and see if that works - although it seems an odd solution as the game itself works without being in a home directory.

You might not be able to change the location without changing the permissions on the folder. A vicious circle, to be sure. 

I would set your system to allow login as root, if you haven't already, and change permissions on the folder recursively (that is, all access to the folder as well as all subfolders and files).

---

### Post by stuart.crouch on 2006-08-31
Yes, officially development on AUT has stopped, but there were always things some of us werent happy with.  One of the other devs made some changes, such as knives sticking in walls and being picked up when touched. I've just been tweaking it to do some of the things I wanted but never had time, and fix bugs (again because I didnt have time to track them down).  

I doubt there will be any more graphical/image related stuff but small things like proper bullet penetration, grenades exploding when you kill the holder and a better mixed akimbo system are all possible via code.

Hopefully I'll get it all up and running tonight and then come back to ask the next question - How do I link my ut2004 directory to a directory in wine (so I dont have to have two copys of UT installed).  Linux, its powerful but only if you know how to use it :(

---

### Post by tr4veler on 2006-08-31
sudo chmod -R a+rwx Action 

Should do what you need.

Note: that gives all users read write and execute permissions for everything in and under that directory.

ln -s [wine directory] [linux directory]

---

### Post by stuart.crouch on 2006-09-04
Ahah, thanks.

I did the chmod thing but didnt give execute permissions - my logic was not to give execute permissions because the mod doesnt need to execute anything, the ut2004 is what gets executed.

Unfortunatly, linux needs execute permissions to do any sort of searching or browsing on a directory - which is why "bad mod" was coming up.  As soon as I added +x all was good with the world and I spent the weekend just playing AUT.

Thanks for the link thing, Im installing wotgreal now and I'll have a go at compiling later :D

---

### Post by tr4veler on 2006-09-04
Glad to hear it worked.  I'm not sure the link command I listed will do what you want but it's a place to start.

---

