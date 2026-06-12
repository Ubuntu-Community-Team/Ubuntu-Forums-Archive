---
title: "adding &quot;echo 1024 &gt; /proc/sys/dev/rtc/max-user-freq&quot; to your system startup script"
date: 2005-11-05
forum: Desktop Environments
---

### Post by QWERTY on 2005-11-05
How do I add "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to my system startup scripts so it is executed during startup.

Thanks

---

### Post by adwait on 2005-11-05
uuh......this has been discussed umpteen times on the board, please use the search feature before posting. Anyway, here's what you do:
1)Add that line to a text file and save it.
2)Make it executable. For that open a terminal and:
```
chmod +x <filename>
```
3)Move it to /etc/init.d/
```
sudo mv <filename> /etc/init.d/
```
3)Open rcconf
```
sudo rcconf
```
Now check the box against the file you just created using space bar. If it says command not found for that, use
```
sudo apt-get install rcconf
```
then repeat the step.

---

### Post by riggsd on 2005-11-05
It is easier and more "correct" to use sysctl.

1. [COLOR="Red"]sudo sysctl dev.rtc.max-user-freq=1024[/COLOR]   # to make it work now

2. [COLOR="Red"]sudo gedit /etc/sysctl.conf[/COLOR]   # add the line "[COLOR="DarkRed"]dev.rtc.max-user-freq=1024[/COLOR]" to make it work on reboot

See sections 1 and 2 of this [article on sysctl and /proc]("http://ipsysctl-tutorial.frozentux.net/chunkyhtml/index.html") for a good overview of sysctl.

---

### Post by QWERTY on 2005-11-07
[QUOTE=adwait]uuh......this has been discussed umpteen times .....[/QUOTE]

Actually I searched for it, I really did, but found nothing.

But thanx for your solution.

---

### Post by Joe_lurker on 2005-11-07
> sudo gedit /etc/sysctl.conf # add the line "dev.rtc.max-user-freq=1024" to make it work on reboot
Interesting.  I did this and I got "Key not found".  So I went to the other option.  Has this happened to anybody else?

-Joe

---

### Post by timeoff on 2005-11-07
[QUOTE=Joe_lurker]Interesting.  I did this and I got "Key not found".  So I went to the other option.  Has this happened to anybody else?

-Joe[/QUOTE]

In a similar vein to the above I found adding the line to sysctl.conf did NOT carry over a reboot :( 

T

---

### Post by QWERTY on 2005-11-15
I also found it's only the rcconf method, which carry over from reboot :-k .

---

