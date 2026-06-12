---
title: "More and more slower overall"
date: 2009-05-06
forum: General Help
---

### Post by barraclou on 2009-05-06
Everybody shout about Linux being faster than Windows and using less memory. I agree that it loads less crap when you turn it on, but to me it seems to stop there. Ubuntu needs much more more hd memory (at least 1GB more than Windows) and twice the minimum RAM required to install it, then when it is running, it is so thirsty with the RAM. Running Photoshop on Wine is really, really slow, but even if I make it an exception, overall it seems to be more and more slower. Linux is supposed to be pretty much virus-free, but can it be some kind of nasty getting my machine slow? On a PIII running W2k, I was able to run many applications at the same time without any problem, but it is not really a good idea to do so with Ubuntu, especially if you browse (Firefox and/or Opera) as well. If I multitask on Ubuntu, it is not unusual to see my browser frozing or the radio stream on Audacious skipping. What's wrong? Maybe I am losing patience. If only the memory thing was just for the installation, it would a just a bad moment, but it is seems worse each day. It is really sad to say so, but it is so awful that I am thinking to make Windows my main OS back.

---

### Post by anti_microsoft on 2009-05-06
> **barraclou said:**
> Everybody shout about Linux being faster than Windows and using less memory. I agree that it loads less crap when you turn it on, but to me it seems to stop there. Ubuntu needs much more more hd memory (at least 1GB more than Windows) and twice the minimum RAM required to install it, then when it is running, it is so thirsty with the RAM. Running Photoshop on Wine is really, really slow, but even if I make it an exception, overall it seems to be more and more slower. Linux is supposed to be pretty much virus-free, but can it be some kind of nasty getting my machine slow? On a PIII running W2k, I was able to run many applications at the same time without any problem, but it is not really a good idea to do so with Ubuntu, especially if you browse (Firefox and/or Opera) as well. If I multitask on Ubuntu, it is not unusual to see my browser frozing or the radio stream on Audacious skipping. What's wrong? Maybe I am losing patience. If only the memory thing was just for the installation, it would a just a bad moment, but it is seems worse each day. It is really sad to say so, but it is so awful that I am thinking to make Windows my main OS back.

You did give a swap partition a presume.? I would not really worry to much about how you see the ram being used, unused ram is wasted ram and Linux is much better at managing it the older versions of Windows (Vista is a little better and 7 is better yet but another story).

Running wine is going to be a little slow on a slow CPU. Figure to run Photoshop you have to run a layer between it and the OS in order for it to run. If you are using an older CPU maybe you should have a look at GIMP.

Also you may want to look at what services are running and disable those you don't need. The sound skipping issue sounds to me like a CPU being maxed (or close to) issue to me, I have run Linux on many older machines that play really nice if you learn how to tweak it out.

---

### Post by spillin_dylan on 2009-05-06
Well I'm sure that I won't be the only one to tell you that you're comparing an OS made 9 years ago with one that was released a few weeks ago.  Have you tried putting Vista on that computer?  I'm thinking it would likely come to a screeching halt as well.

The other thing to keep in mind, is that Ubuntu is definitely one of the more "resource-hog" distros out there, and maybe a Debian or Slackware or (something else???) would work better with your setup.

---

### Post by colau on 2009-05-06
> **barraclou said:**
> Everybody shout about Linux being faster than Windows and using less memory. I agree that it loads less crap when you turn it on, but to me it seems to stop there. Ubuntu needs much more more hd memory (at least 1GB more than Windows) and twice the minimum RAM required to install it, then when it is running, it is so thirsty with the RAM. Running Photoshop on Wine is really, really slow, but even if I make it an exception, overall it seems to be more and more slower. Linux is supposed to be pretty much virus-free, but can it be some kind of nasty getting my machine slow? On a PIII running W2k, I was able to run many applications at the same time without any problem, but it is not really a good idea to do so with Ubuntu, especially if you browse (Firefox and/or Opera) as well. If I multitask on Ubuntu, it is not unusual to see my browser frozing or the radio stream on Audacious skipping. What's wrong? Maybe I am losing patience. If only the memory thing was just for the installation, it would a just a bad moment, but it is seems worse each day. It is really sad to say so, but it is so awful that I am thinking to make Windows my main OS back.
From Applications>Graphics you can use GIMP instead of photoshop in ubuntu.
Do you have a swap partition activated?
From terminal
```

cat /proc/swaps

```

---

### Post by barraclou on 2009-05-07
The Gimp? Forget me, I just don't like it and Gimpshop is waste of time. It is sure that I would rather prefer a Linux version of Photoshop, but Adobe is not interested to offer that version. So, if I want to run on Linux, Wine is far from being perfect, but it is the only alternative to cover these important gaps, such as Photoshop. Otherwise, as many others, I would jail in Windows. 

I installed Ubuntu alone (no dual boot) in the main partition, plus an activated swap on sda5. No Windows at all on that machine.

It might be a maxed out machine. I admit that I should compare older Windows with older Linux, newer Windows with newer Linux. Photoshop/Wine was just an example, but it would pretty much the same thing using a few native applications at the same thing. The point is something that I don't understand is why everyone bitches that each newer Windows version get heavier for no real justified reason, if it is pretty much the same thing with Ubuntu? It is supposed to be lighter and I installed on-start applications, then in full action, it is heavier to run than Windows. What make it heavier from version to version, if nothing new is automatically installed on start?

Unless finding a better solution to my Ubuntu slowness, I admit that maybe I should give a try (dual boot?) to Debian or Slackware, if it is run better.

---

