---
title: "RA3 and PunkBuster"
date: 2006-07-25
forum: Gaming &amp; Leisure
---

### Post by andy- on 2006-07-25
-First time after installing quake 3, and rocket arena 3, I can join any ra3 server and PB starts to update. Record time for update I lasted was 45 minutes of getting kicked into 'Spectator' mode while PB updates.
-I usually just give up and /quit in console, to try to update it manually, by going to PB website and downloading the html file manually. (That never does anything either.)
-I've re-installed 3 times now and I'm allways getting the same error on PB servers:
```

^3PunkBuster Server: CRITICAL ERROR: Cannot Load /home/andy/.q3a/pb/pbcls.so
```

Here is the contents of my PB folder in .q3a/:

```
andy@home:~/.q3a/pb$ ls
dll  pbag.so   pbcl.db     pbcl.so   pbsec.htm  pbsv.db  scrnshot  svss
htm  pbags.so  pbclold.so  [COLOR="Magenta"]pbcls.so[/COLOR]  pbsv.dat   pbsv.so  svlogs

```

-Obviously the file is in there.

-Some other things that I've tried are setting user access to myself, and not root on the entire /usr/local/games/quake3/ folder, and just the /pb/ folder itself to see if it updates properly then, but had no luck either.
-I've also manually edited q3config.cfg in /.q3a/areana/ and /.q3a/baseq3/ and made sure that all the punkbuster comands are set to '1' like "cl_punkbuster 1" etc. Every time I re-enter a PB enabled server, PB just turns itself to Disabled again, and gives me the same error. (pbcls.so missing).
-PB homepage [www.evenbalance.com](www.evenbalance.com) hasn't give me any solutions to this either.

So if anyone has had this problem in the past and has any kind of suggestions, I'm all out of ideas.

Thanks for any help in advance.
-Andy

---

### Post by andy- on 2006-07-26
No one has run into this problem? ](*,)

---

### Post by andy- on 2006-07-26
For future refrence, for anyone who has this problem, this solution helped me:

[I]In the latest pointrelease the Anti-Cheat-Software punkbuster was integrated, which is automatically installed with the pointrelease. The punkbuster should update itself – But mostly it doesn’t. The easiest way to do it manually is to download the updatetool of punkbuster, pbweb.

Download it, and save it in /home/youruser/.q3a/pb (".q3a" - mind the dot - is a hidden folder so if the "Save" dialog doesn't show it move it there manually). You must save it there, otherwise it won't work. Now make it executable by typing
[B]
chmod +x / home/youruser/.q3a/pb/pbweb.x86[/B]

Then execute pbweb.x86 after changing into the pb folder

[B]cd /home/youruser/.q3a/pb
./pbweb.x86[/B]

Now punkbuster will bring itself up-to-date - this can take some time even if you are on broadband, seems like the responding server is rather slow.

That’s all you have to do to get a running version of Quake 3 Arena.

To start Quake 3 Arena type “quake3” in a shell or use the shortcuts on your desktop or in your desktopmenu. To play online with punkbuster, go into the menu of Quake 3 Arena, Multiplayer, and activate punkbuster.[/I]

Full HOWTO from Linux-Gamers.net direct link: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3")

Enjoy.

~Andy

---

### Post by cv_zero on 2007-10-06
Thanks! I've been having the same problem with wolf3d....I'll give this a try

---

