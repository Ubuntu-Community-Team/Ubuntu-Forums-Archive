---
title: "[SOLVED] Enemy Territory"
date: 2008-03-10
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-10
Hi,
I recently downloaded ET.
It starts without a problem.
I try to go online.
There is a big list of servers that show up. I clicked on a few but everyone I tried it eventually quit out of ET by itself.

Any suggestions?

---

### Post by almostlinux on 2008-03-10
Make sure you have the latest version of et: 2.60b

---

### Post by Rytron on 2008-03-11
Hi,
I have this one:
et-linux-2.60.x86.run

---

### Post by almostlinux on 2008-03-12
You need the 2.60b patch on top of it. Google for it.

Once done, update your punkbuster.

I'm at work .. can't access gaming websites. If you have trouble finding the patch let me know.

---

### Post by Rytron on 2008-03-12
Ok, I just got this: [http://games.softpedia.com/get/Patch/Wolfenstein-Enemy-Territory-Patch.shtml]("http://games.softpedia.com/get/Patch/Wolfenstein-Enemy-Territory-Patch.shtml")
I'm not sure how to apply it though.

---

### Post by Rytron on 2008-03-13
ET
Hi I got online in the end. I think the problem was simply I had choose a server that was password protected. I put on the patch anyway though - I went onto terminal

```
sudo nautilus
```

then I put the ET patch into the Linux folder it came with and put this folder into /usr/local/games/enemy-territory

Also how do you give medical attention in ET?
What is a fireteam?
Why is it that there are some servers that do not require you to download a file while there are others that do. Is there a filter / method to only show servers that you can get straight into the action?

I now know that the problem was not the lack of a patch but picking the incorrect servers. The joys of trial and error.

---

### Post by ShodanjoDM on 2008-03-13
> **Rytron said:**
> 
Also how do you give medical attention in ET?
What is a fireteam?
Why is it that there are some servers that do not require you to download a file while there are others that do. Is there a filter / method to only show servers that you can get straight into the action?

1. Medical attention: you can play as a medic that can heal other team mates and himself. Or if you're playing as others, there are usually few places in every map where you can find ammo and medic stacks.

2. Fireteam: AFAIK it's a "team inside team" supposedly to be commanded by a player who will give instructions to his team members. I haven't played as a fireteam member yet, though.

3. There are numerous mods and addons for this game. From sounds/costumes mods to weapons, new maps, game balancing etc. Not every servers require specific mod to run as there are also few servers with "stock" map set, standard weapons etc. If you join a server that has a specific mod installed, you have to download the mod also. But it's usually done automatically.

And yes, there are filters on the server list screen. For example, you can show only servers that enables "friendly fire" so you can kill your own team member (usually with dire consequences :lolflag:)

---

### Post by almostlinux on 2008-03-14
Try this server ... 8.2.120.143. It's pretty popular, usually full and has friendly folks on. 
In the beginning you would have download a bunch of files .. then you'll be all set.
Look for 'sparc' if you need help.

---

### Post by Rytron on 2008-03-14
Is it possible to download mods from another computer and install them to your own pc?

I notice that when I click to join a server I have to download files - the problem with this is that it takes too long (the speed at which the files are downloaded is much slower than when I download files from the internet normally).

Or are mods specific to each server?

---

### Post by almostlinux on 2008-03-14
90% of the servers play one of these mods which you can download off the internet.

etmain(the default one which comes with the game)
etpub
etpro
jaymod
noquarter

Besides this, you have individual maps. The game comes with 6 default maps. There are hundreds user designed maps - a google search for the map will get you a download link.

Some servers customize their settings/graphics .. so this'll be small additional server specific files.

On linux all the maps go to ~/.etwolf/etmain/

---

