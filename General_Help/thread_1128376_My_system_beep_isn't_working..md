---
title: "My system beep isn't working."
date: 2009-04-17
forum: General Help
---

### Post by feedmecereal on 2009-04-17
I see that a lot of people are asking how to stop the computer from beeping but I actually want it to beep occasional. But I have heard no beep at all since I upgraded to Intrepid (I am currently using Jaunty and no beep now either). I really want my computer to beep when I get a new email or when someone replies when I use Pidgin.

Someone in a chatroom suggested that I could make it beep on demand by typing "echo -e "\b"" but that didn't work then either.

---

### Post by sdennie on 2009-04-17
I can't imagine why you'd want this behavior but, you probably want to look in the System->Preferences->Sound application.  Specifically the second tab.

---

### Post by feedmecereal on 2009-04-17
I looked at that tab and I could not find anything to do with system beep (or whatever its called). There is an "alert sound" but that comes from my external speakers. I am specifically refering to the speaker inside the computer.

I want it to beep so that I know when someone IM's or emails me when I am not at the computer and my monitor is off.

---

### Post by Therion on 2009-04-17
Going by memory here, but if you go to System/Preferences/Sound/Sounds (tab) and enable "Play alert sounds", does that do it?

---

### Post by ibuclaw on 2009-04-17
Is this Motherboard Beep or an OS/Desktop Beep?


1) Motherboard Beep
Just suggesting the obvious, but:
```
lsmod | grep pcspkr
```
Does that output anything?
If the answer is **no**, then
```
sudo modprobe pcspkr
```


2) OS/Desktop Beep
Exactly the way sdennie and Therion have suggested.

---

### Post by sdennie on 2009-04-17
There are many reasons why your system (or application) wouldn't beep.  Those reasons could range from tinivoles modprobe stuff to applications not being configured to beep to, literally compiz.  I think you are going to have to provide more information if this initial diagnosis/solutions doesn't help us.

---

### Post by feedmecereal on 2009-04-17
Therion: I did have that box checked. Besides, all the alert sounds seem to deal with the sounds comming from my external speakers.

tinivole: ```
$ lsmod | grep pcspkr
pcspkr                 10496  0 

```

sdennie: I would be happy to provide everyone with more information but I'm still not all that familiar with some of the inner-workings of Ubuntu. What info do you need?

---

### Post by sdennie on 2009-04-17
The "lsmod" brought back good news so, that's one thing less to consider.  With that output, your speaker is capable of producing sounds, it just isn't.  So, it's a software problem.  Much harder to figure out.  I recommend installing the beep program.  If it doesn't produce sound then, it's easier to localize the problem:

```

sudo apt-get install beep
beep --debug

```

---

### Post by feedmecereal on 2009-04-17
> **sdennie said:**
> The "lsmod" brought back good news so, that's one thing less to consider.  With that output, your speaker is capable of producing sounds, it just isn't.  So, it's a software problem.  Much harder to figure out.  I recommend installing the beep program.  If it doesn't produce sound then, it's easier to localize the problem:

```

sudo apt-get install beep
beep --debug

```

I installed beep (it was not already installed). Yet, I still cannot get my computer to beep.

```
$ beep --debug
[DEBUG] 1 times 200 ms beeps (100 delay between, 0 delay after) @ 440.00 Hz

```

---

