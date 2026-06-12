---
title: "Random crash (not the needle in the haystack question you expect)"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Tylerofl on 2006-06-20
-AMD64 build, Dapper Drake, fully updated
-GeForce FX 5700LE, using the Nvidia drivers

At any point when I'm using this operating system (not constantly, but often enough to really get on my nerves), it could be ten minutes into it, or two hours into it, the system will just completely freeze up. If music was playing, it'll endlessly loop a bit of whatever is playing. Ctrl+Alt+Backspace doesn't do anything, etc etc, the only way to get it running again is the big fat restart button.

The only thing consistent in each case is GAIM running. I don't think it's the problem, but it's all I've been able to gather. I've had this problem since I first switched to Ubuntu (it didn't happen on Kubuntu, but I'd take a bat to the face before switching back KDE), and hoped each update would fix it, but no go.

I'm not asking what the problem is, it could be a billion things (but if anyone has an idea...). I'm asking if there's a way I could look into it. Some kind of log file, maybe something running in the background to detect it, I dunno. There's got to be something.

---

### Post by bikeboy on 2006-06-20
Well /var/log/ is where you will find most logfiles. Hard to recommend which one to look at exactly but have a look at the Xorg logs for sure.

---

### Post by Tylerofl on 2006-06-20
Whoa, that's a lot of really big text files. What kind of message am I looking for regarding a crash? There are plenty of error-type messages here, but I assume they're ones the OS overlooks, because none seem significant enough to cause a complete freeze.

---

### Post by bikeboy on 2006-06-23
Sorry I didn't get back to you. In the xorg logs I think there a codes, might be listed in the file. eg. WW for warning, search for that.

---

### Post by txmail on 2006-06-23
I had a head scratching issues like this in the past. I would check the logs and nothing would really be in there from what caused the crash. It took allot of testing but oddly enough it was narrowed down to my power supply. Might want to check it out if there are no error logs. ](*,)

---

