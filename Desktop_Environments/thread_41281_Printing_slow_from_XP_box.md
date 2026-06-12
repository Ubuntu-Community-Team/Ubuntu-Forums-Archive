---
title: "Printing slow from XP box"
date: 2005-06-12
forum: Desktop Environments
---

### Post by easy_target on 2005-06-12
Hello,

I have a printer setup on my Ubuntu box which is shared by two other XP machines.
However when I try to print from any of the XP boxes it takes AGES to start printing something. It takes forever for the application being used to print to even respond. After TWO AWFUL MINUTES it starts printing. What can I do to speed-up the process?
Totally newbie here.

Thanks in advance

---

### Post by intangible on 2005-06-17
Do you have it shared through CUPS (ipp/http) or SAMBA?

If you have it shared through SAMBA, try changing it to CUPS, it seems to be a cleaner way to do it.

---

### Post by Seandq on 2005-06-17
[QUOTE=intangible]Do you have it shared through CUPS (ipp/http) or SAMBA?

If you have it shared through SAMBA, try changing it to CUPS, it seems to be a cleaner way to do it.[/QUOTE]

I'll agree one hundred percent. CUPS Win32 printing is still much faster than SAMBA printing. If using CUPS, please let us known..and if using SAMBA, please consider a move to CUPS.

---

### Post by easy_target on 2005-07-13
I am currently using samba, mostly due to ignorance on how to set up CUPS for the XP box. Can someone give me directions? Thanks for the kind replies!

---

### Post by skirkpatrick on 2005-07-14
XP has a quicker response (almost normal) when printing directly to Cups whereas Win98 responds faster when printing through Samba.

Check out my post to this thread: [http://www.ubuntuforums.org/showthread.php?t=47963](http://www.ubuntuforums.org/showthread.php?t=47963) for setting up Cups and XP machines.

---

### Post by easy_target on 2005-07-14
It worked just fine, thank you very much! I even use it to connect a Xandros box in the other room in addition to the XP laptop my wife uses to work. I just have a question: My network is setup as DHCP. Can I use the computer name on the network instead of the IP to get it working? I don't know if the IP will change after a refresh...

---

### Post by skirkpatrick on 2005-07-14
I use my Ubuntu machine's name instead of it's IP for the same reason.  However, sometimes I can't access some of the machine's on the network by name.  Not sure why, maybe you need Samba setup for the NetBIOS stuff.

---

