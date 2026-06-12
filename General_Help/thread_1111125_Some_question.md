---
title: "Some question"
date: 2009-03-30
forum: General Help
---

### Post by wongpk on 2009-03-30
Take your time, not really in hurry. Just came back to Ubuntu again :) A few questions want some answers...

**1, How to speed up Ubuntu boot up?** It seems taking some times on booting up. And also speed up the sensitivity of menu/folder opening? I feel it's slow.

**2, Root account?** I deleted my username account and now I'm booting in with root access, I wonder is there any way to **retrieve** back the deleted account?

**3, Firefox seems lagging.** Is that because I didn't have any swap space? I dual boot with Vista, limited 10GB for Ubuntu.

Thanks!

---

### Post by perpetualcacophany on 2009-03-30
**1.** There are a few things that I know of. First, cut down on the number of startup programs you have. Go to System > Preferences > Startup Applications and choose what you need and what you don't need on startup. 

This next one will only help if you have a dual core processor. In the terminal type:

```
gksu gedit /etc/init.d/rc
```

In there, you will want to find the line that reads CONCURRENCY=none and change it to CONCURRENCY=shell

**2.** I don't know of any way to regain all of the info from that account, but I would definitely suggest that you don't use root as your normal login account. It's very unsafe. Ubuntu was built to have the root account inaccessible for this reason. 

**3.** I don't think a lack of swap would effect your performance in Firefox. Swap only really comes in to play when you run out of ram. It is used to keep the system from locking up when no extra ram is present by allowing the computer to write to it in the same way it would use ram. 

There are many reasons that Firefox could be running slowly, so my suggestion would be to make a thread in Absolute Beginners giving more specifics about the problem. They should be able to help you there.

---

### Post by Iowan on 2009-03-30
1. There's a How-To around here somewhere about speeding up boot-up... 
2. You can check the passwd/shadow file to see if user still exists.  If it was deleted, you can build another user and add them to the sudo (admin?) group.
3. IPv6 *can* cause problems. the link in my sig is somewhat dated.

---

### Post by 3Miro on 2009-03-30
You should have made a swap partition. That way you could enable hibernation and then in stead of minutes, Ubuntu boots in 30 - 40 seconds. Unless you have at least 2GB of RAM, no swap would mean an overall slower machine. For a laptop swap is a pretty much a must for power conservation.

Booting as root is really bad idea. You can accidentally damage something and you inevitably make your system more vulnerable. I don't thnik there is away to restore a user, if the /home/username folder is deleted, then user is gone. You can go to System -> Admin -> Users and Groups and create new user and log in as that one.

What do you mean by lagging Firefox, does it do that when you visit specific pages or in general? Does it take some time start up and then runs well, or starts up fine and then slows down? Have you updated to the latest version? You can use System -> Admin -> System Monitor to see if you have any rouge processes taking up a lot of RAM/CPU or if Firefox itself is going rouge.

---

### Post by wongpk on 2009-03-30
Thanks a lot for all the reply. Very helpful... More questions coming :P

perpetualcacophany
#1, I'm running on Core2Dual, same command on terminal?
#2, That's what I know after I deleted the user account :lol:
#3, Heading there now :)

Iowan
#1, Indeed... Should have check into it instead :P But I find most speed up are complicated as they're mostly command in terminal, which I don't really like (Scare)
#2, I want the information/config I have had on that account :( Guess it's gone...
#3, My ISP use IPV6 for local, will it affect if I disable it?

3Miro
#1, I see... I have 3GB RAM with laptop. Now I got some job to do :?
#2, If I'm the one and only one who use this laptop? Does it make it safer?
#3, Basically my Firefox took time to change tab (Only 5 tabs currently). It will stop respond when I click on another tab, or I click back to Firefox from my movie. Well, actually this happen to me on XP and Mac, only Vista run Firefox well.

---

### Post by hyper_ch on 2009-03-30
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Iowan on 2009-03-30
> **wongpk said:**
> Iowan
#1, Indeed... Should have check into it instead :P But I find most speed up are complicated as they're mostly command in terminal, which I don't really like (Scare)

#3, My ISP use IPV6 for local, will it affect if I disable it?

1. It's a bit dated, but [this]("http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot") is the How-To I remember. It's only scary the first few times - then it's a sense of accomplishment (like driving a stick shift).
3..  IPv6 is more of an issue if your ISP does NOT support it.

---

