---
title: "xorg memory problems"
date: 2010-01-29
forum: Desktop Environments
---

### Post by rd1381 on 2010-01-29
i have total of 4gb ram and when using ubuntu 9.10 x64 ,xorg process consumes too much memory
it happened in gnome+metacity and gnome+compiz and gnome+kwin, so i think it not entirely because of one of the window compositors. though by using metacity it was worst (like memory usage of 2.7GB just by xorg :(  )
and its not virtual memory on anything like that because i checked :) . and also sometimes using metacity my memory gets full :) and my system hangs :( .
its a memory leak if i read correctly in other posts and in Google searches.
right now i have just firefox and gedit open( though i have a few applets running in gnome-panel) and xorg memory usage is 670MB and  closing firefox or anything else wont reduce the usage. 
my questions:
	 is there anyway to fix it?even a workaround? ( like running a command and 'freeing' memory used by xorg)
	my most important question:how can i find what process is leaking memory( if i am correct its not xorg fault but processes 'leak memory' (whatever that means) in xorg and dont free it up right?)
	if its xorg bug is it fixable ( my opinion is that its xorg fault not other programs because maybe some program is written by a stupid person and don't clean after themselfs but why xorg dont clean itself when it sees that that progrma is closed??
	
i have searched a lot of forums and this problem is a very common one regardless of volume of memory present.and it's not just ubuntu.so its either a common program used in many of does distros ( like java or java apps or firefox , which i use all 3 of them)or its internal( xorg  kernel or something like that ( i am not that fimilia with internal linux working))

---

### Post by mrant on 2010-04-23
I too am experiencing this problem. I am running Ubuntu 9.10 x86 with PAE with 4GB ram. My current uptime is about 8.5 days and Xorg process is eating 827MB ram. That is twice what firefox is using with easily 50+ tabs open. I am running Compiz, but is still a problem with metacity as well. My xorg-server version is 1.6.4

Any news on this?

--MrAnt--

---

### Post by rd1381 on 2010-04-23
i dont get any answer( at least to fix my problem) but i reinstalled ubuntu and this time xorg memory consumption doesn't go over 60mb

maybe it had to do with me installing xorg updates from launchpad repositories, but i remember that deleting does repositories and downgrading xorg didnt help

so my advice it wait for lucid (29th April) and don't install base library and apps updates from launchpad (just from ubuntu default update)

---

### Post by Gimmie5Bukks on 2010-05-28
try this command 

```
sudo GDK_NATIVE_WINDOWS=1
```

---

### Post by tsx2424 on 2011-05-08
> **mrant said:**
> Xorg process is eating 827MB ram.


 Same here...Compiz and Firestarter are eating a lot of memory as well.

---

