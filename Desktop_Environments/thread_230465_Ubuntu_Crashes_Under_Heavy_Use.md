---
title: "Ubuntu Crashes Under Heavy Use"
date: 2006-08-06
forum: Desktop Environments
---

### Post by bart_simpson on 2006-08-06
Hey again, well, I've fixed numerous problems on my Ubuntu OS and everything is almost just about in order. Just about the final problem with it is that my Ubuntu OS randomly crashes when I use resource heavy applications like Frostwire and Flash. I added more RAM for a total of 768 MB today (it was crashing before that) and I have an Intel Celeron 2.2 Ghz processor. Any light you could shed on the situation would be greatly appreciated, thanks.

---

### Post by srunni on 2006-08-06
You could try adding XFCE to Ubuntu and using that instead when you're doing resource-heavy stuff. You should be able to keep GNOME and select which one you want when you're logging in (at least I can do that with GNOME/KDE). Otherwise, you could replace the default window manager, Metacity, with a lighter one, such as Fluxbox or Enlightenment.

---

### Post by bart_simpson on 2006-08-06
Is there anything else I can do to solve the problem besides switching desktop environments? My computer should be more than powerful enough to handle Gnome just fine, and it barely uses a 1/4 of my memory at heavy usage.

---

### Post by dennisharrison on 2006-08-06
do you get any errors when ubuntu starts up? before it mounts the root filesystem?
are you sure its not a hardware issue? what do you mean by crash? does the system freeze, or does it reset? is it turning off? is it only when you are using lots of cpu cycles or when you just leave your computer idle for a long time also?

---

### Post by 3rdalbum on 2006-08-06
I've not used Frostwire, but if it's a Java program that's probably the problem.

You'll have to define "crash". Is it just the immediate program, does the system lock up, if so can you kill the X server with "control-alt-backspace"? Are you using the proprietry Flash or one of the open-source ones?

---

### Post by bart_simpson on 2006-08-07
Okay, I'm going to try to answer your questions and provide you with all the information Ubuntu is giving me:

There was a filesystem error when I was starting up, but I fixed it with the help of a friend, bad partition or something, so now it boots cleanly, no errors.

I'm not sure it's not a hardware issue, it could be, but no signs show it is. I ran a memory test and it didn't pick up anything.

By crash I mean, Ubuntu logs me out of my account (now, this is when I'm using applications which require heavy CPU power) and takes me to a prompt which is like this:

Ubuntu 6.0.6.1 LTS Ubuntu ttyl

Ubuntu Login:



I've attempted to type something in, but at most it'll only catch one letter I type. Then after about 10-15 seconds, it'll shut down as if I went to System-> Quit-> Shut Down. It will almost always shut down when I'm using applications which require either Flash or Java like Youtube movies and Frostwire respectively.

Another thing, I had System Monitor up when I was opening Frostwire, and my CPU% was up around 100%, and even after it was done opening, if I left my computer idle while the app was open, it still was between the 40-70% in CPU usage range. After consulting with my friend who said while opening Frostwire he didn't top 50%, I thought this could be an issue, especially since my CPU (Intel Celeron 2.20 Ghz) is faster than his (Athlon XP 2000+).

My web browser (Firefox) also freezes usually if Youtube is up and running, I can watch the movie and all, but it will slow down considerably and eventually I'll have to force a quit. 

I'm also not sure if I can kill it with "Control-Alt-Backspace", haven't attempted to yet because, I didn't know what that did until now. And finally, I have proprietary Flash.

I hope all this information will help you help me to solve this problem, thanks.

---

### Post by joe343 on 2006-08-07
Hi, don't know if it helps but I had similar problems with my computer crashing/freezing when using a lot of CPU. It was due to my CPU overheating... I cleaned it up (removed all the dust from the heat sink) and now everything is fine.

---

### Post by kast on 2006-08-08
Same here I used canned air and blew it into the vents and a crap load of dust came out. after that no more crashing : )

---

### Post by bart_simpson on 2006-10-22
Hey, I know I'm really late responding and I apologize for that, I just wanted to say that the canned air idea worked great and stopped my frequent crashes, thanks.

---

