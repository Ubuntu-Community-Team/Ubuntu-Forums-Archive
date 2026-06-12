---
title: "Error when setting default application &quot;Open With&quot;"
date: 2006-08-08
forum: Desktop Environments
---

### Post by nexes on 2006-08-08
I've searched through the wiki, forums, and Google and have yet to find a solution to this problem.

I'm trying to set mp3's so that when they're selected they will open with XMMS. When I go to "Open With" and select any application (or type in any command) I get a dialog with the title: "Could not add application" and the body "Could not add application to the application database".

The only exception is the few items already in the Open With menu, such as Beep Media Player and Movie Player.

Also, when I go to the file properties, I have the same issue. But in addition, I can't change the selection for the default program. The checkbox's don't respond at all. Also, the remove button isn't selectable.

I've asked a few of my friends, and none of them have ever encountered this problem.

Any help would be appreciated!

---

### Post by computergroove on 2006-08-08
Can you open XMMS and open your mp3 files from the file menu? Do they play when you do this?

---

### Post by nexes on 2006-08-08
Yes, that does work, although I've simply been dragging and dropping them.

It's not just with mp3s. I've tried this with torrent files as well (trying to get them to open in uTorrent) and a few other applications. It applies to all types of files and apps.

---

### Post by computergroove on 2006-08-09
OK, has any of these things ever worked for you? Is this a clean install of ubuntu or did you update it in the terminal? When did this start happening?

---

### Post by nexes on 2006-08-09
I just installed Dapper Drake a few days ago. The first time I messed something up (ran out of disk space running Automatix, I stupidly gave it too little, restarted and couldn't login), but I recall trying thison that first install and having it not work either, but I'm not positive.

I wiped it clean and reinstalled a few days ago. I've installed a bunch of software, but it's all been through Synaptic. I can't really think of anything abnormal that I've done.

Is there any way to change file associations through the terminal and avoid the gui altogether?

---

### Post by nexes on 2006-08-10
Does anyone know I can find the application database for Nautilus? I'm trying to find a way to manually change file types, and I think that the permissions may be screwed up.

---

### Post by computergroove on 2006-08-10
I just tried to open a mp3 with XMMS and it worked flawlessly. I right clicked and was able to change the open with option. I have a pretty new install of Dapper Drake (2 weeks maybe). First thing I did was set a root password. Then I did all the online updates. Then I installed automatix and all the relevent programs that I would like to use. Then I made sure my Nvidia drivers were working. Then I installed the optimized kernel for my cpu and I am where I am now. I can only wish you luck from this point on. I do not understand why a fresh install would act like that. Im out of ideas.

---

### Post by nexes on 2006-08-10
Thanks for trying. I'm still working on it. I just can't seem to find where the Nautilus application database is. I can only assume that the permissions are somehow screwed up.

I'll be sure to post whatever resolution I come to.

---

### Post by shdgrao on 2006-08-14
Did you manage to solve the problem?? I have exactly the same problem with my ubuntu dapper. 

Thanks

---

### Post by shdgrao on 2006-08-14
The solution for me was:

In the home dir (change <your user> to your login name):

sudo chown <your user> -R .local
sudo chgrp <your user> -R .local

---

### Post by Glendon on 2006-10-11
Thanks. I had the same problem.

---

