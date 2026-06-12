---
title: "Firefox in Wine"
date: 2009-04-19
forum: General Help
---

### Post by phantom3113 on 2009-04-19
Firstly, I apologize if this is in the wrong section, but I wasn't sure if it was actually a wine issue or not. Anyway, I've heard all kinds of accounts on Firefox under windows/wine being faster than the native repos version for ubuntu. Well, mine is apparently backwards. The original FF runs absolutely fine while FF under wine is sluggish, particularly on pages that use java/flash (scrolling is slow, clicking is slowly responsive, etc). I need to use FF under wine some websites will only work under a windows-like environment for some reason. Not my choice, but I deal with it. :(

---

### Post by Merk42 on 2009-04-19
Well I ran [http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action) and the results were better in Ubuntu 8.10 vs Windows 7

What sites require a windows version of Firefox?
Usually I'd see something that just requires Internet Explorer, or maybe one that **says** Windows/Mac, but will work in Linux (like the H&R Block free US Federal taxes)

I don't really know the answer to your question but maybe here [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by phantom3113 on 2009-04-19
I guess to be more specific, playing some games that require connecting to a server or such gives Ubuntu problems. Examples would be Facebook games and zOMG on gaia-online. In regular firefox, the game(s) hang when trying to connect to the server.

BTW, how would I move this thread to the wine section? Or should I just create a new thread there?

---

### Post by codeseer on 2009-04-19
What was the problem with zOMG?

Which facebook game is giving you problems?

---

### Post by phantom3113 on 2009-04-20
With zOMG, it would give me a 104 error when trying to connect to the game server (various forums gave me the idea that it's a problem with java in Linux; I haven't tried it in wine yet...)

The facebook game is Texas Hold'em Poker. Again, when connecting to the game server, it hangs at "loading 20 of..."

---

### Post by CowzRule on 2009-04-20
One thing you could try is a Firefox add-on called "User Agent Switcher". The add-on allows you to change which Browser and OS is being reported to the server. For more info see [http://chrispederick.com/work/user-agent-switcher/]("http://chrispederick.com/work/user-agent-switcher/")

---

### Post by codeseer on 2009-04-20
Facebook works just fine with me:

[[IMG]http://img408.imageshack.us/img408/7020/screenshot003u.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshot003u.png)

Do you have the flash from the repositories or the official flash?

Edit:

zOMG is down right now, but from what I've read the 104 error is common amongst everybody.

Gaia seems to work fine as well:

[[IMG]http://img511.imageshack.us/img511/6370/screenshot004z.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshot004z.png)

---

### Post by codeseer on 2009-04-20
I see the issue with the 104 connect error on zOMG. People have been complaining about that occuring on Linux for over 4 months to the company; this shows you that the company doesn't care.

I'm going to try something and get back to you on it.

Edit:

Looks like zOMG plays just fine under Wine in the latest Firefox with the latest official Flash. I've played around with it and changed maps; I did a bunch of stuff and it all seems to work fine. As for your Wine slowness issue, I would recommend completely removing Wine and deleting the configurations and stored files for it, then reinstalling it.

The alternative to using Wine would be to install the official Flash version 9 (old version); however, I believe you will need to incorporate the latest official Flash (version 10.x) into your current Ubuntu install to get Gaia and Facebook to work properly.

Tell me whether you have a 32-bit or 64-bit install and I will give you the instructions on how to properly install the official Flash.

---

### Post by phantom3113 on 2009-04-20
To answer the flash question, I believe I have the repos version. I can't be too sure since I did all that a while ago, but I distinctly remember installing flash via the terminal, so the chances are good that it's repos. I'll try reinstalling wine as well, and would much appreciate the instructions for insalling the official java :) (I'm running 32-bit Intrepid BTW) Also @ CowzRule, I'll look into that addon. Hopefully, it'll let me view those Internet-Explorer-only sites. Thanks for the help everyone!

---

### Post by codeseer on 2009-04-20
> **phantom3113 said:**
> To answer the flash question, I believe I have the repos version. I can't be too sure since I did all that a while ago, but I distinctly remember installing flash via the terminal, so the chances are good that it's repos. I'll try reinstalling wine as well, and would much appreciate the instructions for insalling the official java :) (I'm running 32-bit Intrepid BTW) Also @ CowzRule, I'll look into that addon. Hopefully, it'll let me view those Internet-Explorer-only sites. Thanks for the help everyone!

I find that the User Agent Switcher addon is only good for when a website developer has some bias or is lazy and blocks everything but IE by looking at the user agent string; this is a fairly rare occurrence and when I see it I try my best to use some other website, service or business just for the principle of it. Some website developers are even rude and arrogant about it, giving you a nasty little message.

I believe the official Flash is what you'll need to get the Facebook, Gaia and other sites working. Here are the instructions for installing the official Flash:

Download the .deb from: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

Close Firefox.

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Execute the .deb and install the official Flash.

For the official Java install see this post: [http://ubuntuforums.org/showthread.php?t=1113039]("http://ubuntuforums.org/showthread.php?t=1113039")

---

### Post by phantom3113 on 2009-04-20
Ok, followed the uninstall and install instructions, everything went fine. Poker managed to actually work, although I can't see any of the tables (selecting "find me a seat" allows me to play though) nor any servers on the server list. Also, zOMG still gives me a 104 timeout error, but then I wasn't expecting much from there. I've attached a screenshot to help

---

### Post by codeseer on 2009-04-20
The poker was like that on mine also, I didn't pay any attention to it because I clicked the 'find me a seat' right away. The other Gaia stuff works for you now though also, right?

If you redo your wine like I said, you should have no problem with the zOMG and probably can use it just fine for the poker.

---

### Post by phantom3113 on 2009-04-20
Haven't fiddled with gaia much yet and wine's my next target :P I'll let you know how it goes! Thanks again :)

Update:Wine was freshly installed after a complete purging; Firefox appears to be running much more smoothly now! Hopefully this will keep my various issues at bay...for now. :P

Forgot to mention earlier, a professor of mine at my college posts his lecture notes on his website, however they're done in PowerPoint and then uploaded as html through Explorer in a way I've found has been called "lazy code". Due to this, the presentations look fine in Explorer, but through firefox, they're a jumbled and completely indecipherable mess! Do you think that addon would make them viewable, or is it a lost cause?

---

