---
title: "How do I uninstall America's Army?"
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by user1397 on 2006-08-13
the title says it all...

---

### Post by user1397 on 2006-08-13
friendly bump

---

### Post by searayman on 2006-08-13
i cant help you, but i was woundering if you could help me? DOse punkbuster work on AA in ubuntu? CAuse hten i try to play punkuster dosent really install its updates.

---

### Post by user1397 on 2006-08-13
> **searayman said:**
> i cant help you, but i was woundering if you could help me? DOse punkbuster work on AA in ubuntu? CAuse hten i try to play punkuster dosent really install its updates.sorry man, but i don't even know what punkbuster is...

---

### Post by samureye on 2006-08-13
Punkbuster ensures nobody cheats, not so?

---

### Post by Pathfinder_ on 2006-08-13
To uninstall AA you have to run the uninstall script. To do this, in terminal go to your americas army folder and then uninstall it using this:
```

sh uninstall
```

@searayman

Yes, it does work, but I think it needs write permissions to the AA folder in  order to work. if you have AA instaled in other directory then your home then this might be a problem. (I think, but I'm not sure)

---

### Post by user1397 on 2006-08-13
> **Pathfinder_ said:**
> To uninstall AA you have to run the uninstall script. To do this, in terminal go to your americas army folder and then uninstall it using this:
```

sh uninstall
``` 
@searayman

Yes, it does work, but I think it needs write permissions to the AA folder in  order to work. if you have AA instaled in other directory then your home then this might be a problem. (I think, but I'm not sure)hmm i installed AA by using the command ```
sudo sh ./armyops250linux.run
``` and i was in /home/erik/Desktop/downloads.  so does that mean that the uninstall script's gonna be there?  (im not in my ubuntu partition right now, im on windows)

---

### Post by Pathfinder_ on 2006-08-14
the uninstall script is in your ArmyOps folder.

---

### Post by Gustav on 2006-08-14
The ArmyOps folder is probably somewhere in /usr/local/ It's not a big folder so it should not be hard to find (if it is there :)).

---

### Post by prigodan on 2006-10-27
Hi there,
when i try to uninstall AA i receive this msg:
Could not find a usable uninstall program. Aborting.:o 

Im tring with the command "sh uninstall" from this folder /usr/local/games/armyops/
](*,) 
tnx

---

### Post by user1397 on 2006-10-27
> **prigodan said:**
> Hi there,
when i try to uninstall AA i receive this msg:
Could not find a usable uninstall program. Aborting.:o 

Im tring with the command "sh uninstall" from this folder /usr/local/games/armyops/
](*,) 
tnxhave you tried **sudo sh uninstall** ??  maybe that sudo will make it work.

---

### Post by btrotter on 2006-10-30
I had this same problem and finally figured it out.

I did this:

su
[type root password]
./uninstall

I guess a sudo wasnt good enough.

*********Screen capture********

user7@computer5:/usr/local/games$ su root
Password: 

root@computer5:/usr/local/games/armyops# ./uninstall 
Product: America's Army: Operations
Installed in /usr/local/games/armyops
/usr/local/games/armyops : Is a directory
America's Army: Operations has been successfully uninstalled.

---

### Post by MikeDK on 2007-03-03
well not workin on my install, I accidently choose the Software-driver instead og OpenGL and the game will not start up, and now i have to uninstall it for it to be reinstalled, cant find the settings in the .ini file to set it back to OpenGL

Regards MikeDK AKA [T-DK]B4D4SS^V in AA

---

### Post by felipeim on 2007-09-15
I did:

sudo su
[root password]
./uninstall

Then:

locate armyops

And:

sudo rm -r /home/user/.armyops/ (in my case /home/felipe/.armyops/, in your case command "locate" can find another folder with files of the game installation)

---

### Post by goaferdan on 2007-10-14
> **btrotter said:**
> I had this same problem and finally figured it out.

I did this:

su
[type root password]
./uninstall

I guess a sudo wasnt good enough.

*********Screen capture********

user7@computer5:/usr/local/games$ su root
Password: 

root@computer5:/usr/local/games/armyops# ./uninstall 
Product: America's Army: Operations
Installed in /usr/local/games/armyops
/usr/local/games/armyops : Is a directory
America's Army: Operations has been successfully uninstalled.

Thanks btrotter!

This suggestion fixed my prob.

---

### Post by Tim0miT on 2008-03-23
thanks felipeim, fixed my problem, that was a sh*t game!


just going to stick with CSS:)

---

### Post by Orion13622 on 2008-03-27
Yeah I basically trashed the folder and files as well because the ./uninstall command wasn't working for me either, and I had version 1.7.0 for Linux.  Graphics were ok, but you can't contact any servers, and it even locked up from time to time.  No thanks, would rather stick to CSS like you, or play something else.  

-- Orion

---

### Post by Orion13622 on 2008-03-27
Many thanks for helping those of us now getting into the Linux Community.  You're words of wizdom helped greatly!  Especially since the command line is a new experience compared to MS-DOS or Windoze.

Again, thanks brother!

---

### Post by tuathan on 2009-07-10
i had this same problem. When i tried to uninstall by navigating to the directory and  trying to uninstall using the uninstall script it would say: 
Could not find a usable uninstall program. Aborting.

Turns out that since i was using bash i first had to > sudo sh  then > su and finally >  ./uninstall.

The program is uninstalled sucessfully:

Product: America's Army: Operations
Installed in /usr/local/games/armyops
/usr/local/games/armyops : Is a directory
America's Army: Operations has been successfully uninstalled.

---

### Post by DarthZimmeris on 2009-07-16
Thanks, this worked for me.    :D

---

### Post by SNOOPY817 on 2009-08-18
i still dont get it

---

### Post by Applelnx on 2009-09-06
Hi, I cannot login with su. I never created any other user than mine when I first installed Ubuntu. I've always used the same password for all. Can somebody help me?

---

### Post by surfed on 2009-09-06
sudo <command> with your user password is all i can say

---

