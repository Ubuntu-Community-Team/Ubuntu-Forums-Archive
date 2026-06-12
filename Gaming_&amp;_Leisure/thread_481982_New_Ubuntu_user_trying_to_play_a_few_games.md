---
title: "New Ubuntu user trying to play a few games"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Ratsock on 2007-06-23
Hi all,
I just finished installing Ubuntu this morning and am reasonably happy so far. Atm i've got a dual boot setup with windows XP and ubuntu on separate disks.

Was wondering if i am able to run Warcraft 3: Frozen Throne from inside ubuntu. The guides i've seen ask me to install it using wine then run it. However I already have it installed on my Windows partition. It would be great if I didn't have multiple copies of it sitting around on my system. I have already mounted the ntfs partition and can access the war3 installation directory. But when i attmept to run it i just get the war3 splash screen then a black screen.

Also I was wondering about playing on Battle.net since the battle.net entries are listed in the windows registry. How would ubuntu access those? could i export the registry in windows then import then using wine?

thanks in advance all :)

---

### Post by cisforcojo on 2007-06-23
You're going to have a hard time finding anyone who would recommend you run it off your Window's partition I think. It's generally not a good idea.

First, you'd need to install write support for your NTFS drive (be careful). Ubuntu doesn't enable write support to NTFS upon install for safety reasons.
Install ntfs-3g from Synaptic or:

```
sudo apt-get install ntfs-3g
```

I'm not sure if this includes ntfs-3g-config (if not, install that as well and run it)

War3 will run fine on Battle.net if installed locally in Ubuntu. You're right, you'd have problems accessing your XP registry from Ubuntu and I generally think it's a bad idea. You'll also need to find a NoCD crack as well. 


Anyone else with me on this? (To not try and run it off the XP partition???)

---

### Post by Afoot on 2007-06-23
Running something off a non-native filesystem is never something to recommend. Maybe it could work, but it could also not work (and fail miserably). If you have sufficient space left, I'd vote for you to copy it over to your fake windows drive (I did that).

---

### Post by Cappy on 2007-06-23
I've copied a game over to a NTFS and played it from there. I just made a symlink
```
ln -s targetdirectory newlinkname
```
and it didn't even realize anything changed.

---

### Post by Lord Illidan on 2007-06-23
Hmm, if you can't afford at least a gig of space, it's time to get a new drive. I'd run it on my native disk...it plays well on wine there.

---

### Post by Ratsock on 2007-06-24
Hi all,
Its working now. And Im running it off the ntfs partition.
The first problem was that warcraft's movies were causing some issues with starting up. I was just getting a black screen. So after deleting the Movies folder that fixed the problem.

When I tried to login to battle.net (i use a pvpgn gateway so i use w3l.exe) w3l.exe was unable to find war3.exe. This problem was solved via the following commands:

pushd "path-to-war3.exe"
wine w3l.exe -opengl
popd

Everything working great after this :)

---

### Post by jimminy_kriket on 2007-07-09
Good job, ive had success running starcraft off my windows partition without write ability's, i just cant create new profiles.

---

### Post by Jovec on 2007-07-09
> **Cappy said:**
> I've copied a game over to a NTFS and played it from there. I just made a symlink
```
ln -s targetdirectory newlinkname
```
and it didn't even realize anything changed.

Which game(s)?

LInux native games that share content resource with their windows versions are smart enough to write your preferences in your home dir while accessing (read-only) content via your symlink.  As has been said, emulation through wine where the game is going to try to write date (save games, prefs) into a NTFS partition isn't the best idea.  If space is a real concern and there will be numerous apps sharing space, you could have your windows boot/system drive on NTFS and make a fat32 partition for shared windows/Linux resources.

---

### Post by mafyoo on 2008-02-28
> **Ratsock said:**
> Hi all,
Its working now. And Im running it off the ntfs partition.
The first problem was that warcraft's movies were causing some issues with starting up. I was just getting a black screen. So after deleting the Movies folder that fixed the problem.

When I tried to login to battle.net (i use a pvpgn gateway so i use w3l.exe) w3l.exe was unable to find war3.exe. This problem was solved via the following commands:

pushd "path-to-war3.exe"
wine w3l.exe -opengl
popd

Everything working great after this :)

Hi, where do i enter those commands?

Thanks.

M.

---

