---
title: "Uninstalling Demo"
date: 2009-06-23
forum: General Help
---

### Post by HDingus on 2009-06-23
Hey everyone. I hope you guys can help me with this, because it's a pretty unique problem.

I recently got a new computer. When I say "new" I mean it's old, but I just got it, so it's new to me. It's kind of a placeholder until we can get our old computer back (it broke :o). It was recently cleaned out of everything. The only thing installed on it was Windows XP (and, of course, everything that automatically comes with it; e.g.: Internet Explorer).

I wanted to put Ubuntu on it because Windows is just so...blegh. Problem is, the computer's so old it doesn't even burn discs. I didn't want to request a CD because I wanted Ubuntu right away. I looked for a way to use ISO files without a disc and found Virtual Clone Drive by Slysoft. It worked and I was presented with the usual install menu. I chose the top button (to install demo and later install the full thing without Windows). It said I needed to leave the disc in or choose that I can't use the disc drive. Naturally I chose the latter, because I didn't have a disc.

The computer restarted, and the prompt came up to choose XP or Ubuntu. Choosing Ubuntu presented me with the loading screen and I thought I had it. Then a thing came up asking me to input commands. I figured it was doing that because there was no disc, so I restarted and chose XP. I set out to uninstall the Ubuntu demo, so I went to my Add or Remove Programs thing and uninstalled it, thinking that would be the end of it until I can get a disc. However, whenever I turn my computer on it still asks for me to choose XP or Ubuntu. This wouldn't be too big of an issue to me, it's just a matter of pressing Enter when the computer starts up. The thing is, though, that the computer has been running noticeably slower ever since. I still only have about 7 programs installed, none of them huge files. The only explanation I can come up with is that Ubuntu never fully uninstalled.

Help would be HIGHLY appreciated, as the sluggishness of the computer has become a great annoyance.

Regards,
HDingus

---

### Post by wojox on 2009-06-23
Hey HDingus, you need to edit the boot.ini file in xp.

   1. Right-click My Computer, and then click Properties.
   2. On the Advanced tab, click Settings under Startup and Recovery.
   3. Under System Startup, click Edit.

Now you should see a line in there that refers to ubuntu. Delete that line and save or apply changes.

Heres a site you can refer to [http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm). I use to run XP Home and then I found Ubuntu and never looked back. I have to boxes, on my Dell I run 8.10 server and on my Medion it's 8.10 desktop. Also run the DiskCleanup utility and maybe a defrag on windows. If your daring, you could open the registry go to edit click find and look for all instances of ubuntu and delete them. You do take matters into your own hands with registry edits. You been warned.

---

### Post by CatKiller on 2009-06-23
[This page]("https://wiki.ubuntu.com/WubiGuide#Uninstallation") might help.

---

