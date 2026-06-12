---
title: "No Games will install (-5003 : 0xffffec75)"
date: 2008-04-19
forum: Gaming &amp; Leisure
---

### Post by 4rk3typ3 on 2008-04-19
I'm using cedega, but unfortunately their forums don't seem to be of much help on this matter. I have been trying for almost a week now to get games to install in it but the only games I've had any success with are starcraft and ultima online. Every time I go to install a game I get the error:

```
Error Code:	-5003 : 0xffffec75
Error Information:
>SetupNew\SetupDLL.cpp (711)
PAPP: -Any Game-
PVENDOR: -Any Vendor-
PGUID: -blanked by me-
$12.0.0.49974
@Windows XP Service Pack 2 (2600) BT_OTHER 64196.103
```

Now, from what I'm seeing it appears that it is assuming I am trying to install in windows XP without service pack 2. Every game is giving me this message when I try to install from CD but of course certain things are different between them. I have reinstalled cedega, used autoremove to get rid of any remnants and even tried it on a different system to see if i could get it working...still same error.

If anyone has seen this issue and have any information relating to it and how to fix it, it'd be much appreciated. 

Things I've already done:
reinstalled cedega
Installed cedega on another system (fresh install of ubuntu)
Inserted D3DX9_30.DLL into my cedega's system32 folder

Another thing to note, I receive this error in the command line whenever I open cedega in either system, I think it is related but I don't specifically know what it's asking for

```
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
```

seems the gddb parser is out of date, but I dunno. I also get this message whenever the game errors out. 

```
wine: Unhandled exception, starting debugger...
```

so wine seems to be playing rough with cedega. 

I have tried several other methods but I was unable to find them again to post this thread, If i find them I will pull them in if necessary.

***New development on the matter seems to be that the installation of previous cedega installation is causing the issue, but I thought that installing in a fresh install of ubuntu would exclude that. When I get home I will attempt to purge the files for Cedega completely, possibly even wine, and try again.

---

### Post by Cappy on 2008-04-19
Cedega:
[http://games.cedega.com/gamesdb/games/view.mhtml?game_id=4616](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=4616)

Wine:
[http://appdb.winehq.org/appview.php?iAppId=4051](http://appdb.winehq.org/appview.php?iAppId=4051)

It doesn't work in Cedega, only wine and even that seems to have problems for some people.

I recommend Google before you waste a ton of time. "Cedega Supreme Commander"

---

### Post by 4rk3typ3 on 2008-04-19
Thank you for your reply, however, I believe you may have misunderstood my situation. No games will install, the error was an example of what I am seeing from any of the games I try to install regardless of them being on the GDDB or even proven to work. The error does appear to suggest that a previous installation is already in place, but as I have said multiple attempts to remove and use cedega have been unsuccessful.

---

### Post by Cappy on 2008-04-20
Here's a thread relating to your problem: 
[http://www.cedega.com/forum/viewtopic.php?t=8221](http://www.cedega.com/forum/viewtopic.php?t=8221)

---

