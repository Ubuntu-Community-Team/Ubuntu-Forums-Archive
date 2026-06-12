---
title: "No sound on Hulu or Youtube using Dell Latitude"
date: 2009-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfman1221 on 2009-02-26
I'm  new to Ubuntu, so I am not really sure why I cant hear anything on Hulu or Youtube. Also, whenever I return to a screen showing a video on either site I see simply a white screen and no video. If anyone knows how to fix these two problems, I would really appreciate it.

---

### Post by sirebral on 2009-02-26
Are you using pulseaudio?  It has been causing a lot of problems.

---

### Post by wolfman1221 on 2009-02-26
This is what I am using.


"HDA Intel (Alsa Mixer)"

---

### Post by sirebral on 2009-02-26
You are probably using pulseaudio.

Since you are a noob I will give you a walk through to open up the System Monitor and how to find out if you are running pulseaudio.

Open a Terminal:

**Accessories** > **Terminal**

Enter the system monitor command:

**gnome-system-monitor**

You should receive a window that functions much like the Windows Task manager.  Click on the **Process** tab and look for pulseaudio.

---

### Post by wolfman1221 on 2009-02-26
Okay, I found it.Now what?

 I also received this message in my terminal.


"** (gnome-system-monitor:12125): WARNING **: SELinux was found but is not enabled."

---

### Post by sirebral on 2009-02-26
No worries on the message.  So did I.

Kill Pulse Audio.  Don't worry, it will come back when you restart.  You should also quit Fire Fox and look to see if you have a Fire Fox process hanging back after you quit.  Then kill that.  Then restart Fire Fox and try your media again.

If this doesn't work it might be a video problem.

P.S. To kill a process, **right click** on it and the choose **Kill Process**.

---

### Post by wolfman1221 on 2009-02-26
Thanks. I was wondering if you knew if it was possible to have Hd like quality audio in ubuntu?

---

### Post by wolfman1221 on 2009-02-26
I just tried that whole kill process thing, and it killed my sound.

---

### Post by sirebral on 2009-02-26
:P

That sucks.  Well, you can type

**pulseaudio -D**

in the terminal and get it back.  Not sure what your problem is then.  Sorry.

---

### Post by sarahlizz3 on 2009-03-22
Sirebral - I just had the same issue and that fixed it, so wanted to say thanks!

---

### Post by karenyyng on 2009-03-23
I had Dell XPS M1210 and that also fixed my sound issue :) 
Thanks.

---

