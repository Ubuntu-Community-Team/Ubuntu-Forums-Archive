---
title: "Can't play DVD"
date: 2006-01-30
forum: Desktop Environments
---

### Post by BlackJack on 2006-01-30
I am new to Linux and based on what I have seen Ubuntu is one of the easiest ones to install and setup, basically it was so easy that I really didn't learn anything while installing it and it recognized just about everything in my laptop. So far it seem to be every bit as easy to use as Windows is and I have been using it since before Windows NT.

Anyway, before I make the committal jump to Linux I am trying to make suere that everything I need/want is there and works as I expect it to. One thing I have found so far it that I am unable to play a DVD movie in Totem. It keeps telling me that I am attempting to play an encrypted DVD without libdvdcss. I am unable find this library in the Synaptic Package Manager and have hit the wall. Can anybody help me out and let me know what I need to do to play a DVD movie? Do I need a different player? Do I need to install a Windows based player under Wine? Will it work if I get libdvdcss, and if so, how do I get it and install it?

Any help would be appreciated.

Thanks..........
(doesn't this have a spell check?)

---

### Post by dickohead on 2006-01-30
Assuming you're using Breezy (5.10), see here: [http://ubuntuforums.org/showthread.php?t=88788&highlight=dvd+playback+breezy](http://ubuntuforums.org/showthread.php?t=88788&highlight=dvd+playback+breezy)

Or add the ubuntu-backports repositroies for hoary (5.04) to your breezy sources.list file, and then run apt-get update and try installing libdvdcss2 then.

---

### Post by BlackJack on 2006-01-30
Yes I am using 5.10. Unfortunately i think I am getting lost. I looked at the thread you refferrred me to and it look like that user already had teh library. i went into Synaptic Package Manager and went to Settings/Repositories. When I looked at the format of the other repository properties I figured that what I had to do was enter in a Custom Repository of "http://us.archive.ubuntu.com/ubuntu-backports" but it wouldn't accept it.

How do I add the 5.04 repository?

---

### Post by dcstar on 2006-01-31
[QUOTE=BlackJack].......
One thing I have found so far it that I am unable to play a DVD movie in Totem. It keeps telling me that I am attempting to play an encrypted DVD without **libdvdcss**. I am unable find this library in the Synaptic Package Manager and have hit the wall.
.......[/QUOTE]
Add this line to your /etc/apt/sources.list:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by BlackJack on 2006-01-31
Thank you both for your quick responces. It is working fine now.

Thanks again..........

---

