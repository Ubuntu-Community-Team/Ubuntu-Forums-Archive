---
title: "*nix IM worm?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by darthsabbath on 2006-01-14
Hey all, I know this will probably sound funny, but with the recent hit of IM worms for Yahoo and AIM, is it possible that one could exist in the wild for *nix machines?  Someone on my Yahoo list reported receiving links from me that I haven't sent.  I only run GAIM on 2 Ubuntu boxes, and I have GAIM installed on my parents XP box.  It's possible that they have been infected, but GAIM does not run at start time on that box. 

Gonna keep tracking this and see if I can figure out what's going on, but I wanted to at least see if anyone has had similar issues.

Phil

---

### Post by towsonu2003 on 2006-01-14
I'd say best way to go is run virus scan (clamav for linux in repos, command after auto-updating of virus list is clamscan -r -i /) and rootkit check (rootkitrevealer for windows, rkhunter -not in repos- and/or chkrootkits for linux) for all 3 machines... I don't think gaim should be working for a script to use your settings to send out files (but, I have no real ideas about that)...

also, you can chack out programs that are accessing web using ```
lsof -i
``` for programs running with your permissions, or ```
sudo lsof -i
``` for all programs accessing web. in sudo, you'll get printer stuff (hpiod and python in my machine) accessing localhost, ignore those at first.

---

### Post by darthsabbath on 2006-01-14
Well, I ran Clam on my notebook, as well as Chkrootkit, neither turned up anything.  Gotta check my desktop as well.  If those don't turn out clean that could just leave the XP machine, which as we all know could certainly be hax0red.

Phil

---

### Post by handy on 2006-01-14
Here's a good read while we're on the topic:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

It kinda makes you feel more secure...:KS

---

### Post by towsonu2003 on 2006-01-15
If all computers come up clean and your friend is sure that s/he received an infected message (that you **did not** send, than you could set up a frehly installed computer in your network and run ethereal for a couple of days (will give big big big file) to monitor what's going on (while noting what you did on the internet at which time)... if you're somehow infected, something's gonna call home or send out something else to someone at one point or another... 

maybe someone got your yahoo password? change it just in case, in a machine known to be clean. while you're there, change all your passwords as well ;)

---

### Post by Karma_Police on 2006-01-15
Couldn't it be a worm/virus in your friend's side, that disguises as you? It could show messages to your friend, pretending to be some random contact in is list. Don't know if such a thing exists, but it could be possible :P. Try to ask him if it's just you that sends him weird urls.

---

### Post by AmboyGuy on 2006-01-15
I agree with Karma_Police. Since most worm / zombie infected systems grab a persons address book and mail themselves to those addresses, odds are you aren't even infected. It's someone else's machine sending stuff with your name & address as the originator. ( I'd kinda bet it's a windows based zombie system where the owner doesn't have a clue he's infected).

---

### Post by darthsabbath on 2006-01-16
Ah, crap, I didn't think of that.

He's a knowledgeable computer user, but he does have a 7 year old who could easily get the box infected.  

That's gotta be it, as my boxes test clean.

Thanks!

---

### Post by ardchoille on 2006-02-10
[QUOTE=AmboyGuy]I agree with Karma_Police. Since most worm / zombie infected systems grab a persons address book and mail themselves to those addresses, odds are you aren't even infected. It's someone else's machine sending stuff with your name & address as the originator. ( I'd kinda bet it's a windows based zombie system where the owner doesn't have a clue he's infected).[/QUOTE]
YAY for the education you can't help but end up with when you use Linux for any decent amount of time :)

This is one of the reasons that I say Windows makes idiots out of most of its users.

---

