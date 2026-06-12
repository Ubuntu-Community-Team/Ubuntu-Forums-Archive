---
title: "am I being hacked?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Houman on 2006-09-26
Hello there, 
couple of days ago I got my router set up with dyndns and set up ssh server on my computer. I was pretty thrilled that I can ssh from anywhere without having to remember my IP, until I happened to look at my /var/log/auth.log file. It looks like someone is trying to brute force their way into my computer through my ssh. Here is a snippet (there is sooo much more):

```

Sep 23 17:30:42 localhost sshd[9291]: Did not receive identification string from 203.145.137.54
Sep 23 17:31:34 localhost sshd[9322]: Invalid user bart from 203.145.137.54
Sep 23 17:31:34 localhost sshd[9322]: (pam_unix) check pass; user unknown
Sep 23 17:31:34 localhost sshd[9322]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:31:36 localhost sshd[9322]: Failed password for invalid user bart from 203.145.137.54 port 50869 ssh2
Sep 23 17:31:39 localhost sshd[9327]: Invalid user jaap from 203.145.137.54
Sep 23 17:31:39 localhost sshd[9327]: (pam_unix) check pass; user unknown
Sep 23 17:31:39 localhost sshd[9327]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:31:41 localhost sshd[9327]: Failed password for invalid user jaap from 203.145.137.54 port 52163 ssh2
Sep 23 17:31:45 localhost sshd[9332]: Invalid user www from 203.145.137.54
Sep 23 17:31:45 localhost sshd[9332]: (pam_unix) check pass; user unknown
Sep 23 17:31:45 localhost sshd[9332]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:31:47 localhost sshd[9332]: Failed password for invalid user www from 203.145.137.54 port 53004 ssh2
Sep 23 17:31:50 localhost sshd[9337]: Invalid user andre from 203.145.137.54
Sep 23 17:31:50 localhost sshd[9337]: (pam_unix) check pass; user unknown
Sep 23 17:31:50 localhost sshd[9337]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:31:52 localhost sshd[9337]: Failed password for invalid user andre from 203.145.137.54 port 53771 ssh2
Sep 23 17:31:55 localhost sshd[9342]: Invalid user bjorn from 203.145.137.54
Sep 23 17:31:55 localhost sshd[9342]: (pam_unix) check pass; user unknown
Sep 23 17:31:55 localhost sshd[9342]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:31:57 localhost sshd[9342]: Failed password for invalid user bjorn from 203.145.137.54 port 54500 ssh2
Sep 23 17:32:00 localhost sshd[9347]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54  user=ftp
Sep 23 17:32:02 localhost sshd[9347]: Failed password for ftp from 203.145.137.54 port 55246 ssh2
Sep 23 17:32:05 localhost sshd[9352]: Invalid user jonas from 203.145.137.54
Sep 23 17:32:05 localhost sshd[9352]: (pam_unix) check pass; user unknown
Sep 23 17:32:05 localhost sshd[9352]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:07 localhost sshd[9352]: Failed password for invalid user jonas from 203.145.137.54 port 56030 ssh2
Sep 23 17:32:10 localhost sshd[9357]: Invalid user nisse from 203.145.137.54
Sep 23 17:32:10 localhost sshd[9357]: (pam_unix) check pass; user unknown
Sep 23 17:32:10 localhost sshd[9357]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:11 localhost sshd[9357]: Failed password for invalid user nisse from 203.145.137.54 port 56783 ssh2
Sep 23 17:32:15 localhost sshd[9362]: Invalid user peter from 203.145.137.54
Sep 23 17:32:15 localhost sshd[9362]: (pam_unix) check pass; user unknown
Sep 23 17:32:15 localhost sshd[9362]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:17 localhost sshd[9362]: Failed password for invalid user peter from 203.145.137.54 port 57505 ssh2
Sep 23 17:32:20 localhost sshd[9367]: Invalid user admin from 203.145.137.54
Sep 23 17:32:20 localhost sshd[9367]: (pam_unix) check pass; user unknown
Sep 23 17:32:20 localhost sshd[9367]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:22 localhost sshd[9367]: Failed password for invalid user admin from 203.145.137.54 port 58271 ssh2
Sep 23 17:32:25 localhost sshd[9372]: Invalid user andreas from 203.145.137.54
Sep 23 17:32:25 localhost sshd[9372]: (pam_unix) check pass; user unknown
Sep 23 17:32:25 localhost sshd[9372]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:27 localhost sshd[9372]: Failed password for invalid user andreas from 203.145.137.54 port 59058 ssh2
Sep 23 17:32:30 localhost sshd[9377]: Invalid user ebner from 203.145.137.54
Sep 23 17:32:30 localhost sshd[9377]: (pam_unix) check pass; user unknown
Sep 23 17:32:30 localhost sshd[9377]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:32 localhost sshd[9377]: Failed password for invalid user ebner from 203.145.137.54 port 59803 ssh2
Sep 23 17:32:35 localhost sshd[9382]: Invalid user helmut from 203.145.137.54
Sep 23 17:32:35 localhost sshd[9382]: (pam_unix) check pass; user unknown
Sep 23 17:32:35 localhost sshd[9382]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.145.137.54 
Sep 23 17:32:37 localhost sshd[9382]: Failed password for invalid user helmut from 203.145.137.54 port 60539 ssh2
Sep 23 17:32:40 localhost sshd[9387]: Invalid user horst from 203.145.137.54

```

The interesting facts are that all the attemps originate from the IP: 203.145.137.54 and that all the attemps are made within seconds of each other indicating a scripted and systematic attack. I did try to traceroute the IP but that didnt lead me anywhere.

Also the attacks continue for 10 minutes. Now the strange thing is that the next day, the same attack ocurred, and the same sequence of usernames were used in attempting to break into my ssh, starting with bart , jaap, www, .... this time the duration of the attack was 30 minutes. Also teh log file only shows information for the past two days, and on each day the ssh attacker was at work, so I am assuming this has been going on for a while.

Also I googled around and I found the attacker's IP in this link:
[http://danger.rulez.sk/projects/bruteforceblocker/blist.php]("http://danger.rulez.sk/projects/bruteforceblocker/blist.php")

Anyways this is getting weird so I am asking the community to lend me a hand please, 

Thank you,
Houman

---

### Post by whizbaby on 2006-09-26
put the line
ALL: 203.145.137.54
in your /etc/hosts.deny. Attacks by scripts are common (though not each one is a threat as you saw).
You can also add the IPs from the page you posted in the same manner (they try to detect the origins of brute-force attacks, thats why the IP is on the list).

---

### Post by Houman on 2006-09-26
hi whizbaby,

Thank you for your reply, its good to know its not something personal , although it seems someone is targetting me otherwise they wouldnt be doing this everyday.

/etc/hosts.deny would be a good quickfix, but shouldnt ssh block a host after it has attempted unsucessfully to login so many times? or is there any program that would prevent such brute force attacks from ssh? I searched around in the repo and couldnt find anything.

thanks again,
Houman

---

### Post by whizbaby on 2006-09-26
> **Houman said:**
>  although it seems someone is targetting me otherwise they wouldnt be doing this everyday.

For me this proves it's a dumb script run by idiots, otherwise the next day there would be another IP and a more elaborate list of usernames.
Look over the net to find scripts that block after 1,2,3 ... unsuccessful attempts to login from remote and add automatically to hosts.deny, you'll get additional information doing that and you finally take the responsability on how to protect your system. If I was a script-kiddie I could now easily lead you to a script doing what you want and aditionally giving me a backdoor to your computer - the opposite of what you want. So only use scripts you perfectly understand and trust when it comes to security.

---

### Post by misteral on 2006-09-26
Houman
I'm doing as you are - using dyndns so I can access my box from work. 

In my router set up what I did is I'm routing a not normal to port 22 - therefore when I'm at work, I do ssh -p80000 my.host.net for example, and my router then translates that into port 22. This way, your usual scanners should usually skip right over this.

Also, I found a very useful howto on here for setting up Deny Hosts. What denyhost does is it detects frequent unsuccessfull logins and all sorts of bad stuff and automatically puts that IP into the deny file. Check it out, I was able to set it up pretty effortlessly:  [http://ubuntuforums.org/showthread.php?t=254149](http://ubuntuforums.org/showthread.php?t=254149)

---

### Post by Houman on 2006-09-26
thank you misteral,
I just went and changed the router to forward the public port 60000 to 22, although I think the script kiddies will figure that out because theyre using port scanners (unless the port scanners dont check the useless ports like 60000).

and thank you very much for the howto, just what i needed! I think i can turn my sshd back on soon :D

thanks eveyone

Houman

---

### Post by misteral on 2006-09-27
Houman
It's entirely probrable that someone scans these ports. What I've been told and what I've read is that because port 22 is always tied to SSH, most attacks would run through the standard ports. So it'll try 21, then know if it's Telnet it can use a Telnet based approach, 22, knowing it can use an SSH based approach etc.
FWIW, I'm still learning like you, so I'm only passing on second hand information passed on to me by the networking guys at work.

---

### Post by Johan! on 2006-09-27
If you install fail2ban (it's in the repositories) it will ban an IP after 5 failed login attempts.
During the installation you can specify how many login attempts, and the time the IP is banned.

---

