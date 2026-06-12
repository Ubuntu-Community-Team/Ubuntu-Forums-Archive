---
title: "Gnome stalls"
date: 2005-10-13
forum: Desktop Environments
---

### Post by desperado666 on 2005-10-13
Hi

My gnome hangs whenever i boot up my notebook.
This happened few day before.
This morning i did sudo apt.get update &upgrade but doesnt help

What to do now?

---

### Post by drogoh on 2005-10-13
Check to make sure your laptop's hostname is in /etc/hosts

Gnome will wriggle, moan, complain and outright refuse to work by not having a resolving hostname.

---

### Post by ssam on 2005-10-13
check that your clock is set right.

```
sam@titania:~$ date
Thu Jan 1 18:07:57 BST 1904
sam@titania:~$ sudo date -s "Thu Oct 13 18:08:57 BST 2005"
Password:
Thu Oct 13 18:08:57 BST 2005
```

gnome wont start if the date is crazy. 

although it could be a network problem. does

```
sudo ifup lo
```

help?

---

### Post by desperado666 on 2005-10-13
I will try later on and report thx for all your current posts.

If this is not working i will do my third new Ubuntu install....

Where is a repair function????

---

### Post by desperado666 on 2005-10-13
[QUOTE=drogoh]Check to make sure your laptop's hostname is in /etc/hosts

Gnome will wriggle, moan, complain and outright refuse to work by not having a resolving hostname.[/QUOTE]


I dont get what you are telling me.....

---

### Post by drogoh on 2005-10-13
[QUOTE=desperado666]I dont get what you are telling me.....[/QUOTE]

When you type 'hostname' in a terminal, the output is your "host name".  If that doesn't resolve to an actual IP (most of the time 127.0.0.1), a lot of applications will have issues communicating (especially desktop environments like Gnome)

The /etc/hosts file is your local database of host names so that your local computer will associate names to places, as long as you have an entry there.  I'm playing most of this by memory, as I am currently at work and away from my Breezy install, so I don't quite recall the graphical interface that shows the same thing.

---

### Post by desperado666 on 2005-10-13
[QUOTE=drogoh]When you type 'hostname' in a terminal, the output is your "host name".  If that doesn't resolve to an actual IP (most of the time 127.0.0.1), a lot of applications will have issues communicating (especially desktop environments like Gnome)

The /etc/hosts file is your local database of host names so that your local computer will associate names to places, as long as you have an entry there.  I'm playing most of this by memory, as I am currently at work and away from my Breezy install, so I don't quite recall the graphical interface that shows the same thing.[/QUOTE]


I will try this and report later 
thx for reply

---

### Post by desperado666 on 2005-10-13
[QUOTE=drogoh]When you type 'hostname' in a terminal, the output is your "host name".  If that doesn't resolve to an actual IP (most of the time 127.0.0.1), a lot of applications will have issues communicating (especially desktop environments like Gnome)

The /etc/hosts file is your local database of host names so that your local computer will associate names to places, as long as you have an entry there.  I'm playing most of this by memory, as I am currently at work and away from my Breezy install, so I don't quite recall the graphical interface that shows the same thing.[/QUOTE]


If i understand you right my "host name" must be 127.0.0.1?
Well my output is notebook.
Its the name of my notebook in the network.

What can i do to resolve this problem???

---

### Post by binarymelon on 2005-10-13
```
ping -c4 `hostname`
```

run that command if you get 4 recieved than your fine.  Also note that those are not apostrophes so your best bet would be to copy it directly into the terminal if possible.

---

### Post by desperado666 on 2005-10-13
[QUOTE=drogoh]When you type 'hostname' in a terminal, the output is your "host name".  If that doesn't resolve to an actual IP (most of the time 127.0.0.1), a lot of applications will have issues communicating (especially desktop environments like Gnome)

The /etc/hosts file is your local database of host names so that your local computer will associate names to places, as long as you have an entry there.  I'm playing most of this by memory, as I am currently at work and away from my Breezy install, so I don't quite recall the graphical interface that shows the same thing.[/QUOTE]


This is the entry of my /etc/hosts

127.0.0.1	localhost.localdomain	localhost	notebook

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by pjbgravely on 2005-10-15
I have the same problem. Gnome takes 3 minutes to start and 2 minutes to shut down.

 'sudo ifup lo' fixes the problem, , but I would have to use it every time I start the computer. but I don't understand what it does,and couldn't find the "lo" in ifup man pages.

I am assuming this was caused by my install problem.

When I installed I didn't have a either net cable attached and my wireless card wasn't detected. When I did my first start, Gnome started up fast but I could not use sudo because the host name wasn't written in /etc/hosts. I had to reboot to rescue kernel and fix the file that way. When I rebooted  Gnome started fine and I set up the network and it worked fine. The next time the computer was booted Gnome was slow to start. I am assuming that it is a network problem but once Gnome is running the network is fine. Do I need the 'ifup lo' command somewhere in my startup scripts?

*update*
ok 'lo' is the loopback device and it is not starting at boot. I fixed it by adding 'auto lo' to /etc/network/interfaces
Paul

---

### Post by Nightwish on 2005-11-08
that's a retarded error. let's see if i remember the post so i can tell if it worked.

---

