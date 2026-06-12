---
title: "WoW Patch 2.2.0 issues"
date: 2007-09-26
forum: Gaming &amp; Leisure
---

### Post by melzanis on 2007-09-26
Ok so WoW was working great (will a few bugs here and there, nothing major) and then the new patch comes out. In the back of my mine i'm thinking great, i'm going to spend a few hours trying to sort this one out. However I haven't found anything on this forum or on Wine's forum that can help. I have tried updating wine and I'm still getting the same problem. 

My problem comes after the patch has been downloaded and the downloader tries to install the patch. It keeps saying "waiting for files to close". It's just keeps flashing this message and then doesn't do anything after that. I'm forced to close down my terminal. I have no idea what to do, can someone please help me out with this.

---

### Post by Seraed on 2007-09-26
> **melzanis said:**
> Ok so WoW was working great (will a few bugs here and there, nothing major) and then the new patch comes out. In the back of my mine i'm thinking great, i'm going to spend a few hours trying to sort this one out. However I haven't found anything on this forum or on Wine's forum that can help. I have tried updating wine and I'm still getting the same problem. 

My problem comes after the patch has been downloaded and the downloader tries to install the patch. It keeps saying "waiting for files to close". It's just keeps flashing this message and then doesn't do anything after that. I'm forced to close down my terminal. I have no idea what to do, can someone please help me out with this.

Same....

Though I cheated and used Cedega to finish the patch. Also... the game performance in Wine is garbage for me unless I disable audio completely, unless I use Cedega, then everything is working fine.

---

### Post by melzanis on 2007-09-26
you have to pay for Cedega right? if not where can I get it so I can play some WoW =P

---

### Post by Nkari on 2007-09-26
Could it be something to do with the fact that there is now an inbuilt voice chat client so there is no longer a need to use ventrillo or teamspeak or something of the sort?

---

### Post by generious on 2007-09-26
There was a poll on the cedega forums about the chat feature for it to be intergrated into cedega poll passed to developers no feedback as of yet.

Noticed this morning on the cedega forums couple of people are having 3d problems artifacts ect and sound problems....

---

### Post by UbuntuniX on 2007-09-26
Make sure WoW is closed.
I've recently got a bug where WoW must be xkilled to exit, so I had this problem until I xkilled.

---

### Post by sunfire on 2007-09-26
Using wine and get "Waiting for files to close."-error.
-------------------

"Blizzard Updater errors 
[edit]
Waiting for Files to Close Error 

On occasion, once the patch has been downloaded, the updater itself will fail to start and instead flash a message which says "Waiting for files to close." 
Run winecfg 
Set the Windows version to NT 4.0. 
Close winecfg and run the updater. 

After the updater is finished, switch the Windows version back to whatever you had previously in order to play."

------------------

This worked for me today with WINE :) 

btw, I used ".../World of Warcraft/Patches/WoW-2.1.3-to-2.2.0-enGB-Win-patch/BNupdate.exe" after downloading patch and getting that error message.

Copy from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors)

-------------------------

After 2.2 patch my Wine dosen't play WoW anymore on OpenGL :( I have tried lots of tricks to make it work like before patch with OpenGL but no succees.
Does anynoe have this proplem after patching to 2.2 ?

---

### Post by melzanis on 2007-09-26
Well first I want to thank every one for their posts. 
I however still get the same error come up, I haven't tried killing WoW it's self and just letting the installer do it's thing. Because I don't know what the key's are to do so.

---

### Post by Jaxilian on 2007-09-26
I have same problems with Wine. Any solution yet?

---

### Post by Lsuwulf on 2007-09-26
This was noted in the beta, and has to do with the integrated voice chat.  Unfortunately, it's a bug on WINE's side.  Give it a couple of weeks to get fixed.

---

### Post by Jaxilian on 2007-09-26
> **sunfire said:**
> Using wine and get "Waiting for files to close."-error.
-------------------

"Blizzard Updater errors 
[edit]
Waiting for Files to Close Error 

On occasion, once the patch has been downloaded, the updater itself will fail to start and instead flash a message which says "Waiting for files to close." 
Run winecfg 
Set the Windows version to NT 4.0. 
Close winecfg and run the updater. 

After the updater is finished, switch the Windows version back to whatever you had previously in order to play."

------------------

This worked for me today with WINE :)

Copy from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors)

Tried this....doesn't work for me

---

### Post by Jaxilian on 2007-09-26
What did work though was this:

```

Wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Patches/WoW-2.1.3-to-2.2.0-enGB-Win-patch/BNUpdate.exe 

```

---

### Post by sunfire on 2007-09-26
> **melzanis said:**
> Well first I want to thank every one for their posts. 
I however still get the same error come up, I haven't tried killing WoW it's self and just letting the installer do it's thing. Because I don't know what the key's are to do so.

Did you use  ".../World of Warcraft/Patches/WoW-2.1.3-to-2.2.0-enGB-Win-patch/BNupdate.exe" after downloading and winecfg change to NT4.0 ?

---

### Post by orionsbelt on 2007-09-26
> **sunfire said:**
> Using wine and get "Waiting for files to close."-error.
-------------------

"Blizzard Updater errors 
[edit]
Waiting for Files to Close Error 

On occasion, once the patch has been downloaded, the updater itself will fail to start and instead flash a message which says "Waiting for files to close." 
Run winecfg 
Set the Windows version to NT 4.0. 
Close winecfg and run the updater. 

After the updater is finished, switch the Windows version back to whatever you had previously in order to play."

------------------

This worked for me today with WINE :) 

btw, I used ".../World of Warcraft/Patches/WoW-2.1.3-to-2.2.0-enGB-Win-patch/BNupdate.exe" after downloading patch and getting that error message.

Copy from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Blizzard_Updater_errors)

-------------------------


I'm having the same problem as everyone else ("waiting for files to close" error).  I've tried switching to Windows NT 4.0, I've tried running the installer through the terminal, the way other people have mentioned...none of it has worked.

Has anyone found anything else?

---

### Post by orionsbelt on 2007-09-26
Okay, I feel silly now.

As you may know, new versions of wine can be a bit finicky (as they're released every 2 weeks and in perpetual beta...or something like that).  I had trouble with 0.9.44, so I've been sticking to patch 0.9.43.

Anyway, I decided since I was having trouble anyway, I would try upgrading - especially since 0.9.45 is out right now.

And viola, no more problems!  I installed through the terminal with wine set to "Windows NT 4.0" (see previous post for detailed instructions.) 

Hope this helps some of you out.

---

### Post by dantum on 2007-09-26
Yes I can confirm that 0.9.45 version of wine fixes this sound issue. But you need to be wary of other problems that come with versions above 0.9.42.

See [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) for list of possible issues.

Have fun

Dan

---

### Post by andraxion on 2007-09-27
Yea it also seems like this new patch has disrupted gameplay for people actually running Windows. There is a problem with network cards that limit the data and when people log on, nothing loads UI related so your skills all seem to be gone, you look naked, and your items appear as the question marks (whichs means WoW couldn't load the data to load the images)

Anyone affected by any of this? I am downloading WoW right now because I lost my CDs years ago and it's taking forever.

---

### Post by hikaricore on 2007-09-27
andraxion:  You forgot to mention they **completely removed hardware sound support**.

[COLOR="DarkRed"]**The Blizzard devs are complete @#%$ing morons.**[/COLOR]

---

### Post by andraxion on 2007-09-27
It appears there has been violent rioting by some players... maybe haha.

[http://forums.worldofwarcraft.com/maintenance.html](http://forums.worldofwarcraft.com/maintenance.html) is what you see when trying to view the forums. Blizz probably got fed up with the "Told you this voice-chat system is lame" posts.

---

### Post by hikaricore on 2007-09-27
> **andraxion said:**
> It appears there has been violent rioting by some players... maybe haha.

[http://forums.worldofwarcraft.com/maintenance.html](http://forums.worldofwarcraft.com/maintenance.html) is what you see when trying to view the forums. Blizz probably got fed up with the "Told you this voice-chat system is lame" posts.

Actually this is scheduled downtime for everything but the game servers.

There was a news post about it ingame.

---

### Post by andraxion on 2007-09-27
Ah. I got Linux without the urge to get WoW because my wireless connection was really crappy in Windows. Now that I got Linux, the elusive driver that everyone seems to have problems with was already installed. I also get like 25% more connectivity with Linux so I decided to get WoW again.

---

### Post by jdimauro on 2007-09-27
Switching winecfg to NT4.0 did the trick for me (I'm using wine 0.9.43).

:)

---

### Post by vondomitz on 2007-09-28
I encountered the "waiting to close"  message as well when trying to run the patch.  The resolution I had was to kill every .exe processes besides the BNUpdater.  Of course, wineserver must still be running.

The .exe running for me was Repair.exe...

---

### Post by Tellisk on 2007-09-28
I had the same issue as the OP. It worked after I

1. Restarted computer.
2. Opened directory containing the patch (having already been downloaded by the Blizzard Downloader)
3. Run the patch exe file using Wine.
4. Open WoW.

---

