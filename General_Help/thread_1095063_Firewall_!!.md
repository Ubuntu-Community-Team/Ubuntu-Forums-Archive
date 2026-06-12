---
title: "Firewall !!"
date: 2009-03-13
forum: General Help
---

### Post by dejay68 on 2009-03-13
Coming from windows xp I am aware of the need to be safe on the net !!

I hear that it is not that necessary on ubuntu is that correct?

Also I hear the inbuilt firewall has everything left open - hence usless ! is this correct ? I installed firestarter and it says i have a number of serious events (altho i just updated some progs) 
Q. Do I need a firewall & how can i auto setup the inbuilt one
for info I ran Zone alarm in windows which was very user fiendly.
Thanks in advance ;)

---

### Post by ushills on 2009-03-13
Have a read of this, it will enlighten you.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by t0p on 2009-03-13
Linux is very different to Winderzz when it comes to security.  There's no need for anti-virus software (unless you want to scan for Winderzz malware) as there are few/no Linux viruses out there.  And a firewall is unnecessary unless you are running web-facing services.

If you *are* running web-facing services, you should read the documentation for the Ubuntu firewall (I think **ufw** is the default firewall for Intrepid) and make sure you get the policies right for the ports you have open.   But, at the end of the day, Ubuntu is significantly more secure than Winderrz, and the security culture that you found necessary when running XP is not needed.

---

### Post by dejay68 on 2009-03-14
How about bit torrent ? I understand that this is a potential way that others can get access to your pc, and how would you be able to scan the downloaded data for viruses or am i misunderstanding that microsoft aimed viruses dont infect ubuntu ?
Thanks again Guys and G:popcorn:irls

---

### Post by Pfredpfudpucker on 2009-03-14
Good thought, but the design features in Linux make it difficult for viruses to attack Linux.  The primary protection you can exercise is never use root for routine tasks.  Ubuntu enforces this policy by not allowing log-in as the root user.  Instead, when you need to work as root, attempting to do so will require giving the password you entered when you installed the OS.  The best policy for day-to-day operation is to go to "users and groups" (System>Administration>Users and Groups) and set up another user for day-to-day use.

Also, read and study the security sticky.

---

