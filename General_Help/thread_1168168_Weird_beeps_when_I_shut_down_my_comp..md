---
title: "Weird beeps when I shut down my comp."
date: 2009-05-23
forum: General Help
---

### Post by Nicka727 on 2009-05-23
Whenever I shut off my computer my computer beeps which I think is coming from the motherboard and not the speakers. Also when I get a new email in Mozilla Thunderbird, the same thing happens. 

PS: How do I check my CPU usage?

---

### Post by albert ozzy on 2009-05-23
Modify the file  /etc/modprobe.d/blacklist to include this line: > blacklist pcspkr

PS: you can check your cpu usage from System Monitor located at System> Administration. Or simply run > gnome-system-monitor from terminal if you're using Gnome Desktop Environment.

---

### Post by Nicka727 on 2009-05-23
```
nick@ubuntu:~$ /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: No such file or directory
nick@ubuntu:~$ blacklist pcspkr 
bash: blacklist: command not found
nick@ubuntu:~$ 


```

Sorry, I've only been using Ubuntu for 2 days so I'm a little confused.

---

### Post by c/Kr3t on 2009-05-23
> **Nicka727 said:**
> ```
nick@ubuntu:~$ /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: No such file or directory
nick@ubuntu:~$ blacklist pcspkr 
bash: blacklist: command not found
nick@ubuntu:~$ 


```

Sorry, I've only been using Ubuntu for 2 days so I'm a little confused.

type sudo gedit /etc/modprobe.d/blacklist

---

### Post by Nicka727 on 2009-05-23
I added it, but It didn't work =(.

---

### Post by mikewhatever on 2009-05-23
The obvious question to ask first is, have you tried disabling the beeps or sound alerts from System->Preferences->Sounds?
If you want to disable the beep by blacklisting the pcspkr module, run the following command:
**sudo echo >> /etc/modprobe.d/blacklist.conf 'blacklist pcspkr'**

Edit: Since you started editing the file manually, please back it up with
**sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf-backup**

---

### Post by Nicka727 on 2009-05-23
Fixed. Thanks guys. ):P

---

