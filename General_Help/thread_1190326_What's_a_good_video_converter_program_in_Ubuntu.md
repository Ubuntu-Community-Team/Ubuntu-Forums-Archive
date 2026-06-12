---
title: "What's a good video converter program in Ubuntu?"
date: 2009-06-17
forum: General Help
---

### Post by Shibblet on 2009-06-17
I feel like Pacino.  "Every time I try to get out, they pull me back in."

I really am trying to accomplish all of my tasks with Ubuntu, instead of Windows.  I am looking for a good video converter program.  All of the video converters for Ubuntu (Linux) are either command line or blank areas to be filled in that work "like" a command line.

One thing I can say for Windows...  Even the free-ware, or open-source programmers seem to make much more user friendly applications.  To name a few that I use.

DVD Shrink 3.2
DVD Decrypter 3.5.4.0
VirtualDub 1.8.8
DGDecode 1.54

All of these programs are point and click simple.  And really don't require a lot of tweaking.

So, what's my option?  Run Wine?  I'd like to use Linux based programs, but it's a bit like driving a stick-shift when I'm used to an automatic.

---

### Post by howefield on 2009-06-17
> **Shibblet said:**
> I am looking for a good video converter program.

What format do you want to convert from and to ?

> ...All of these programs are point and click simple.  And really don't require a lot of tweaking.

Handbrake ? Website is handbrake.fr 

Doesn't get much more pointy and clicky. Suit you down to the ground ;)

---

### Post by Therion on 2009-06-17
Based on the list of Windows applications in your post I'm going to suggest the following tutorial.  I've used it many times with great success for backing up my video library.

[http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/)

A couple apps from the repositories, a few clicks to set things up, and you're off and running.

---

### Post by Cheesemill on 2009-06-17
Avidemux, it's in Add/Remove programs.

---

### Post by maheshasolkar on 2009-06-17
+1 for K9copy... based on my experience about a year back.

---

### Post by Chronon on 2009-06-18
Mencoder and WinFF.

---

### Post by ActiveFrost on 2009-06-18
ffmpeg + WinFF ( fast and powerful, though, user interface could be better :D ).

---

### Post by Shibblet on 2009-07-06
What I am trying to do is Rip a DVD.ISO to the hard drive, then I can decode it with K9, and convert it with AviDemux.

I can't find a good DVD.ISO reader.  If a DVD (Like "The Longest Yard") has copy protection, K9 refuses to read it.  DVD Decrypter did a pretty good job, and DVD Fab did a wonderful job of removing copy protection.

Now, I am not trying to steal movies, I do this with my own DVD's.  I have about 500 of them, and I am going to put them all on HD.

---

### Post by Bradj47 on 2009-07-06
> **ActiveFrost said:**
> ffmpeg + WinFF ( fast and powerful, though, user interface could be better :D ).

I couldn't get Win FF to work.

---

### Post by ju2wheels on 2009-07-06
DVD9 to DVD5 (aka what Dvdshrink does): Dvd95, k9copy
DVD to avi/divx/... : Handbrake (getdeb.net)
convert X to X: Avidemux, WinFF
convert X to DVD: Devede

One thing to note with DVDs, I would recommend you have installed libdvdcss2 from medibuntu.org.

To view the dvd.iso without burning:

```
sudo mount -o loop /path/to/dvd.iso /media/cdrom0
```

Right click on the cd that appeared on your desktop and select to play with your media player of choice.

To unmount it:
```
sudo umount /media/cdrom0
```

---

### Post by Shibblet on 2009-07-07
> **ju2wheels said:**
> One thing to note with DVDs, I would recommend you have installed libdvdcss2 from medibuntu.org.

You're my hero!  I installed libdvdcss2 and K9 works beautifully!  Thank you very much!

---

### Post by Shibblet on 2009-07-07
Except now, when I extract the MPEG files from the DVD, I get a 0 byte file in the directory where I've extracted them to.  Doesn't seem to be extracting.

---

### Post by abhi_69 on 2009-07-07
+1 for winFF.
it works like charm for me. i supports many popular video format to convert.

---

### Post by paul.gevers on 2009-07-07
> **Bradj47 said:**
> I couldn't get Win FF to work.

I am interested in this problem. What happened/what went wrong? If you want to I invite you file a bug in the upstream [bug tracker]("http://code.google.com/p/winff/issues/list").

---

### Post by dka on 2009-07-07
Handbrake all the way.  It doesnt get simpler and there are even tutorials out their to cluster Handbrake operations to get faster processing power.

---

