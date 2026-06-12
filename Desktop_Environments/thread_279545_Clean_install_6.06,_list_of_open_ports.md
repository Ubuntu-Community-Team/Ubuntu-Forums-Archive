---
title: "Clean install 6.06, list of open ports ?"
date: 2006-10-18
forum: Desktop Environments
---

### Post by mikeh123 on 2006-10-18
Hello,

I was wondering whether anyone could give us a listing of the open ports on a clean install, as i'm concerned i may have been hacked again!

I had a clean install of dapper, i then installed openssh-server to use for backups/copying files inside a network. left the machine on for a day and by the time i got home it had been hacked.  All of my files appeared to be OK, but to be sure i trashed ubuntu install by formatting the / and /swap partitions and re-installed afresh **.

Upon the reinstall, i'm concerned about the following:

```
johns@hera:~$ sudo nmap -sT -O localhost

Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2006-10-18 08:23 BST
Interesting ports on localhost ( 127.0.0.1):
Not shown: 1677 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
1155/tcp open  nfa
Device type: general purpose
Running: Linux 2.4.X
OS details: Linux 2.4.7 (x86)

Nmap finished: 1 IP address (1 host up) scanned in 2.298 seconds
johns@hera:~$ sudo netstat -tlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 localhost:4352          *:*                     LISTEN     4351/python 
tcp        0      0 localhost:1155          *:*                     LISTEN     4323/hpiod
tcp        0      0 localhost:ipp           *:*                     LISTEN     5266/cupsd
```

under System -> Network Tools -> Port Scan it reveals
631 open ipp
1155 open unknown
4352 open unknown

everytime i reboot my machine there are 2 or 3 ports over 1000 that are 'unknown' and have got me worried. is there a default list on new installs of open ports for dapper?? i have not seen this info anywhere.

does anyone know what these could be ??

since this incident i have certainly leared (had to) alot about ssh. it seems crazy to me now that the default install allows password entry, rootlogins yes etc. !! i think the default should be changed so that keys are needed that way newbs would need to read man pages/howtos to get it to work and it would be far more secure.

** (i left a winxp ntfs partition and a another fat32 partition that had mp3's, media etc, could this have re-opened my machine by backdoor ??)

---

### Post by carontis on 2006-10-18
I never tried to check for open ports on Ubuntu, 'cause it's know that Linux is very careful about connections and security, so I think this is done (probably) by the WinXP partition you have. At boot the pc checks for ALL open ports, also those from XP partition, 'cause in effects they are electric signals coming/going. If you need I have a list of all dangerous ports to be skipped in your programs (like p2p). But I wouldn't be so alarmed...
The install of Ubuntu is clean, yes, and athis also if in the middle of installation it asks for a DHCP or for a line where download updates. Don't be afraid and don't worry about. Before giving Ubuntu around to peoples, they tried every way to check if there was something dangerous, and I don't think they would loose a lot of time and money for giving a holed distro.

---

### Post by mikeh123 on 2006-10-18
cheers for your reply.

upon further investigation, port 631 is running cups (common unix printing system), and port 1155 is running hpiod which is some sort of HP printing service which both look standard. it only leaves port 4352 running some python program which is a little concerning.

it looks OK in that i can't telnet or ssh to these ports from outside, it would just be useful to compare someone elses clean installed to what i have at the moment (i suppose i could find out myself by getting hold of another pc and installing not connected to the network).  

But i don't know what you mean by it could be the winxp partition. the machine is dual boot ubuntu/xp so surely when booting into ubuntu it couldn't possibly start up any windows services ??

---

### Post by merkur2k on 2006-10-18
wow corontis, that made absolutely NO sense whatsoever. I think you are very confused about how computers and networking actually work...
What makes you think the machine has been compromised? The odds of it happening to an *up to date* linux computer are extremely slim even if someone is specifically targeting you, and next to nonexistent as part of a random attack. Especially against a desktop system that has very few open ports. Make sure you run updates first thing after a new install, and keep running it at least once a week.
Some of the ports listed as being open are most likely only open on the localhost interface too. You should be doing scans from an external source, or at the very least scanning your external interface address, not localhost.

---

