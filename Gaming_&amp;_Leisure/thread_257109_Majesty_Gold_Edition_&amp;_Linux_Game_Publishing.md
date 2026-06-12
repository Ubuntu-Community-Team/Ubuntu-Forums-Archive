---
title: "Majesty Gold Edition &amp; Linux Game Publishing"
date: 2006-09-14
forum: Gaming &amp; Leisure
---

### Post by ShirishAg75 on 2006-09-14
Hi all,
       I installed Majesty Gold Edition. Details of the game here . The game I got as Majesty-linux.iso & mounted it using mount loop command.

```
mkdir /home/shirish/cd

sudo mount -o loop /home/shirish/majesty-linux /home/shirish/cd
```

I had the CD but just wanted to use the image hence this way, it's also a tad faster for installs & stuff. Anyway. 

Looking into the .iso saw tht there is a setup.sh file . So ran the setup.sh with

```
./setup.sh
```

so it installed the game as well as LGP update files at :-

```
/home/shirish/LGP_Update
/home/shirish/majesty
```

now can run the game which is at ver. 1.4.0 . Tried updating it through LGP & while it says it did update don't see this on the screen while the majestyupdate at LGP_Update


```
Listing product updates

Majesty: The Fantasy Kingdom Sim
URL: http://updates.linuxgamepublishing.com/majesty/updates.txt
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updatefiles.linuxgamepublishing.com
Connecting to updatefiles.linuxgamepublishing.com
Connected
Transfer complete
Retrieved update list

Majesty: The Fantasy Kingdom Sim: Patch 1.4.01
Downloading README
URL: http://updates.linuxgamepublishing.com/majesty//majesty-1.4-1.4.01.run.txt
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updatefiles.linuxgamepublishing.com
Connecting to updatefiles.linuxgamepublishing.com
Connected
Transfer complete
Downloading update
URL: http://updates.linuxgamepublishing.com/majesty//majesty-1.4-1.4.01.run
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updatefiles.linuxgamepublishing.com
Connecting to updatefiles.linuxgamepublishing.com
Connected
Transfer complete
Verifying GPG signature
URL: http://updates.linuxgamepublishing.com/majesty//majesty-1.4-1.4.01.run.sig
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
Looking up updatefiles.linuxgamepublishing.com
Connecting to updatefiles.linuxgamepublishing.com
Connected
ERROR: HTTP error from server: HTTP/1.1 404 Not Found 
GPG signature not available
Verifying MD5 checksum
URL: http://updates.linuxgamepublishing.com/majesty//majesty-1.4-1.4.01.run.md5
Looking up updates.linuxgamepublishing.com
Connecting to updates.linuxgamepublishing.com
Connected
ERROR: redirection max count exceeded (looping redirect?)
MD5 checksum not available
Verification succeeded
Ready for update
Performing update
Update: /home/shirish/.lgp/lgp_update/tmp/majesty-1.4-1.4.01.run
Unpacking archive
Uncompressing Majesty 1.4 - 1.4.01...........................................
=============================================================
Welcome to the Majesty 1.4 - 1.4.01 Update
=============================================================

=============================================================
Performing update:
Updating files
-> PATCH FILE data/gpltext.cam
-> PATCH FILE data/miscdata.cam
-> PATCH FILE data/sounddesc.cam
-> PATCH FILE datamx/mx_gpltext.cam
-> PATCH FILE datamx/mx_miscdata.cam
-> PATCH FILE datamx/mx_sounddesc.cam
-> ADD FILE data/mdl1_action.cam
-> ADD FILE data/mdl1.bcd
-> ADD FILE data/mdl1_maindata.cam
-> ADD FILE data/mdl1_soundfx.cam
-> ADD FILE data/mdl1_unittype.cam
-> ADD FILE data/mdl1_voices.cam
-> ADD FILE data/xqd1_intro.cam
-> ADD FILE datamx/xqd1_bytecode.bcd
-> ADD FILE datamx/xqd1_intro.cam
-> ADD FILE datamx/xqd1_maindata.cam
-> ADD FILE datamx/xqd1_soundfx.cam
-> ADD FILE datamx/xqd1_unittype.cam
-> ADD FILE datamx/xqd1_voices.cam
-> ADD FILE quests/krolm.q
-> ADD FILE quests/mdl1.qdd
-> ADD FILE questsmx/balance_of_twilight.q
-> ADD FILE questsmx/xqd1_questdescriptions.qdd
-> ADD FILE README.extraquests

Product updated successfully.
Update complete 
```

Now my query is there anyway to know if the update has been installed & installed correctly or not. 

If anybody has played this game or patched it plz. reply. Thnx in advance.

---

### Post by gaminggeek on 2006-09-14
Majesty worked just out of the box for me how odd although I installed from the cd and I don't think there are any downloads to install

---

### Post by ShirishAg75 on 2006-09-14
hmm..... u didn't get the LGP_update thing. There are updates. Look [here]("http://updatefiles.linuxgamepublishing.com//majesty/") . Now it's a .run file. Any updates or advice would be nice. There is an FAQ also [here]("http://www.linuxgamepublishing.com/faq.php?id=8&") .  So plz. tell me in simple speak what I need to do. Thnx in advance.

---

### Post by Perfect Storm on 2006-09-14
The easist way I think is (Global installation):
```
sudo sh /destination/to/MajestyGold/CDrom/setup.sh
```

When installed, exit thet launcher and write:

```
gksudo /usr/local/games/LGP_Update/lgp_update
```

Done. Now it's full updated and ready to be used.

---

