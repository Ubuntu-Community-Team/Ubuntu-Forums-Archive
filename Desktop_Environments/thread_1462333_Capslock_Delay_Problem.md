---
title: "Capslock Delay Problem"
date: 2010-04-25
forum: Desktop Environments
---

### Post by xmRipper on 2010-04-25
Hello,

I want to say that there is only one reason for me to not use Linux.

That is the capslock delay problem.
I've tried to use Linux numerous times since years but that annoying capslock delay problem always returned back me to Windows.

**What is the capslock delay problem ?**
The problem occurs if you are used to typing capital letters using capslock button instead of shift and if you are writing too fast.

For example, you can see the same sentences which were written in windows and linux;

In Windows:
"Hello friends. How are you today?"

In Linux:
"H**E**llo friends. H**O**w are you today?"

There is a delay while switching to lowercase...

---

That problem occurs in every Linux-based operating system since years and it is still not fixed. I've tried different desktop computers, laptops, netbooks. Still same.

That's the only reason for me to not use Linux.

**Update: Here is a video for you to reproduce the problem** [http://www.youtube.com/watch?v=lVdu5lXz8RA](http://www.youtube.com/watch?v=lVdu5lXz8RA)

Thank you.

---

### Post by ajgreeny on 2010-04-25
The obvious question is "why on earth do you use Caps Lock instead of shift?"

I don't think I have ever heard of the problem before, nor somebody who uses Caps Lock in that way.  That is surely not the normal way to use a keyboard.

---

### Post by xmRipper on 2010-04-25
I've just found that the issue is also mentioned before there : [http://ubuntuforums.org/showthread.php?t=96492](http://ubuntuforums.org/showthread.php?t=96492)

You can't understand the problem without using capslock & writing really fast with it.

I want to give another example, my nick name is xmRipper.
Whenever I try to write my nickname on Linux, it writes this: xmRIPper

**Edit:**
Also mentioned there: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=744541](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=744541)

---

### Post by DaymItzJack on 2010-04-25
Have you tried using shift?

---

### Post by xmRipper on 2010-04-25
> **DaymItzJack said:**
> Have you tried using shift?
Please be serious.
I said I am used to using capslock key instead of shift. Of course shift key is working without any problem.

[B]
Edit:[/B] If you mean remapping capslock  to shift, no I haven't tried that yet.

---

### Post by 3rdalbum on 2010-04-26
Problem reproduced. It's very much a corner case, though; the vast VAST majority of people who can type quickly use Shift, because every touch-typing program and teacher in the world will make you use Shift for the odd capital letter.

It's not even really a bug in the sense of the word, but instead of just switching back to Windows and "hoping it'll be fixed", have you actually made the Xorg developers aware of your problem? Chances are that they don't know - because I'd never heard of this before today.

EDIT: Perhaps renicing X to -20 might help reduce the delay?

---

### Post by xmRipper on 2010-04-26
> **3rdalbum said:**
> (..)have you actually made the Xorg developers aware of your problem?(...)

No, because I don't know the people who are developing linux core or that 'Xorg' thing, and I don't know where I should report the problem. The reason of this is my not being used Linux before.

Also, my English wasn't good enough to report the problem years ago.

Now, I will be glad to help to solving the problem. I can help it on testing step. I've been interested in software development since I was 12. I'm 18 now.

---

### Post by xmRipper on 2010-04-27
So who are going to fix this? Where should I report this problem?

---

### Post by 3rdalbum on 2010-04-27
[http://bugs.freedesktop.org](http://bugs.freedesktop.org)

The project to report against is "xorg".

---

### Post by xmRipper on 2010-04-29
Reported. By the way, I've just realized that delay problem only occurs for lowercase letters.

You can reproduce this problem yourself.
Press capslock and A keys fast and repeatedly then you will see that there is no any lowercase letter.

You will see this;
"AAAAAAAAAAA"
instead of;
"AaAaAaAaAaA"

---

### Post by RisingFalcon on 2011-03-04
Exactly.I have this problem too.If you guys have any solution, please tell me.Its annoying.Infact, supppper annoying

---

### Post by xmRipper on 2011-04-30
bugs.freedesktop.org link for this bug :
[https://bugs.freedesktop.org/show_bug.cgi?id=27903](https://bugs.freedesktop.org/show_bug.cgi?id=27903)

And I've just made a video on Ubuntu 11.04 and reproduced the problem, which can easily be reproduced by everyone :
[http://www.youtube.com/watch?v=lVdu5lXz8RA](http://www.youtube.com/watch?v=lVdu5lXz8RA)
There is a delay while switching to lowercase.

---

### Post by Crosshash on 2011-11-11
Just signed up to this forum to report the same issue. Every single distro of linux (be it SUSE, Ubuntu, Red Hat (back in the day)) that I've used has had this problem.

You can see it for yourself. Turn capslock on and press for example:

H -> CAPS -> j

It'll actually write out

HJ

---

### Post by xmRipper on 2011-11-11
> **Crosshash said:**
> Just signed up to this forum to report the same issue. Every single distro of linux (be it SUSE, Ubuntu, Red Hat (back in the day)) that I've used has had this problem.

You can see it for yourself. Turn capslock on and press for example:

H -> CAPS -> j

It'll actually write out

HJ
And still not fixed for years.

---

### Post by typhoon_tip on 2011-11-11
> **xmRipper said:**
> Reported. By the way, I've just realized that delay problem only occurs for lowercase letters.

You can reproduce this problem yourself.
Press capslock and A keys fast and repeatedly then you will see that there is no any lowercase letter.

You will see this;
"AAAAAAAAAAA"
instead of;
"AaAaAaAaAaA"

I just did, and apart from a initial weird moment of uncertainty of my keyboard, here is the result:
```
Hello Friends, How Are You Today ?HowAaaAAAAaAaAaAaAaAaAaAaAaAaAaAAAAaAaAAaAaAaAaAaAAaAaAaAaAaAaAaAaAaAaAaAaAaAaAaAaA
```

It didn't miss a bit, the last part I was using finger at guitar picking speed (I play guitar).

But I did notice another very weird thing: everytime your caps-lock change status, hard disk is written or accessed..... is this normal for you guys ?

---

### Post by xmRipper on 2011-11-11
> **typhoon_tip said:**
> I just did, and apart from a initial weird moment of uncertainty of my keyboard, here is the result:
```
Hello Friends, How Are You Today ?HowAaaAAAAaAaAaAaAaAaAaAaAaAaAaAAAAaAaAAaAaAaAaAaAAaAaAaAaAaAaAaAaAaAaAaAaAaAaAaAaA
```

It didn't miss a bit, the last part I was using finger at guitar picking speed (I play guitar).

But I did notice another very weird thing: everytime your caps-lock change status, hard disk is written or accessed..... is this normal for you guys ?

Nah here is a better way to reproduce:
[http://www.youtube.com/watch?v=lVdu5lXz8RA](http://www.youtube.com/watch?v=lVdu5lXz8RA)

Hold any button like A or S, then press capslock repeatedly. You will see the number of capital letters will be higher. But they are supposed to be same.

---

### Post by typhoon_tip on 2011-11-11
> **xmRipper said:**
> Nah here is a better way to reproduce:
[http://www.youtube.com/watch?v=lVdu5lXz8RA](http://www.youtube.com/watch?v=lVdu5lXz8RA)

Hold any button like A or S, then press capslock repeatedly. You will see the number of capital letters will be higher. But they are supposed to be same.

Lol true ! But actually in pratical world is very hard to ever bump into this issue. I am in IT field since I was 14, I am 36 now and never noticed this problem.

---

### Post by xmRipper on 2011-11-11
> **typhoon_tip said:**
> (...) I am 36 now and never noticed this problem.

Because you are not used to type capital letters using capslock.

---

### Post by jz88 on 2012-04-23
SAme problem. I was taught to use shift key but somewhere along the line changed to caps lock.

TYping speed potential can be higher for some people using caps lock   because it avoids the process requiring the brain to perform a   simultaneous key press.

IF you can press three keys faster than pressing two keys  simultaneously, then you should use caps lock.  IT comes down to  brain-hand coordination speed and what feels more  logical for the  individual. I use my left pinky finger to quickly double  tap the caps  lock key whilst sneaking a character in between with  another finger...  it feels less interruptive and more efficient.  I've always  experienced a slight stall with the simultaneous  key press  which renders it a slower process, but this may not be the  same for  everyone. 

Hope the problem can be fixed. MAYbe I just need a faster CPU. Back to slow/lazy typer's shift key for the moment :p

---

### Post by jz88 on 2012-04-23
.

---

### Post by xmRipper on 2012-04-23
> **jz88 said:**
> "I recommend using caps lock instead of shift to type capital letters to allow more flexibility in the hand that you would normally use shift with." - Typing tips from the fastest typist, Sean Wrona

Yeah.

---

### Post by rhlobo on 2012-09-21
ANy news??


# THE PROBLEM
There is an unproportional delay when turning off caps lock between keyup and lowering case.


# DESCRIPTION
I know I should have learned to use Shift modifyer, but this is not the case. It's very much a corner case, but there are plenty of other users who have this bad habit as I do. I don want to discuss with is the best way of typing, etc. It will not be productive.

The problem seems to happen only when turning the CAPS LOCK off, so it seems to be suffering form a programmatically induced delay. Xorg developers must have not bumped into this problem yet, specially because it affects only people with this "terrible" habit that are able to type fast (70+ words por minute).

CapsLock functioning as normal:
<CAPSLOCK KEY_DOWN><CAPSLOCK KEY_UP> T <CAPSLOCK KEY_DOWN><CAPSLOCK KEY_UP> est

Expected Result:
Test

Actual Result:
TEst


# WHAT IT IS NOT
It is NOT a hardware problem. I've experienced this problem for years now, with many linux distros (actually, occurs to every single distro I've tryed including SUSE, Red Hat, Slackware) using various machines and keyboards. I explicity assure that it is not a RAM problem as well. And by the way, other OSs, using same machines, do work without problem (even with heavyweight programs).


# LINKS
**The are many threads about it.** Someone with more power here should unify / cross-reference them. For the ones interested in this issue, I recommend to use the official bug report (lets centralize/coordinate efforts):

- Bug report [https://bugs.freedesktop.org/show_bug.cgi?id=27903]("https://bugs.freedesktop.org/show_bug.cgi?id=27903")

For reference:
- [http://ubuntuforums.org/showthread.php?t=96492]("http://ubuntuforums.org/showthread.php?t=96492")
- [http://ubuntuforums.org/showthread.php?t=744541]("http://ubuntuforums.org/showthread.php?t=744541")
- [http://ubuntuforums.org/showthread.php?t=1462333]("http://ubuntuforums.org/showthread.php?t=1462333")
- [http://ubuntuforums.org/showthread.php?p=12252966]("http://ubuntuforums.org/showthread.php?p=12252966")
- [http://forums.justlinux.com/showthread.php?123715-delay-in-turning-off-caps-lock]("http://forums.justlinux.com/showthread.php?123715-delay-in-turning-off-caps-lock")


# HOW TO REPRODUCE THE PROBLEM
```
Turn capslock on and as fast as possible press: H -> CAPS -> H -> H -> H
It'll actually write out: HHhh
```

Videos that try to reproduce the problem:
[http://www.youtube.com/watch?v=0Xa6_yJYMsU]("http://www.youtube.com/watch?v=0Xa6_yJYMsU")
[http://www.youtube.com/watch?v=lVdu5lXz8RA]("http://www.youtube.com/watch?v=lVdu5lXz8RA")


# FIX
It seems that xorg 1.12 will have this partially fixed. There are other things that will need to be fized as well, but it seems you will be able to configure a few things and make it work. Just take a better look at the bug report.
As I have ubuntu, I may try to update xorg using [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"), but as I am short on time, it may take a little while. If someone else does that please report back the results.

---

### Post by Agnwristos on 2012-10-18
The bug website states it is resolved.. If so can someone please share the solution with me?

This issue is what prevents me from using Linux.. I can not type which is the most essential aspect of using a computer.

---

### Post by nabukadnezar43 on 2012-10-31
```
xkbcomp -xkb $DISPLAY /home/username/myxkbmap
```Now you'll have a file named myxkbmap in your home directory. Open that file with your text editor and edit the key <caps> entry like this:

  ```

  key <CAPS> {     repeat=no,     type[group1]="ALPHABETIC",     symbols[group1]=[ Caps_Lock, Caps_Lock ],     actions[group1]=[ LockMods(modifiers=Lock), Private(type=3,data[0]=1,data[1]=3,data[2]=3) ]   };

```Save it. And then reload it:

```
xkbcomp /home/username/myxkbmap $DISPLAY
```

You can write an executable startup script so that you won't have to do this everytime X starts.

Like:

```
#!/bin/sh

xkbcomp /home/username/myxkbmap $DISPLAY
```

Save this with any name you want. Make it executable. And make it one of your startup programs.

---

### Post by Driiper on 2013-06-10
> **nabukadnezar43 said:**
> Snip....

Holy ****, i must revive thread to tell you that your a god.

Thanks!

---

