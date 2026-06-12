---
title: "Sim city 3000 in Hoary?"
date: 2005-04-27
forum: Gaming &amp; Leisure
---

### Post by drews_blunted on 2005-04-27
This Thread was Created to help people find a way to install sim city 3000 on ubuntu. **(Updated Version)**

---

### Post by Leif on 2005-04-30
I'm going to copy/paste someone else's solution, I noted it from an earlier thread :

With a basic install, this is what happens:

michael@ubuntu:/opt/cxoffice$ sc3u
sc3u: relocation error: sc3u: symbol _dl_global_scope, version GLIBC_2.0 not defined in file 
ld-linux.so.2 with link time reference

Although Loki is closed, there are still product updates available on the net. The site I used was [http://public.planetmirror.com/pub/lokigames/patches/](http://public.planetmirror.com/pub/lokigames/patches/) , but any site listed on [http://updates.lokigames.com/](http://updates.lokigames.com/) will do. Instead of using the generic Loki update tool, which I suspect will not work because their updates server is down, downloaded the latest patch as a ".run" file.

Run the update script with "--keep". The "--keep" option is VERY important, I was not able to get the script to run otherwise:
Code:

sh sc3u-2.0a-x86.run --keep



Running the game with just "sc3u" results in a segfault. The solution is to instead start ALL Loki games with:
Code:

LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/[NAME OF GAME]


In other words, to start SimCity 3000:
michael@ubuntu:~$ LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/sc3u

NB: Some have reported that using LD_ASSUME_KERNEL=2.2.4 works better for them. I haven't had a problem with 2.2.5 so far.

---

### Post by drews_blunted on 2005-05-01
Thank you so much, i have never been able to get sim city 3000 to work on kernel 2.6 Ubuntu and its users truely are the Best!

I shall continue to spread the word, i have already converted 7 people to ubuntu  :) 

Keep up the good work! \\:D/

---

### Post by jkndrkn on 2005-06-01
Hey guys, the above howto worked perfectly in getting my copy of sim city 3000 unlimited up and going. However, sound does not work in it. The game's readme mentioned editing the file ~/.openalrc to enable OSS, but it seems I have no such file in my home directory.

My sound is currently configured to use ALSA and I have no other sound problems besides this one.

Any suggestions?

---

### Post by jkndrkn on 2005-06-01
Hey guys, the above howto worked perfectly in getting my copy of sim city 3000 unlimited up and going. However, sound does not work in it. The game's readme mentioned editing the file ~/.openalrc to enable OSS, but it seems I have no such file in my home directory.

My sound is currently configured to use ALSA and I have no other sound problems besides this one.

Any suggestions?

---

### Post by Matyy on 2005-09-11
Hej!

It doesn't really work for me, the game starts but I get a segmentation fault when I want to load a city. When I start a new one I can't build things like a power plant, streets are messed up (...).

> fcntl: Invalid argument
fcntl: Invalid argument

BUG! (Segmentation Fault)  Going down hard...
SimCity 3000 Unlimited 2.0.955a
Built with glibc-2.1 on x86
Stack dump:
{
        0xffffe420
        0xb7d70b7e
        0x84a0efd
}
Please send a full bug report,
along with the contents of autosave to: [email]support@lokigames.com[/email]
Unable to execute loki_qagent - exiting


---

