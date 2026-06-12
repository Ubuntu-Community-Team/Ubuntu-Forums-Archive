---
title: "Reducing network activity."
date: 2006-06-30
forum: Desktop Environments
---

### Post by Rizado on 2006-06-30
I'm going away this summer and I'll bring my computer. There's no internet connection so I'm going to use my gprs phone as a modem to check emails etc. The phone connection is already working but I's like to turn everything that access the internet off because I have to pay per kb I transfer. 

I'm using Kubuntu. the first thing that comes to my mind is the update notifier so I'd like to turn it off but don't know how. Also if you think of something else please post here, even if you don't know how to turn it off. Thanks.

---

### Post by woedend on 2006-06-30
sudo chmod -x "/usr/bin/update-notifier"
will keep it from running on next boot.  If you want it back remember to use +x instead. I'm not sure what else ubuntu uses by default that would access the net.

---

### Post by Rizado on 2006-07-03
Ok done that now and it seems to work, but it's called "adept_notifier" in kubuntu. Thanks

---

### Post by Rizado on 2006-07-23
Well it didn't work just disabling adept-updater, apt tried to do apt-get update all the time anyway so I moved sources.list. Also I couldn't use firefox becuase it searched for new updates and I can't disable it. (The searching is several 100kb large, stupid firefox) With konqueror i didn't have this problem.

---

### Post by fragos on 2006-07-23
If you ever enabled an NTP server for time synchronization you may want to turn that off as well.  You can further cut down email traffic by using a gmail account.  Gmail filters spam and if you configure it for POP access it won't forward the spam.  A net based spam filter server so to speak.

---

### Post by Rizado on 2006-08-05
> **fragos said:**
> If you ever enabled an NTP server for time synchronization you may want to turn that off as well.  You can further cut down email traffic by using a gmail account.  Gmail filters spam and if you configure it for POP access it won't forward the spam.  A net based spam filter server so to speak.Ok, I will remember that until next time. I solved the email problem with using a brand new spam free email and set thunderbird to only download the title.

---

