---
title: "css error. but cs kinda works (im using wine)"
date: 2007-07-19
forum: Gaming &amp; Leisure
---

### Post by Zexter on 2007-07-19
ok so i finally get steam downloaded and installed.

i wait the countless hours to download css, and css wont open. it tries and then i get the follow error message

                                                     
                                                                  ERROR!
SteamStartup() failed: SteamStartup(0xf , 0x0034E064) failed with error
1: The registry is in use by another process, timeout expired


but i can open regular cs. but i cant see any txt. and i put toham in the proper wine directory.
also i can join a server in regular cs, but it runs soooo slow.

im runnin 
intel celeron d 3.2 ghz proc
and 1.43ghz of ram

---

### Post by DaH-RaT on 2007-07-24
im having the same problem with the new wine. it worked before i restarted.
registry in use by another process.

Dell Precision|M70
ntel Centrino 1.8ghz ~ oced 2.39 ghz
7800 GTX go
1gb DDR2

---

### Post by jtwhitford on 2007-07-24
Did you try:
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

If its a wine issue, they should know about it.

---

### Post by DaH-RaT on 2007-07-25
im not quite sure im going to tease with it some more but i think some specific programs were running when i attempted, when i restarted fully it worked fine and i haven't had a problem with it again yet. ill try to find out what it was. i couldnt find the fbug on the site yet i know im a super hero when it comes to missing something so zexter you might want to check it out too for the time being

---

### Post by DaH-RaT on 2007-07-26
reading this thread  sounds like to me its been problems due to steam updates over the past week or two also with cedega not just with wine.

[http://www.cedega.com/forum/viewtopic.php?t=2878&highlight=&sid=675069c274e2f70b1332c1f6a90ac4bf](http://www.cedega.com/forum/viewtopic.php?t=2878&highlight=&sid=675069c274e2f70b1332c1f6a90ac4bf)

also jtwihitford helped us find this too

at the bottom it states how to fix the problem i think under known issues :)

[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

Known issues:

    * When starting a game Steam throws an error saying The registry was in use by another process.
      This seems due to a tendency of the steam client to crash when trying to shut down and release its registry. You can fix this problem by shutting down steam cleanly (keep running and exiting steam itself until you get a clean shutdown without any errors after "Shutting down" - watch the console you ran steam from) and then restarting it. Once steam has been shut down cleanly and restarted the error should not occur.
      If all fails, start Steam, right-click on the game and select Properties. Go to Local files tab and click on Verify integrity of game cache...

so far this is all i can find at the moment.

:::::EDIT:::::
i found a solution that worked for me, i loaded steam went to Games , right clicked counter strike source and went to protperties,  local files ,  and clicked Verify integrity of game cache. it worked right afterwards  :)

---

