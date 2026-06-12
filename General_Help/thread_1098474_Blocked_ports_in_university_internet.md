---
title: "Blocked ports in university internet"
date: 2009-03-17
forum: General Help
---

### Post by ubiedubie on 2009-03-17
On my campus, they block the ports to most games, including steam game servers. Therefore none of my friends on campus can play any steam games or others like CoD4.

Oddly enough they do not block World of Warcraft.
If I was to find out the World of Warcraft ports, and made a server at home, using those ports, would they be able to connect then? Or would it still be blocked or something.

Has anyone done this before? And if so what ports are needed?

Thanks

---

### Post by mb_webguy on 2009-03-17
Some games allow you to change the ports used.  So if a game does allow you to change the ports, you could set up a server for that game using ports not blocked by your network's proxy, and your friends could use that server for that game.

You might also find a proxy server that allows you to bypass the school proxy and access regular game servers.

This is one reason why I think it's a bit silly for universities to use port blocking to control the usage of their networks.  It's extremely easy to bypass.  There are other more effective means of controlling bandwidth usage.

Of course, you need to make sure you're not violating the Terms of Service for your school's network by doing this.  Some schools don't forbid gaming in their TOS, believing it sufficient to block the ports.  Other schools whose IT are more competent *do* forbid gaming in the TOS, and monitor network traffic in addition to blocking the ports.  If this is the case, you could face some disciplinary action for violating the TOS, such as having your computer's MAC address blocked temporarily or permanently.

---

### Post by hikaricore on 2009-03-17
Blizzard also may frown upon you port forwarding through another server to get to their servers.
Might look suspicious and get you banned once that happens you have to deal with the idiots who work for Blizzard tech support.
Said idiots have the final say if you get to touch the account you pay them for ever again. Just things to keep in mind.

---

### Post by lisati on 2009-03-17
mb_webguy has made a couple of good suggestions.

I also wish to emphasise that most workplaces and educational facilities will have some kind of rules and expectations about acceptable use of their gear. Try to keep yourself on good terms with the admins by not violating their rules. Talk to them first if you need to, getting yourself in trouble for being sneaky isn't worth the hassle.

---

### Post by ubiedubie on 2009-03-18
I think it is allowed to play games in the TOS, they just block the ports and apparently don't give any good reason. They claim they are blocked to stop torrenting, but everyone seems to be able to torrent anyway.

mb_webguy - would it be possible to set up a proxy server on my ubuntu laptop? And if so what would I have to install, and what would my friends have to install to connect through it?

Thanks for your replies

---

### Post by mb_webguy on 2009-03-18
Setting up a proxy server, particularly one that does what you want it to do, is a non-trivial task.  Your best bet would be to search the Web for existing public proxies.

If you do decide you want to try setting up your own proxy, your first step would be to do some research on the [Squid proxy server]("https://help.ubuntu.com/7.10/server/C/squid.html").  Configured properly, I think it should be able to do what you want.

---

