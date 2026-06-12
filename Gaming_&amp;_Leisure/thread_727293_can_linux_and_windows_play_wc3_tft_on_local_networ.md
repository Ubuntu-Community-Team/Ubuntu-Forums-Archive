---
title: "can linux and windows play wc3 tft on local network tougether?"
date: 2008-03-17
forum: Gaming &amp; Leisure
---

### Post by archy87 on 2008-03-17
im running wc3tft on cedega, and my brother uses win xp
we both have patched to the latest patch, we both can connect to battle.net
we both have legal copies, and it seems i've open'd the right ports (6112-6119)

any ideas what could be the problem? 

btw, we do have a file sharing and printer sharing already working.

---

### Post by FrozenFox on 2008-03-17
Assuming you mean you want to play together in a game on LAN, then I might be able to help.

I know I've done it using Wine before, wc3 and sc both worked, when on a "fake" LAN using the program called Hamachi in the same hamachi server.

However, the new version of hamachi did not work for some reason. In order for it to work, we all had to use the same old version (I think it was 0.9.9.9).

[http://www.oldversion.com/program.php?n=hamachi](http://www.oldversion.com/program.php?n=hamachi)   for the windows client ver 0.9.9.9.

For the linux client, I couldn't help you much beyond telling you to go find hamachi (no graphical interface) and ghamachi (a gui for it) (EDIT: quamachi is apparently better? see below). Last time I installed and did that was on Sabayon, which wouldn't help you much in Ubuntu most likely. If you can't come up with an easier solution or figure hamachi out, come back I suppose.

[http://sourceforge.net/project/showfiles.php?group_id=191833&release_id=569485](http://sourceforge.net/project/showfiles.php?group_id=191833&release_id=569485)

Perhaps try installing the two .debs from there? I've never tried quamachi, and I installed hamachi manually, but perhaps the two .debs there would greatly help you.

---

### Post by janfsd on 2008-03-17
I don't think hamachi is needed, since both the computers are on LAN, so no need for fake LAN. Maybe you could try with wine? Maybe is a cedega related problem, btw if you are trying with wine, don't install the one of the repos, because it has a bug on multiplayer.
Maybe is a gateway problem? (Taken from appdb.winehq.org)
> Multiplayer Setup

Make sure you have the correct ports open. Open outbound and inbound, TCP and UDP, port 6112, or whatever you set in the game configuration. More Network Ports

If you try to play using the Local Area Network option, and do not see a game hosted from your machine on another or vice versa, and you are in the same subnet, this is likely caused by not having a default gateway. The game relies on sending UDP packets to the broadcast address and Linux will not send them unless there is a default gateway or another rule to handle them. To fix it, there are two methods:

Add a default gateway.
- OR -
Route 255. 255. 255. 255 to your local network.

---

### Post by FrozenFox on 2008-03-18
Actually, it didn't work for me without hamachi for some reason (i tried of course, setting hamachi up was a pain when I did it). Why not is beyond me, but I'll just assume it's a wine bug regarding LAN. Indeed though, a non-hamachi solution would be best.

---

### Post by soxs on 2008-03-18
You should, at least my brother and I did so for years. But you should note that you need to patch wine, as AcceptEx is required but not fully implemented yet or the winesource prior or equal 0.9.53 and compile yourself (you need to do some extra steps if youe running x86_64 system [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)).
Another reason it does not work, is as simple as it sounds: Windows Firewall^^, I know it sounds dumb, but check twice :-P
Hamachi is in no way required.

---

### Post by janfsd on 2008-03-18
Just get the latest version of wine, and no patching needed :)

---

### Post by soxs on 2008-03-18
I am not sure about that, it was 0.9.56 which I last tested wc3tft over LAN & b.net... and that version required patching, at last it did not work out of the box, so I used my old slef-compiled 0.9.53 with applied patch..

---

### Post by janfsd on 2008-03-19
Well, for hosting it requires patching, but to join games it doesn't. So since his brother is using win xp, he doesn't have to host, thus no patching required.

---

### Post by soxs on 2008-03-19
Ok^^ your right, for joining, patching is not required, but for hosting it is^^

---

