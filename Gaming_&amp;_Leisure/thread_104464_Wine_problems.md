---
title: "Wine problems"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by mendosa on 2005-12-16
First of all, I want to say Hello! to everyone here! Great Forum!
Now about the problem:
I've managed to run same games with Wine from the Ubuntu Repositories(via Synaptic). Then I removed that Wine version(via Synaptic) and got later Wine versions from Wine HQ(adding Repositories), and those games didn't want to run although they installed succesfully. So, I removed Wine from Wine HQ and removed those Repositories, then installed  Wine from Ubuntu Repositories, but those games still do not want to run(they install succesfully).
I'll appreciate any help.Thanx.

---

### Post by mendosa on 2005-12-19
No replies, so nobody had such a problem. Good thing is I have a partition backup.

---

### Post by Evil Whisper on 2005-12-19
Wich game(s) are you trying to run with wine?  If you post a list I might be able to help you get them running. :)

---

### Post by mendosa on 2005-12-20
Thanks for Your answer Evil Whisper. I just managed to run them using terminal, (I am not able to run them by Nautilus)which may mean that some links are broken, or wine is not configured correctly. So, thanks again and sorry for bothering.

---

### Post by polt on 2005-12-20
i'm having problems too.  :( i can't tell if i installed correctly.  i'm trying to put on some low tech games like nancy drew and kings quest 5, but this does not seem to be working.  and also, my computer wont connect to the wine repositories.  is installing wine via synaptic package manager sufficient, or are there additional configurations needed?

---

### Post by mendosa on 2005-12-21
Well, I was able to run some games in this way: after installation I opened terminal, changed to game directories and wrote: wine [COLOR="Magenta"]game[/COLOR].exe. Pink colour is in place of the game executable name. Try checking Wine database for the specified titles:
[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php)
but although some are listed as running, I didn't success in running them.
Did You enable Universe Repositories in Synaptic? You need this to install wine.

---

### Post by leech on 2005-12-21
Sounds like when you changed versions of wine it screwed up the configuration.  I would install the wine from WineHQ repositories and then 'rm -r .wine', back up any game files you may have saved in there first of course.  It should have installed everything to .wine/drive_c

Leech

---

### Post by alynx on 2005-12-21
i play wow in wine :) 

anybody knows if the mouse bug is fixed in 0.9.3 ? 

but I could always patch my 0.9.1 with the wowfixes patch

---

### Post by mendosa on 2005-12-21
Thanks leech, but this didn't solve the problem. But of course I can use terminal:) . I did not play wow, so I do not know about the mouse, sorry alynx.

---

### Post by alynx on 2005-12-21
i fixed it with the patch and following the guide around here somewhere.

But i get much lower FPS than in Windows :( just wondering what might cause this ?


edit : cant use windows anymore , just cant , ........ hehe. Im liking Linux too much

edit 2 : hope some linux guru answers my praires :)

---

### Post by mendosa on 2005-12-21
Hi there alynx! Did You consider using Cedega Time Demo? 14-days trial is available at Transgaming web site: [http://www.transgaming.com/products_linux.php](http://www.transgaming.com/products_linux.php)
I noticed that some games are running faster under Cedega.

---

### Post by alynx on 2005-12-22
maybe I'll try that :) 

thanks. 

Do you know if cvs Cedega is working as well as Cedega ?

---

### Post by mendosa on 2005-12-22
I do not have much experience, but I've heard that there are copy protection problems with CD's under cvs.Now I have installed:
Wine 0.93
cvs Cedega(dx9wine version)
Cedega Time Demo.
During Xmas I will have some more time to test some games on this platforms, and I will post about the results here. Stay tuned:D .

---

### Post by mendosa on 2005-12-25
As I promised, some test results today. No good news about cvs(dx9wine)-I didn't manage to run any game using this. General reflection is : if any game is running under Cedega, it will be running under Wine. Games that are in 3D are running a little faster under Cedega, and some movie sequences are played with sound, while under Wine it was no sound. Let the Wine be with You!

---

