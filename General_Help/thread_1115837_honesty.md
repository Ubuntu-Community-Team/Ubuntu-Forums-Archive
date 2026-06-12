---
title: "honesty"
date: 2009-04-04
forum: General Help
---

### Post by george703 on 2009-04-04
all right;
time to come clean.
has anyone got ubuntu working right.

i cant update
download just about anything
cant check hotmail
i cant even play webkinz.

i am at a lose as what to do. i spend all my time trying to resolve issues and it is wearing me out.

is there a source for answers so i dont have to spend all my time fixing or trying to do something?

---

### Post by cavedog on 2009-04-04
It can be frustrating, I know.  My first experience with Ubuntu was less than stellar.  But it has steadily improved.  Sometimes new bugs get created by fixes for other bugs, but generally it's forward movement.  

I've had a very good experience with Ubuntu/Xubuntu 8.04 LTS.  It has worked on every machine I have tried it on, from a 300Mhz 256M Aptiva, to a 3Ghz 512M homebuilt with half dozen in between.  It installed without a glitch on my Dell B120 Inspiron.

Perhaps if you provided a little more information, i.e., what version of Ubuntu, your hardware, and other clues, the knowledgeable ones here can help you out.

---

### Post by ajgreeny on 2009-04-04
Wireless or cable network, what video card, what is the overall spec of the machine, and what exactly are the problems.  It's no good saying nothing works and expecting us to tell you why; we need a lot more information, though from your list, it sounds as if it's all related to your web connection.

But honestly, I have Ubuntu running without any real problems at all.  My hardware suits the system, I agree, but the only time I get a problem is when I have read about something and tried to change my setup and upset the configuration.  My sound, video & graphics, in fact everything works so smoothly it's actually amazing for a system which, let's face it, is all put together mainly by amateurs.  Persevere and you will be well rewarded with an OS worth its weight in gold.

---

### Post by mb_webguy on 2009-04-04
Actually, *most* people have no problem with Ubuntu.  The problems you see posted on this forum represent only a small fraction of the people using Ubuntu.

It's unfortunate that you're in this minority, but posting threads with a vague subject line complaining about having problems without providing any specifics regarding your system isn't likely to get you the help you need.

---

### Post by issih on 2009-04-04
From looking at your other posts you actually have just one issue.

That you can't access the software repositories.

This is your only issue.

Once that is resolved, installing flash will solve webkinz, and updates all come from the same repositories so that will be fine.

To resolve that first tell us if you can access the internet from the pc (to remove lack of connection as a possible reason for the failure) and then post the output of:

```
cat /etc/apt/sources.list
```

as requested in one of your previous threads. (Do note the space though, cat is the program that will echo the contents of a file to the screen, the rest is the file we want to see)

---

