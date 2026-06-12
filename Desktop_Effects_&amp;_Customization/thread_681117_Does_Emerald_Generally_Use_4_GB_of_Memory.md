---
title: "Does Emerald Generally Use 4 GB of Memory?"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2008-01-28
Hi,

I just got back from work and noticed my PC was uncharacterstically sluggish.  I opened system monitor and saw that emerald was using 4GB of memory.  I don't know if this is what was causing the slowdown but is this generally the case?

Also, if it is, does anyone know how I can scale that back without sacrificing too much performance?

Thanks,
Douglas

---

### Post by czeckk on 2008-01-28
Hey,
      I'm just looking through these posts for the heck of it, but emerald only takes up about 900kb on mine... is it still like this after a reboot? if so, i'd go to synaptic and completely remove emerald and then reinstall it...

---

### Post by dustigroove on 2008-01-28
Emerald pretty consistently trends at 14.2 MB for me on my desktop machine. I would imagine something is very wrong if it is using 4 GB consistently.

Cheers,

---

### Post by arsenic23 on 2008-01-28
I'd remove the .emerald folder from your home directory and configure it from scratch again, see if that helps.

---

### Post by djrobthaman on 2008-01-28
Well... just restarted and now emerald is running at about 1.6MB.  So I guess I'll keep my fingers crossed.

Thanks for all the replies.

---

### Post by djrobthaman on 2008-01-29
I guess crossed fingers aren't enough to stop the almighty memory gobbling powers of emerald.  I woke up this morning to find its memory usage back up at 4.0gb.

I suppose I'll delete the .emerald file and reconfigure it but I just have that feeling that it isn't going to work (I really really hope it does though).  But on the off chance that it doesn't, any more suggestions?

Thanks

---

### Post by persona_o on 2008-01-30
I just noticed the same thing, I was trying to get the fancy compiz effects working. They work except for emerald - I can't seem to change themes using the theme manager. 

I'm pretty sure the memory usage is some kind of bug though - I don't have 4 GB of RAM, and the computer runs fine. According to the memory monitor app I'm only using 20%.

---

### Post by djrobthaman on 2008-01-30
Yeah,  I don't have that much RAM either.  I figured it had set up some virtual memory on my hard disk and showing the stats from that usage in addition to the RAM.

Also, the second time I saw it at 4GB the PC was performing well as far as I could see.

BTW, about changing themes in emerald, it's actually an odd process.  The way you're supposed to do it is start up the emerald theme management window and select the theme you want to apply.  Then you need to run emerald --replace.

So just selecting it in the themer will not do it.  Extremely annoying, but what can I say.  Until somebody decides to add a little "Apply Theme" button that executes that command (which I'm sure isn't any sort of a headache for anyone involved in the project) I guess we'll just have to do it the hard way.

---

### Post by dustigroove on 2008-01-31
> **djrobthaman said:**
> BTW, about changing themes in emerald, it's actually an odd process.  The way you're supposed to do it is start up the emerald theme management window and select the theme you want to apply.  Then you need to run emerald --replace.

So just selecting it in the themer will not do it.  Extremely annoying, but what can I say.  Until somebody decides to add a little "Apply Theme" button that executes that command (which I'm sure isn't any sort of a headache for anyone involved in the project) I guess we'll just have to do it the hard way.


Sounds like you definitely have an issue with Emerald then, whenever I select a different theme it applies instantly.

---

### Post by djrobthaman on 2008-01-31
Really?  The way I described applying themes is how I've had to do it from Feisty on up.

---

### Post by H_out on 2008-03-08
Whenever I have a duplicate window (for example, two instances of Firefox or two instances of the terminal), the memory for the emerald process jumps up to 4.0 GB.  Additional duplicates don't scale the memory.  As soon as I exit out of a duplicate, the memory drops down to 600 KB or so.

I'm running Xubuntu 7.10, and my xfdesktop process also says it's using 4 GB of memory.  I've attached a screenshot.  The memory for xfdesktop doesn't change with or without duplicate windows.

I don't have any serious performance issues...my system runs smoothly, even when emerald and xfdesktop are each at 4 GB of memory.

Does anyone know what's going on?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61983&stc=1&d=1204994202[/IMG]

---

### Post by H_out on 2008-03-08
Just figured out something else: in order to make the emerald memory jump to 4 GB, I have to have atleast one Firefox window open!  Here are the steps I took, I'd like to konw if anyone else can reproduce this:

(Make sure you have no duplicate windows when you start this.)

- Open a Firefox window.
- Open two instances of the terminal.
- View the emerald memory.  Mine is at 4 GB.
- Exit out of one terminal.  My emerald memory drops.
- Open another terminal.  The emerald memory jumps to 4 GB.
- Exit out of Firefox.  The emerald memory drops.

Again, my xfdesktop process stays at 4 GB.

I'm running Firefox 2.0.0.12.  I have one extension that opens my home page for newly opened tabs, but that's all.

---

### Post by 22flames on 2008-03-08
remove and reinstalle cause thats freaky

---

### Post by H_out on 2008-03-08
I've removed and reinstalled emerald, and I'm still getting the same results.

Can anyone else reproduce this problem by following the steps from my previous post?

---

### Post by RussellGee on 2008-03-08
Your not the only one experiencing this, I have seen a few posts about this today.

I would file a bug report with the info you have posted here.

Also do you know if there has been any updates for emerald or compiz? If there has been then thats most likely the source of the problem.i havent noticed any but im on hardy most of the time.

---

### Post by dustigroove on 2008-03-08
> **H_out said:**
> Just figured out something else: in order to make the emerald memory jump to 4 GB, I have to have atleast one Firefox window open!  Here are the steps I took, I'd like to konw if anyone else can reproduce this:

(Make sure you have no duplicate windows when you start this.)

- Open a Firefox window.
- Open two instances of the terminal.
- View the emerald memory.  Mine is at 4 GB.
- Exit out of one terminal.  My emerald memory drops.
- Open another terminal.  The emerald memory jumps to 4 GB.
- Exit out of Firefox.  The emerald memory drops.

Again, my xfdesktop process stays at 4 GB.

I'm running Firefox 2.0.0.12.  I have one extension that opens my home page for newly opened tabs, but that's all.


Following the above steps emerald seems to be playing nice on my machine, it stays around 6 MB. (Note - I do have an updated Firefox installed through Ubuntuzilla on my machines)


I have the following packages installed:

```
compiz 1:0.6.0+git20071008-0ubuntu1.1
emerald  0.3~git20070717-0ubuntu1
firefox 2.0.0.12
```--

---

