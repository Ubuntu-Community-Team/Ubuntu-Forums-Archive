---
title: "Caught signal 11. Server aborting after installing new Gnome theme (can't startup)"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by sebas7033 on 2007-07-26
Hi, 
Through the Gnome Art manager I downloaded a login theme, splash screen, background and window theme. Now I cant get ubuntu to start. I do see the Ubuntu progress bar, a blue screen, a black one and than the little "waiting/loading" circle. 

When I sellect Ubuntu, kernel, 2.6.20-16-generic (recovery mode) and wait untill the "terminal" comes up (it does show me as user) but I don't know what to type here.

If I run my live CD in safe graphics mode I see the following error at the bottom.
Fatal server error:
Caught signal 11. Server aborting

Through the file browser on my live CD (in normal mode) I can see the themes that I downloaded, but I can't make any changes since I'm not the "owner" when I work with the live CD.

Any advise for this newbie?

---

### Post by petedct on 2007-07-26
Sounds to me like the xserver is messed up. From the terminal try this.
```
sudo dpkg-reconfigure xserver-xorg
```
After that you'll be asked questions about your PC's configuration.
I just hit enter for every question and that gets x back up and running for me.

---

### Post by sebas7033 on 2007-07-26
Thank you for your reply.
I tried your code and was able to configure the file. However, I was not able to get my graphics back.
Can I somehow, just delete and reset the themes I installed?

---

### Post by petedct on 2007-07-26
Sorry I could not help you out sebas7033. I'll have to yield to the pros now.Good luck.

---

### Post by sebas7033 on 2007-07-26
No problem, I will just back up my data and re install ubuntu (as a windows user I've got used to that process)

---

