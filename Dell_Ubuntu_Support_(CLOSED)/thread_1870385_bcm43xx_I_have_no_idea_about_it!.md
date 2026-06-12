---
title: "bcm43xx: I have no idea about it!"
date: 2011-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shahin_67 on 2011-10-27
Hey guys,

I'm new to linux and have just installed ubuntu 11.10 on my machine, a dell vostro 1500 one. the problem is my old-fashioned wireless card so that by surfing in net I learned I must make it compatible with the linux os. I just learned there are two ways to get it done. 

[LIST=1]
[*]bcm43xx
[*]ndiswrapper
[/LIST]
I know how I must deal with ndiswrapper program but have no idea about that bcm43xx -- just know it's linux driver for broadcom cards. Would anyone please explain me how to tackle it? what to download?

BTW, my wireless card is Broadcom 1390 WLAN MiniCard.

---

### Post by pastalavista on 2011-10-27
[This post]("http://ubuntuforums.org/showpost.php?p=11372158&postcount=4") makes it seem pretty simple. If that doesn't help, you may look through [these posts]("http://www.google.com/search?client=ubuntu&channel=fs&q=site%3Aubuntuforums.org+bcm43xxx+11.10&ie=utf-8&oe=utf-8") for lots of other possibilities.

---

### Post by varunendra on 2011-10-27
Hi Shahin, and welcome to Ubuntu Forums!

> **shahin_67 said:**
> I just learned there are two ways to get it done. 

[LIST=1]
[*]bcm43xx
[*]ndiswrapper
[/LIST]
<snip>
BTW, my wireless card is Broadcom 1390 WLAN MiniCard.
Where did you learn that bcm43xx is suitable for your card, can you provide the link to it? I am not sure but I think it won't work as it is 13xx (i.e., 1390). See [this wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for the list of models supported by this driver. So apparently it is only ndiswrapper that may help you getting that card work.

As a starting point, please open a terminal, enter the following commands and post back their outputs here:
```
sudo lshw -C network
lsmod
```

---

### Post by shahin_67 on 2011-10-28
@pastalavista: Thanks for your suggestion. It did work out well and now my wireless card recognizes modems around. [ANSWER]

@varunendra: Thanks for your suggestion too. I learned about my network (1390 WLAN blah blah blah) card through my Windows. but when I typed the code lspci in terminal it listed pci devices as well as my network pci card. It was something like broadcom 43xx! I applied pastalayista hint and then my wireless card started working properly.

---

### Post by varunendra on 2011-10-28
Congratulations! And Happy Ubuntu'ing :)
How about marking this thread as [Solved] now? :)

---

