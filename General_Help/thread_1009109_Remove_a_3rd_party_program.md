---
title: "Remove a 3rd party program?"
date: 2008-12-12
forum: General Help
---

### Post by AsyliumQc on 2008-12-12
hello all,

i am a fairly new user to ubuntu, ported from windows not long ago and i'm just starting to get the hang of the terminal, although i love it :D

so my problem is that i'm a fan of TrueCombat: Elite, a free videogame (mod based on Wolfenstein: Enemy Territory), and also the tech-support of my best friend, for whom i installed ubuntu not long ago.

so everything was fine, until i decided to install TC:E for him, the game being natively supported on Linux. I downloaded both Wolfenstein, the patch, truecombat and it's patch, as the usual procedure is:

-[Wolfenstein 2.60]("http://stealthzone.net/index.php?option=com_docman&task=doc_details&gid=2&Itemid=26")

-[2.60b patch, i know it's the windows version but it's actually an optionnal patch that shouldn't interfer with TC:E]("http://stealthzone.net/index.php?option=com_docman&task=doc_details&gid=15&Itemid=26")

-[TrueCombat 0.49]("http://stealthzone.net/index.php?option=com_docman&task=doc_details&gid=3&Itemid=26")

-[0.49b patch]("http://stealthzone.net/index.php?option=com_docman&task=doc_details&gid=2&Itemid=26")

As you can see, the files are *filename*.run.gz, so i had a hard time undertanding how to install it, until a friend told me to go in the properties, click the *allow file to be executable* and ./*filename*.run.gz, which worked very well and allowed me to install it.

However here's the real problem: when i installed truecombat, i think i installed it in the wrong directory, in wolfenstein instead of tcetest, however i cannot reinstall without uninstalling first, and this is where i need help: is there a command or anything to remove truecombat?

Thanks in advance, i searched on internet but havn't found anything about it, so hopefully i havn't posted the same as someone else did...

-AsyliumQc

---

### Post by poydence on 2008-12-12
I may not be fully understanding your question however... I think you are still in windows mode. When you install files in Ubuntu, you install packets and it takes care of where to put the files... which is quite different than windows where the user controls this. However, I bet you can uninstall by going to the panel on the top of your screen then 'Administration>Synaptic Package Manager' and then search using keywords for your files. Then mark them for uninstallation. Good Luck!

---

### Post by pedro_orange on 2008-12-12
You may wanna do something like:

```
dpkg -l | grep wolf
```

So you can find the name of the installed packages

Then you can use something like:

```
dpkg -r package-name
```

---

### Post by AsyliumQc on 2008-12-12
re hello!

this is precisely my problem: it's not a package, it's more of a console-version install as you would install it in windows. For example, it lets you choose the path to installation (default for wolfenstein was in /usr/local/games/enemy-territory/ ), so it hasn't created an entry in the synaptic or anything else...

i guess the best would be if someone installed it himself and could then see what it does, however i realise not everyone wants to do that...

hopefully it's more precise now, i would want to rush anyone but... it's rather urgent...

---

