---
title: "Linux Zombie Machines?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Luke771 on 2006-07-28
How big is the risk of a Linux box being hijacked by some "zombifier" programs?
How do I check if my PC has been hijacked?
What to do in the eventuality that it is?

---

### Post by ardchoille on 2006-07-28
Here are the steps I take to improve security on a new install:

1) Replace the text in /etc/issue and /etc/issue.net with something that doesn't advertise the operating system

2) Add yourself to the wheel group and then:
```

sudo chown root:wheel /bin/su && sudo chmod 4750 /bin/su

```
This makes it so that anyone who is not in the wheel group cannot sit there all day and repeatedly call su to try and brute force the root password.

3) If you're not running a world-facing server, add this to /etc/hosts.allow: [COLOR="Red"]ALL: 127.0.0.1[/COLOR] and add this to /etc/hosts.deny: [COLOR="Red"]ALL: ALL[/COLOR]

4) Install and use rkhunter, chkrootkit and tripwire

5) Close all services that you aren't using

6) Install Firestarter and tweak firewall settings

I have been accused of "security overkill", but computer security is a process, not a destination :)

---

### Post by HAARP on 2006-07-28
Who would want to "zombify" Linux machines when he can have far more Windows machines much easier?

---

### Post by ardchoille on 2006-07-28
> **HAARP said:**
> Who would want to "zombify" Linux machines when he can have far more Windows machines much easier?

That is a very good point :)

---

### Post by HAARP on 2006-07-28
> **ardchoille said:**
> That is a very good point :)

Especially since Windows users are less prone to notice that their computer is infected

---

### Post by Luke771 on 2006-07-28
OK, taht's really a good point, the risk of being hijacked running Linux is not so high because hijackers wouldn't target Unix machines in the first place.

What about viruses then? I'm not running any anivirus on my Linux box (not on the windows machine either, but that belongs in a Windows forum) 

How great is the risk of being virus infected running Linux, and more specifically specifically Ubuntu 6.06?
Are there many virus out there?
How easy is it to get one?

I've never really understood why people spread viruses on the net, the only thing I can think of is that the same people who sell antivirus software dose that.

I don't think that *nix people would use such a way to increase the number  of support people being hired, but it's not impossible...

Anyway,
How does it look right now?
Do we need to worry about Linux viruses?

---

### Post by hw-tph on 2006-07-28
Watch out for weak passwords. Really. For example you have an account called test with an easily guessed password - like "test" - you will be rooted in no-time if you run sshd on the standard port. Anyone who has their computer unprotected can see the logs of attempted logins from ssh bots - I have had literally hundreds a day. Don't fool yourself by saying that a user account has no means of doing anything harmful.


Håkan

---

### Post by LORD_PoLvO on 2006-07-28
from what ive heard there are scant few programs out designed to attack linux boxes and they attack certainm programs and they are verry old one of the reasons viriuses atc arent around much for linux macjhines is because there are so manny versions of linux aeround it would be to hard to program a virius that would mass infect linux users :0 wheras windows has monopolised therefore it is one unified ioperating system and its also verry pooorly constructed and esier for ppl to code viruses for  :0 plus who would want to make viruses for linux anyway manny of the virusus for windows are ppl attacking the monopoly  that is microsoft.

---

### Post by LORD_PoLvO on 2006-07-28
> **hw-tph said:**
> Watch out for weak passwords. Really. For example you have an account called test with an easily guessed password - like "test" - you will be rooted in no-time if you run sshd on the standard port. Anyone who has their computer unprotected can see the logs of attempted logins from ssh bots - I have had literally hundreds a day. Don't fool yourself by saying that a user account has no means of doing anything harmful.


Håkan



hw-tph is exactly right because with a simple user acount ppl can use commands like su to acess root and then your completely stuffed

---

### Post by Boomy on 2006-07-28
> **hw-tph said:**
>  Anyone who has their computer unprotected can see the logs of attempted logins from ssh bots - I have had literally hundreds a day. Don't fool yourself by saying that a user account has no means of doing anything harmful.


Håkan

I'm pretty new to Linux, where are the logs located?

---

### Post by hw-tph on 2006-07-28
The logs are in /var/log/. Keep an eye on auth.log if you use the default syslog configuration. You can use tools such as logwatch or logcheck to have them scanned and have anomalies reported (by mail) to you.

Also, a weak user account with no access to su or sudo may still use a local privilege escalation to gain root on the machine. An attacker with a shell is "local" even if the user sits on the opposite side of the planet...


Håkan

---

### Post by Boomy on 2006-07-28
Is this any reason to be concerned?

ul 23 12:03:08 localhost proftpd[9026]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - USER Administrator: no such user found from ns1.jimvaughan.com [207.5.115.111] to 192.168.0.100:21 
Jul 23 12:03:08 localhost last message repeated 2 times
Jul 23 12:03:08 localhost proftpd[9026]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - Maximum login attempts (3) exceeded 
Jul 23 12:03:19 localhost proftpd[9036]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - USER Administrator: no such user found from ns1.jimvaughan.com [207.5.115.111] to 192.168.0.100:21 
Jul 23 12:03:20 localhost last message repeated 2 times
Jul 23 12:03:20 localhost proftpd[9036]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - Maximum login attempts (3) exceeded 
Jul 23 12:03:31 localhost proftpd[9041]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - USER Administrator: no such user found from ns1.jimvaughan.com [207.5.115.111] to 192.168.0.100:21 
Jul 23 12:03:32 localhost last message repeated 2 times
Jul 23 12:03:32 localhost proftpd[9041]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - Maximum login attempts (3) exceeded 
Jul 23 12:03:44 localhost proftpd[9046]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - USER Administrator: no such user found from ns1.jimvaughan.com [207.5.115.111] to 192.168.0.100:21 
Jul 23 12:03:45 localhost last message repeated 2 times
Jul 23 12:03:45 localhost proftpd[9046]: localhost.localdomain (ns1.jimvaughan.com[207.5.115.111]) - Maximum login attempts (3) exceeded 

There are quite a few more of these attempts.

---

### Post by ardchoille on 2006-07-28
> **Luke771 said:**
> OK, taht's really a good point, the risk of being hijacked running Linux is not so high because hijackers wouldn't target Unix machines in the first place.

What about viruses then? I'm not running any anivirus on my Linux box (not on the windows machine either, but that belongs in a Windows forum) 

How great is the risk of being virus infected running Linux, and more specifically specifically Ubuntu 6.06?
Are there many virus out there?
How easy is it to get one?

I've never really understood why people spread viruses on the net, the only thing I can think of is that the same people who sell antivirus software dose that.

I don't think that *nix people would use such a way to increase the number  of support people being hired, but it's not impossible...

Anyway,
How does it look right now?
Do we need to worry about Linux viruses?

Have a read at this:
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by ardchoille on 2006-07-28
> **LORD_PoLvO said:**
> hw-tph is exactly right because with a simple user acount ppl can use commands like su to acess root and then your completely stuffed

This is one good reason why the admin on the Linux box should add themself to the wheel group and then do:
```

sudo chown root:wheel /bin/su && sudo chmod 4750 /bin/su

```
so normal users will get a permission denied error when they try to use su. This keeps people who don't have admin rights from sitting there trying to brute force the root password.

---

