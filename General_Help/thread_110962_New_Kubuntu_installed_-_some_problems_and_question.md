---
title: "New Kubuntu installed - some problems and questions"
date: 2006-01-01
forum: General Help
---

### Post by Brinstar on 2006-01-01
Happy New Year everyone!

I have installed Linux for the first time in 5 years this morning (first new Ubuntu installation this year :-k ) and it went well for the most part. There are a few things that are bothering me though.

1. USB Flash Drive (Sandisk) - I plug it in and I get a '/media:sda1 does not exist' reply.

2. When i installed, I was asked to choose a password. Is that the root password? Is the root called 'root' or 'ubuntu'?

3. I like to play Q3Arena with my brothers. The other PC in the house is WinXP-based. Is it possible to network these 2 machines (my Ubuntu one with the WinXP one) and play as we've been doing?

4. This is not really a problem, but something I'm just curious about. Obviously I haven't done much so far since I just installed this morning, so it's hard to tell if I'll have problems, but I chose not to have a swap file since I have 1GB of RAM. Will I be okay w/o the swap? If not, can I still make a swap file (IIRC I'm pretty sure I can)?

Thanks for any help guys :smile:

Edit: 1 more question :)

5. Can I mount an ISO file like I can do in WinXP using Daemon Tools?

---

### Post by GeneralZod on 2006-01-01
Happy New Year, and welcome to the Ubuntu Forums!


> **Brinstar]Happy New Year everyone!

I have installed Linux for the first time in 5 years this morning (first new Ubuntu installation this year :-k ) and it went well for the most part. There are a few things that are bothering me though.

1. USB Flash Drive (Sandisk) - I plug it in and I get a '/media:sda1 does not exist' reply.
[/QUOTE]

The initial release of Kubuntu 5.10 contained this bug.  Make sure you are completely up-to-date as a fix was release a while later.  You will need to restart KDE in order for the fix to take effect said:**
> 
2. When i installed, I was asked to choose a password. Is that the root password? Is the root called 'root' or 'ubuntu'?


Ubuntu has no root account by default, and the creation of one is fairly strongly discouraged - the "sudo" mechanism is used instead.  See 
[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo) for more info.

> 
3. I like to play Q3Arena with my brothers. The other PC in the house is WinXP-based. Is it possible to network these 2 machines (my Ubuntu one with the WinXP one) and play as we've been doing?


I don't know the answer to this one, but can think of no reason why you shouldn't be able to do this - the net-code should be the same :) Can't be of more help I'm afraid; sorry.  Try searching the forums; there are some specialised gaming sub-forums, somewhere!

> 
4. This is not really a problem, but something I'm just curious about. Obviously I haven't done much so far since I just installed this morning, so it's hard to tell if I'll have problems, but I chose not to have a swap file since I have 1GB of RAM. Will I be okay w/o the swap? If not, can I still make a swap file (IIRC I'm pretty sure I can)?


This is *probably* OK, but I wouldn't recommend it (I initially completely forgot to make a swap partition on my 256MB laptop and, while it ran for a while, it eventually died in a heap, so I submitted a bug report asking for a warning to be given if you don't create a swap partition, so that others don't make the same mistake :)) You can indeed add a further swap file; see e.g. [here](http://ubuntuforums.org/showthread.php?t=89782&highlight=mkswap) for more details.

> 
Edit: 1 more question :)

5. Can I mount an ISO file like I can do in WinXP using Daemon Tools?

Try [this](http://ubuntuforums.org/showthread.php?t=109735&highlight=%22Daemon+Tools%22) thread.
Hope this helps,
Simon

---

### Post by Brinstar on 2006-01-01
Great avatar there :)

And yes, it helped greatly, thank you, but in light of the answer you gave to q1, I'd like to know (and I'm being naive here and thinking, no, hoping, that things will be moving closer to the methods WinXP uses since it looks like Ubuntu is aiming primarily at that type of user) if I can download something close to a service pack and update KDE without installing the entire new KDE package? (I didn't really need to do this last time I used Linux so I don't have much idea of how things were)

Edit: actually, does anything like this exist for the OS as a whole (kind of like SP2 for Ubuntu)?

---

### Post by stimpack on 2006-01-01
Kynaptic/Synaptic or Adept will grab updates for you, they are not batched together like a service pack but as each little upgrade happens. You should have quite a few upgrades available on a new install.

---

### Post by GeneralZod on 2006-01-01
[QUOTE=Brinstar]Great avatar there :)
[/QUOTE]

Hehe - thanks :)

> 
And yes, it helped greatly, thank you, but in light of the answer you gave to q1, I'd like to know (and I'm being naive here and thinking, no, hoping, that things will be moving closer to the methods WinXP uses since it looks like Ubuntu is aiming primarily at that type of user) if I can download something close to a service pack and update KDE without installing the entire new KDE package? (I didn't really need to do this last time I used Linux so I don't have much idea of how things were)

Edit: actually, does anything like this exist for the OS as a whole (kind of like SP2 for Ubuntu)?

All updates are typically performed using your package manager.  In *U*buntu -  without the "K" - the GUI for the package manager is called Synaptic, and there is a system-tray application that monitors for upgrades and helpfully informs you when some are available.  In Kubuntu, there is not (yet) a system tray app like this, and the "official" package manager front-end is called Adept.  Adept is still a very young app, though, and so I personally use and recommend Synaptic for the time being.  To install it, bring up a command-prompt ("K"-menu -> System -> Konsole) and type (or copy and paste!)

```

sudo apt-get install synaptic

```

and enter your password.  When it's all done, Synaptic should be available in "K"-menu->System-> Synaptic Package Manager.  Click this, enter your password as usual, and click the "Reload" button.  "Mark all upgrades" and "Apply" should upgrade every supported app and library on your system - be warned, though, that there might be a couple of hundred megs to download!

There is no such thing as a service pack, though, as Linux is extremely modular and every module is upgraded independently of the others.  Plus, on a 6-monthly release cycle, there's not much need for them :)

---

