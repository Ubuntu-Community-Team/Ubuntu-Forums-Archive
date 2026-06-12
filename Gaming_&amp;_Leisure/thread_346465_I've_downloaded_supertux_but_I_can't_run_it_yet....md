---
title: "I've downloaded supertux but I can't run it yet..."
date: 2007-01-25
forum: Gaming &amp; Leisure
---

### Post by some_random_noob on 2007-01-25
I downloaded supertux from [http://t3-ie.info/supertux.deb](http://t3-ie.info/supertux.deb) which I found a link to in the forums and now I'm trying to get it to work. I unzipped the main file which then gave me the following...

- supertux-data_0.3.0-0ubuntu1_all.deb
- supertux_0.3.0-0ubuntu1_i386.deb*

... the top one installed and I now have supertux files in /usr/share/games/supertux and I also have an application with a penguin on it in /usr/share/games/applications with the file name "SuperTux".

The problem starts with the bottom file*, I try to install it and it says "Error: dependency is not satisfiable: libc6" - so I tried "sudo apt-get install libc6" to try and update/install whatever libc6 is, but I still get the same error ("Error: dependency is not satisfiable: libc6")

I don't know exactly what I'm doing, however I did get dreamchess working by getting "buildessentials" and other various stuffing around. Questions below...

**- Is [http://t3-ie.info/supertux.deb](http://t3-ie.info/supertux.deb) the right place to download supertux?**
**- How should I go about fixing the error with libc6?**

... any help is appreciated :) I'm new-ish to Linux, but saying that I also wouldn't consider myself stupid.

---

### Post by wounded on 2007-01-25
sudo apt-get install supertux 

?

---

### Post by some_random_noob on 2007-01-25
nerd@hostname:~$ sudo apt-get install supertux
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package supertux
nerd@hostname:~$
--------------------------------------------------

?

---

### Post by wounded on 2007-01-25
Are your repositories up to date? Which do you have enabled?

When I search for supertux it is listed:

wounded@mediabox:~$ apt-cache search supertux
supertuxkart - a kart racing game
supertuxkart-data - data files for supertuxkart, a kart racing game
supertux - Classic 2D jump 'n run sidescroller with Tux
supertux-data - Levels for classic 2D jump 'n run sidescroller with Tux
wounded@mediabox:~$



here is the link to the Supertux entry in the Ubuntu Packages index: 

[Package: supertux (0.1.3-1.1ubuntu1) [universe]](http://packages.ubuntu.com/edgy/games/supertux)

Maybe you don't have Universe enabled?

---

### Post by some_random_noob on 2007-01-25
> **wounded said:**
> 
Maybe you don't have Universe enabled?
DAMNIT! ... I'll spend the rest of the day reading FAQs... pretend this thread doesn't exist...

---

### Post by meng on 2007-01-25
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by wounded on 2007-01-25
> **some_random_noob said:**
> DAMNIT! ... I'll spend the rest of the day reading FAQs... pretend this thread doesn't exist...

Ha! It's ok, we've done silly things from time to time. Search through synaptic for all the other games that are in the extra repositories also.

---

### Post by some_random_noob on 2007-01-25
Lol I downloaded heaps of stuff from help.ubuntu.com/community/ which I'll read later... I should have did that a long time ago but ITS JUST TOO TEMPTING TO ASK ON THE FORUMS!!

Anyway I think I know what I'm doing now but sadly I have to leave my beloved computer :( ... linux is awesome. In the package manager I read that there was some kids games that teach maths and typing etc... anyone tried edubuntu because I'm considering promoting Linux to schools to reuse old computers. It could make newsletters :o ... I'm waiting for my computer qualification before I do that though, that way people will actually trust me.

I never knew there was so much software for linux... people say Linux can't do anything. What a load of crap. I don't trust the reliability of emulators but theres so much cross-platform software that its not funny :D

---

