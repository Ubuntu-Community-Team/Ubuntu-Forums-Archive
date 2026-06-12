---
title: "Command line survival hike"
date: 2009-04-03
forum: General Help
---

### Post by jwbrase on 2009-04-03
I find I can generally do most things that I need to do in Ubuntu from the GUI. But I would like to pick up some more fluency with the command line. So let's take a survival hike...

A couple potential situations:

1): Suppose for some reason X doesn't start up automatically for me. In the most basic situation I'd just need to enter: ```
startx
``` or ```
xinit
```. But let's suppose I run in to deeper trouble and get some sort of error that prevents X from loading. What might be some common causes for this, and how would I troubleshoot and fix such a problem from the command line. I figure it's better to be prepared in advance against such a thing than to suddenly find myself stranded at the CLI and have to switch between one computer running Windows and a Web browser and this one running Ubuntu at the command line.

2): X goes on strike for higher wages. Sure, the people who developed it aren't charging any money, but the software itself wants some spending money. Programs have rights too! So I'm stuck at the command line until the labor negotiations are over. I'm stuck in the wilderness with only my wits and a spear for a week. What do I do? (Less poetically, let's assume I'm using some Linux system that for whatever reason does not have X installed. How do I get around?)

3): I understand that at some times command line instructions with arguements can be faster than GUI operations. Let's assume that I'm going through my normal day using Gnome. What are some situations where a graphical solution exists, but the command line is a better option, how do I recognize such a situation, and what commands might I often end up using? I'm young enough that all the OS's I've ever made any serious use of in my life have all had a GUI, so I have the feeling that I often miss moments when the command line could make life simpler simply because I know how to do it under the GUI and thus don't look any further than that. 

4): Repeat of question 3 for the Windows/DOS command line. I'm a bit more familiar with this, but not a lot.

5): Any hints for command line use in general and the exploration of an OS with an unfamiliar command line? (Not that I expect I will ever seriously need to do so). With an unfamiliar GUI you can just poke your way around and figure things out as you go, but that doesn't work quite as well with CLI's. Of course, the first step is always RTM...

---

### Post by Dejai on 2009-04-03
There is a really cool set of Tutorials you should check out that go through a large range of useful basics you should know on your linux / Ubuntu system. You can find more information at: [http://showmedo.com/videotutorials/series?name=pQZLHo5Df](http://showmedo.com/videotutorials/series?name=pQZLHo5Df)

Its called software carpentry - Shell basics. 

Shell can come in handy for example say a program is just frozen on gnome for this example lets say firefox. I can just jump into another ttyl by using CTRL + ALT plus F1 and enter the command:

ps aux | grep firefox

That will give me the processes id then I type:
kill proccess_id 


and I go back to my user space and its all done. 

Making directories on a user system is also interesting:

mkdir -p Test1 Test2 Test3 

Its easier and faster than clicking everything...

The terminal really unlocks Linux as I said watch the videos above, maybe buy a book on it if your really interested :P

---

### Post by jwbrase on 2009-04-03
It was pretty obvious what would happen, but I couldn't resist typing

```
ls / -R
```

The shell is still chugging through the 90 gigs of stuff on our NTFS drive.

(For those who don't know what that means, it spits out a list of every file and directory on your computer. Which can take a really long time)

---

### Post by boof1988 on 2009-04-03
> **jwbrase said:**
> It was pretty obvious what would happen, but I couldn't resist typing

```
ls / -R
```

The shell is still chugging through the 90 gigs of stuff on our NTFS drive.

(For those who don't know what that means, it spits out a list of every file and directory on your computer. Which can take a really long time)

Please post the time to finish that operation. :)

---

### Post by jwbrase on 2009-04-03
> **boof1988 said:**
> Please post the time to finish that operation. :)

I didn't time it and I don't really feel like taking the time to do it again (at least while watching it closely enough to time it).

Maybe 10 or 15 minutes.

---

