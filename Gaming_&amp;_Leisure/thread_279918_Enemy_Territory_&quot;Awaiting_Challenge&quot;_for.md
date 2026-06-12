---
title: "Enemy Territory &quot;Awaiting Challenge&quot; forever."
date: 2006-10-18
forum: Gaming &amp; Leisure
---

### Post by chadk on 2006-10-18
Help.
A few days ago ET stopped letting me into any servers. It just sits there saying "awaiting challenge" and counting up and up and up.  I use XQF to launch games but I've tried it from inside ET as well to be sure the server(s) aren't full.  I've searched the net but can't find any useful information.  Does it require some kind of ports open on the router or something?

---

### Post by chadk on 2006-10-18
seems to be an issue with punkbuster...
> Since the new punkbuster release 1.279 many of you have problems connecting to several servers. The cause of this is an outdated PBNS.DAT which comes from the previous version and is not automatically updated, because one is now less than ever possible to connect to that server. Not until you have been connected the actual Punk Buster software is loaded if there is a difference between client and server. If you connect to servers which are running the last PB Update and the client is running an old version, the PBNS.DAT avoids an GUID authentification (awaiting gamestate) because of operating with outdated data for the masterserver. (new: 192.246.40.62 - pbguidauth.idsoftware.com)  I'll have to figure out  how to update it...

---

### Post by MrBlond83 on 2006-10-19
Go into the enemy-territory/pb directory and run pbweb.x86 (might have to change permissions to make it executable first).

It will update the PB files. After that you have to copy pbweb.x86 into the .etwolf/pb directory and run it again.

That's how I got it to work on my comp after it gave me issues on PB servers and kicked me. Seems like sometimes it takes the data from .etwolf and sometimes from enemy-territory, no idea why, i keep them both updated.

---

### Post by aidanr on 2006-10-19
better to use pbsetup to update your punkbuster games [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

---

### Post by kvonb on 2006-10-20
I downloaded and ran the pbsetup as suggested by aidanr, it didn't work.

I ran it in /home/.etwolf/pb as well as root in /usr/local/games/enemy-territory, still no change.

I then tried MrBlond83's instructions (in BOTH locations) and it now seems to be working again, I say SEEMS because I tried a few servers and got in after about 5 "awaiting challenge".

Thanks :)

---

