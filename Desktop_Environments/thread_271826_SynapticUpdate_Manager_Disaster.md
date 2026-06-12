---
title: "Synaptic/Update Manager Disaster"
date: 2006-10-05
forum: Desktop Environments
---

### Post by d2vge on 2006-10-05
Okay, so I installed some updates about a week ago and have been pulling my hair out ever since. First Synaptic stopped working, so I did the fixes in the sticky, and that seemed to work for a while, but then Update Manager and Synaptic weren't working (they would just attempt to load and then disappear), but Add/Remove was. Now I've just tried to add another program and now *none* of them are working. 
When I try to get updates with  sudo apt-get update, I get this:

```
sudo: unable to lookup  via gethostbyname()
```

Can I fix this without screwing more stuff up? Obviously, I'm a newbie...so I need idiot-instructions. :???:

---

### Post by pjbgravely on 2006-10-05
Post what you have in /etc/apt/sources.list I bet the problem is there.

Paul

---

### Post by d2vge on 2006-10-05
You mean this? 

# 
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by pjbgravely on 2006-10-05
It looks OK. Using us. on mine caused problems but your ca. addresses seem to be working. You can always try and remove ca. from all your enabled repositories and try that. Back up your sources.list first.

Other than that in looks like a DNS problem. If you can browse the net then it must be with apt's ability to use the DNS. I cannot see an easy way to reinstall apt. You can do it using Synaptic, search for apt, and click reinstall. You can force installing from the disk if you go to Synaptic/settings/files/delete cached package files and since it can't go online it should grab it from the disk ( insert it first).

I hope this helps, or that someone more experienced comes along.

Paul

---

### Post by dannyboy79 on 2006-10-05
i know this may sound weird but this happened to me when I messed around with my hosts file, i accidentally removed something I shouldn't have. it's because the machine doesn't know it's own name anymore. at least that was what my problem was because once I popped in a live cd, mounted the root filesystem, i was smart enough prior to changing the hosts file to make a backup so did sudo mv /etc/hosts-backup /etc/hosts
then rebooted and i could use sudo again.
here is my hosts file if it'll help you remember what you did. i am pretty sure the 127.0.0.1 localhost yourcomputernamehere is the most important!

127.0.0.1 localhost XUBUNTU
192.168.0.5 XUBUNTU

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.3 UBUNTU
192.168.0.4 WINXP

---

### Post by arkangel on 2006-10-05
> **dannyboy79 said:**
> i know this may sound weird but this happened to me when I messed around with my hosts file, i accidentally removed something I shouldn't have. it's because the machine doesn't know it's own name anymore. at least that was what my problem was because once I popped in a live cd, mounted the root filesystem, i was smart enough prior to changing the hosts file to make a backup so did sudo mv /etc/hosts-backup /etc/hosts
then rebooted and i could use sudo again.
here is my hosts file if it'll help you remember what you did. i am pretty sure the 127.0.0.1 localhost yourcomputernamehere is the most important!

127.0.0.1 localhost XUBUNTU
192.168.0.5 XUBUNTU ...

check also /etc/hostname   it should have your compute name as well 
in dannyboy79's example   it should have a line  **XUBUNTU**

---

### Post by d2vge on 2006-10-06
> **dannyboy79 said:**
>  it's because the machine doesn't know it's own name anymore.

Yes, exactly so! Because when I open the Terminal it's saying username@[blank]:~$ where it used to say username@hostname:~$. Unfortunately I *wasn't* smart enough to do a backup. :( But the weird thing is, my /etc/hosts file looks pretty much the same as yours, as far as I can see (except for the last two lines, but I don't have XP on my system...maybe I need the other line, though??):
127.0.0.1 localhost ubuntupants
127.0.1.1 ubuntupants

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And arkangel, my hostname file is normal.

*screams* Thanks to everyone for your help, though. Any more ideas? Should I just reinstall the whole deal? :-?

---

### Post by nikhilk on 2006-10-06
Confirm that your "/etc/hostname" file too contains the same hostname, which in your case is "ubuntupants".
BTW: cool hostname you have got there :)

---

### Post by d2vge on 2006-10-06
> **nikhilk said:**
> Confirm that your "/etc/hostname" file too contains the same hostname, which in your case is "ubuntupants".
BTW: cool hostname you have got there :)

Yeah, it does. 
And thanks. :mrgreen:

---

### Post by nikhilk on 2006-10-06
> **d2vge said:**
> 127.0.0.1 localhost ubuntupants
127.0.1.1 ubuntupants
I do not know for sure if the second of the above lines is required . Just see if removing that line (127.0.1.1 ubuntupants) helps.

---

### Post by arkangel on 2006-10-06
the second line is not  required you can leave it,  erase  or put your own ip 

still have problems?

---

### Post by pjbgravely on 2006-10-06
After you take out that line or make other changes reboot. Unfortunately I have found that with the 2.6 kernel a reboot is sometimes necessary. On my server fail2ban refused to work right, but after a forced reboot because of a power failure fail2bad works perfectly now. 

Paul

---

### Post by d2vge on 2006-10-06
> **nikhilk said:**
> I do not know for sure if the second of the above lines is required . Just see if removing that line (127.0.1.1 ubuntupants) helps.

Well, that's weird. I removed the line, and now Add/Remove is working, but none of the Administrative Applications will load (Synaptic, Update Manager etc.) and the terminal's still not displaying my hostname.

---

### Post by dannyboy79 on 2006-10-06
> **d2vge said:**
> Yes, exactly so! Because when I open the Terminal it's saying username@[blank]:~$ where it used to say username@hostname:~$. Unfortunately I *wasn't* smart enough to do a backup. :( But the weird thing is, my /etc/hosts file looks pretty much the same as yours, as far as I can see (except for the last two lines, but I don't have XP on my system...maybe I need the other line, though??):
127.0.0.1 localhost ubuntupants
127.0.1.1 ubuntupants

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And arkangel, my hostname file is normal.

*screams* Thanks to everyone for your help, though. Any more ideas? Should I just reinstall the whole deal? :-?


No, you don't need the other line, that UBUNTU line is for my Ubuntu server. I have put all my ip addresses and their respective hostnames in all my hosts files, that basically is the way my network can identify each other instead of only using ip address I can also ping and whatnot by computer name. it is an option you can set within your smb.conf whether name resolution is done by hosts bcast wins etc etc.
I am now stumped, did you try changing your hostname lately? it's weird that you're saying that your hosts file has the loopback in it, which is the one that says 127.0.0.1 localhost ubuntupants so I am not sure what is wrong since that's how I believe i fixed my problem when i was getting  the same error you are getting? why don't you try removing all "ubuntupants" references and see what happens? so your hosts would look like this. 

127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

either first backup your file or simply remember what you are changing so you can change it back if something goes haywire. good luck

---

### Post by d2vge on 2006-10-06
> **pjbgravely said:**
> After you take out that line or make other changes reboot. 
I've rebooted every time I've changed something. I'm doing all the changes in recovery mode, then ctrl+o, ctrl+x, reboot....reboot is the only way I know to get out of there. :oops: 

[QUOTE=dannyboy79]why don't you try removing all "ubuntupants" references and see what happens?
[/QUOTE]

Did that, but everything seems the same.

---

### Post by arkangel on 2006-10-06
no panic 

if you type in a console  
hostname 

what is the output ?

---

### Post by d2vge on 2006-10-06
> **arkangel said:**
> no panic 

if you type in a console  
hostname 

what is the output ?

Nothing. It just goes back to [username]@:~$

---

### Post by arkangel on 2006-10-06
ok your hostname is not set and the only plcae for that is the /etc/hostname 

for editing /etc/hostname   you need su permisions 

if your hostname is not set,  how are you editing your /etc/hostname ?

---

### Post by d2vge on 2006-10-10
> **arkangel said:**
> if your hostname is not set,  how are you editing your /etc/hostname ?

Like I said, I was doing it in recovery mode. I didn't know any other way of doing it. 
It doesn't matter - everything was so screwed up that I just reinstalled the whole thing. :roll:

---

