---
title: "Cant load up Desktop"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Brokenrgv on 2006-06-21
just did a reboot and after i login the screen stays on that brown backdrop and no gnome launcher starts,it just hangs on the brown screen, id just format and start agin but ive just started getting ubuntu just the way i want it,i can login and start a failsafe xterm session fortunately, can someone lend a hand it would save quiet a few hrs of work for me.
when i try logging into the failsafe gnome it says "could not find the GNOME installation.Running the "Failsafe xterm"session instead.

---

### Post by Kurt_Alan on 2006-06-21
****

Are you referring to the screen that asks for your user name and password? What happens when you enter this information?

---

### Post by Brokenrgv on 2006-06-22
yer that screen comes up ok allows me to enter loggin and password then changes to that brown screen that usually has the graphical bar that shows everything loading,but not in my case was working fine but just broke on me.
ps currently typing this from laptop in case your wondering

---

### Post by manup on 2006-06-25
I seem to have the same problem. Gnome does not hang it just waits for a very long period of time and then finally loads up. I ran netstat -natp during this wait and that is the result:
---cut---
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      1 192.168.0.2:43406       127.0.0.1:16001         SYN_SENT   5614/gnome-session  
tcp        0      1 192.168.0.2:43407       127.0.0.1:16001         SYN_SENT   5668/gnome-settings 
---cut---
This seems to be the problem in my case. Gnome just waits for this timeout. Any ideas how to change it? The tcp port was 16000 the first time I tried it, so it seems to dynamically change...

---

### Post by Brokenrgv on 2006-06-25
i fixed it by format re install :( a little drastic but couldnt wait

---

