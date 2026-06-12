---
title: "Do you game? Do you like Ubuntu?"
date: 2005-11-15
forum: Gaming &amp; Leisure
---

### Post by Grafster on 2005-11-15
Do you gameon Linux? Do you like/use Ubuntu?
Want to so something (admittedly something small) to help both?

Ubuntu isn’t officially covered on transgaming ([www.transgaming.com)](www.transgaming.com)). While this isn’t a huge deal on a technical level (debian and ubuntu are fairly similar) it’s bad that Ubuntu doesn’t have its own forums etc from a perspective of attracting new users, either to Ubuntu or to Transgaming. 

I think it ought to be covered. I started a poll to do that.
Ten votes are needed to get the poll started. (You need to have an active Transgaming account which costs money).
[http://www.transgaming.com/postlist.php?forum=1263](http://www.transgaming.com/postlist.php?forum=1263)

If you don’t have an active account you can respond to this post here; esp if you would get a transgaming account if Ubuntu was officially supported.
[http://transgaming.org/forum/viewtopic.php?p=26221&sid=6fc6909091c182e0e1a1c8e658a5f8e3#26221](http://transgaming.org/forum/viewtopic.php?p=26221&sid=6fc6909091c182e0e1a1c8e658a5f8e3#26221)

Once the poll starts (assuming there are 10 like minded souls out there) I’ll post a link to that space here.
 
To see what distros are covered (a whole lot, including a few that I’ve never heard of) go to their forums ([http://transgaming.org/forum/index.php?](http://transgaming.org/forum/index.php?)) and scroll down to the distros section.

For the record Transgaming, while unpopular in certain circles, is really the only way to get (windows) games you buy in the store to work on Linux (including Ubuntu). They’re for profit (though not terribly profitable) and create a “software layer” that sits between the windows oriented game software and the linux OS to make it work. (OK, I just made that up and have no idea how it really works but that’s how it fits together in my head).

---

### Post by jbo on 2005-11-15
You got my vote. :) Just in time too, my subscription ends the 18th nov.. :P

---

### Post by mrpixels0 on 2005-11-15
only problem i have with Winex is that it is just as bad as regular wine is :(, i stayed with up till version 4.4 and gave up on running things like the sims 2, the sims and many other games. 

yeah i bought the special sims pack that was made for linux at a best buy and it was terrible half of everything was not rendered properly, it was  stated by transgaming that it would run correctly on linux but it did not. so why pay for somthing that is just as good as regular wine when wine is free and just as bad as winex ?.

Mrp.

---

### Post by bored2k on 2005-11-15
I don't "game" in Ubuntu. Although official support is always welcomed everywhere, I really haven't been able to percieve a considerable amount of ubuntu gamers here (besides  a few uber enthusiasts like dodson)...

---

### Post by Grafster on 2005-11-16
The poll request was seconded by enough people, and rather quickly at that. It's been moved up to the next stage of the process where Transgaming takes a look at it.
Thanks everyone!

Once it appears as a full poll I'll post with that address. (I have no idea when that will be...)

I think there are a lot of Ubuntu gamers, it's got its own sub-forum. I think the potential base is much much larger though. I have a few friends run Ubuntu with a Window's partition for games. If I wasn't primarily a WoW player I don't think I would be as blase about the whole thing but there you go.

And yeah, gaming isn't where I would hope it to be on the system. But its pretty good for some games and gaming has always been a bit dodgy anyway. Every Diablo game (for example) has been riddled with bugs that made it unplayable on Windows when it came out.
In some ways its a very immature market, but I do think that Transgaming is incrementally generating success.

---

### Post by tellnes on 2005-11-16
im a bit dissapointed in ubuntus gaming posibillities, i used fedora core 3 and 4, and never had nay problems with the few games i love, like rtcw and et.
But after going to ubuntu, this seems to be impossible, sound problems and dropout problems. Havent been able to fix it.
So, gaming is limited now for my part.

---

### Post by alynx on 2005-11-16
After bashing my head through the wall like a hundred times , i finally got World of warcraft to work with Wine in Ubuntu.  Only problem is that i cant mark any players , NPC's or postboxes ingame.:confused: 

I also have a slight lag problem , but I think i can fix that

---

### Post by ygarl on 2005-11-16
Stuff all that WINE stuff. Tried WINE, can't get DirectX games to run - so all my old faves like Dungeon Keeper, etc to run. So I just moved to Nexuiz, Wesnoth (very tasty!), etc.  I still have Win98 and XP partitions...
Now... how do I get into those things?

Maybe I just outta reformat those...

---

### Post by Grafster on 2005-11-17
[QUOTE=alynx] Only problem is that i cant mark any players , NPC's or postboxes ingame.:confused:[/QUOTE]

This is a known problem. There are two fixes listed in the transgaming forum stickies. The second one (which involved editing and command lines and sounds scary) worked for me.
Its a one shot fix so I've forgotten what I typed but back then but I remember this working for me

[QUOTE=transgaming forum sticky] 
2) This workaround should work for all users on all distros but may cause a frame rate drop.
Edit the World of WarCraft configuration file with your favorite text editor:
command line users: /home/USERNAME/.transgaming/config
Point2Play users: /home/USERNAME/.point2play/configuration_profiles/NAME_OF_WOW_CONFIG
Add the following section to the config file:
[AppDefaults\\wow.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
This change will remain persistent as long as you continue to use that configuration file for World of WarCraft. This change may need to be removed for future versions of Cedega.
[/QUOTE]
from <http://transgaming.org/forum/viewtopic.php?t=3149&sid=3a7f679a642a12e012193db83499f752>

I have -not- updated to cedega 5.0 yet so I can't verify. But it worked on the prior versions. 4.3 or 4.4 or whichever was most recent.

---

