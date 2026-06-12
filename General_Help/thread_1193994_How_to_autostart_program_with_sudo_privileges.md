---
title: "How to autostart program with sudo privileges?"
date: 2009-06-22
forum: General Help
---

### Post by Lockheed on 2009-06-22
I need conky to autostart with ubuntu with sudo privileges. 
How do I do it?

---

### Post by t0p on 2009-06-22
In Jaunty, go to **System > Preferences > Startup Applications** and add Conky to the list.

In previous versions, it would be under **System > Preferences > Sessions** I think.

---

### Post by VCoolio on 2009-06-22
That wouldn't give conky sudo privileges. Also I think it's a very bad idea to run conky as root, as anyone can change your conkyrc file and let conky run any command then. What do you want conky to display that you need root permission for?

---

### Post by Lockheed on 2009-06-22
t0p, kudos for reading with understanding.

VCoolio, I need conky to run cpupowerd (to read cpu voltage) which only runs with sudo.

---

### Post by VCoolio on 2009-06-22
Depending on what cpupowerd can do you can run "sudo chmod u+x /path/to/cpupowerd" (check the path with "which cpupowerd", probably /usr/bin), but that would maybe be a security risk.
Or (very expansive) make a cronjob that puts the output of your command in a text file regularly which conky then can read (something like "sudo cpupowerd -s | grep VID | cut -f2 -d: > /home/username/.tmpcpu.txt" and then in conky something like "execi variable-in-seconds cat ~/.tmpcpu.txt".

---

### Post by Lockheed on 2009-06-23
I tried the first method but it did not work. The cpupowerd was in /usr/sbin/  Is this location probable?

I am a bit weary about the second method. Apart from the fact that I know nothing about writing or running cron scripts, I am afraid that:
1. this txt will either be written once and never updated so conky would only know the initial voltage from when the script was first run
2. or the file will swell to huge size with every new value written by cpupowerd

---

### Post by Lampi on 2009-06-23
Lockheed,

Use the first method, it will run cpupowerd with root privileges, so there is no need to use sudo. /usr/sbin is not part of you path environment as it is supposed to be. So if you want to run a binary placed in there you need to call it with full path: /usr/sbin/cpupowerd

---

### Post by Lockheed on 2009-06-23
> **Lampi said:**
> call it with full path: /usr/sbin/cpupowerd

Yes, that's what I did but I still don't get cpupowerd readout in conky as I do when I run "sudo conky"

---

### Post by Lockheed on 2009-06-24
Guys, it is not working for me. Any ideas?

---

### Post by Lockheed on 2009-06-26
bump

---

### Post by mister_p_1998 on 2009-06-26
If you REALLY want to run conky as root, use this method I use to do an auto shutdown in cron:

Sudo gedit /etc/crontab

@reboot root /usr/bin/conky

your .conkyrc file wont be found though its in your user area, you'll probably have to enter the full path to it:

@reboot root /usr/bin/conky /home/steve/.conkyrc

obviously your not called steve (are you?)

Steve

---

### Post by Lockheed on 2009-06-26
Hmm, this is still not giving me the readout but if I kill conky and run it by "sudo conky" it does show me the voltage. Strange.

---

