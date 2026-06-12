---
title: "changing computer name"
date: 2006-01-06
forum: General Help
---

### Post by veloct on 2006-01-06
When I first installed ubuntu, I left the computer name to Ubuntu so when I go to the terminal it will show me:

```
 username@ubuntu $ 
```

Is there a way to change the word ubuntu without having to reinstall?  I guess that's the computer name.  Any input is appreciated.

---

### Post by xmastree on 2006-01-06
sudo **hostname** <new computer name>

---

### Post by veloct on 2006-01-06
Thanks :)

---

### Post by xmastree on 2006-01-09
I just discovered that my method only works until you restart, then it reads the contents of **/etc/hostname** so it's better to edit that.

---

### Post by veloct on 2006-01-10
ah, I did it through Kcontrol.  :) Good to know though, thanks.

---

### Post by Norwal on 2006-01-14
Help,

I tried editing the hostname file now all I get is an error message when I log in ( I will copy the error message next log in) and I can't edit the hostname file back to the original. I get this error message.

> nor@NorLinux:~$ sudo gedit hostname
sudo: unable to lookup NorLinux via gethostbyname()


Log in error message is> Could not look up internet address for NorLinux.
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
NorLinux to the file /etc/hosts.

---

### Post by Neo Ex on 2006-01-14
I did it with KControl and I haven't had problem; maybe you have to edit two (or more) files, and not only /etc/hostname.
The first line of my /etc/hosts is:
```
127.0.0.1 localhost.localdomain localhost d83-184-206-198 kubuntu
```
Try adding 'NorLinux' at the end of this file: d83-184-206-198 was my old computer name, and kubuntu is the new one (which I also have in /etc/hostname), so...:)

---

### Post by Norwal on 2006-01-14
Thanks for your reply.

> **Neo Ex]I did it with KControl and I haven't had problem said:**
> 

I believe you're correct the hosts needs to be edited aswell. But I logged off before I relized that and now can't edit either file. I tried to access the host  file and I get the same error message as above.[QUOTE] nor@NorLinux:~$ sudo gedit hostname
sudo: unable to lookup NorLinux via gethostbyname()

Any other ideas?

---

### Post by Neo Ex on 2006-01-14
You can access the rescue terminal, right?
If yes, you can write
```
cat /etc/hosts
```
to see your /etc/hosts.
Then,
```
sudo cp /etc/hosts /etc/hosts_backup
```
I don't know how to add a word at the end of the first line, but, reading the man pages, I learned how to add words line by line.
```
sudo echo line1 > /etc/hosts
```
This will replace what is written in /etc/hosts, but what I've though is to add all the lines that you have had before in your default /etc/hosts, but at the end of the first line you'll add NorLinux.
To add a new line do this:
```
sudo echo word-to-add >> /etc/hosts
```
Sorry for the bad explaination, but I'm not English :) 
I hope you have understood anyway (and obviously that this can help you!).
Maybe someone with better skills than the mine can provide you an easier way to do this, but it could work. If not, you have the backup :p

---

### Post by Norwal on 2006-01-14
I'm not sure I understand it all but I'll give it a try. The worst that could happen is a need for a complete install and it's all about learning.

Thanks and I'll let you know how it went. 

Any other idea are still welcome of course.

---

### Post by Neo Ex on 2006-01-14
I'm going to write an example to explain what I've though:
```

daniel@kubuntu:~$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost d83-184-206-198 kubuntu

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
daniel@kubuntu:~$ sudo cp /etc/hosts /etc/hosts_backup
daniel@kubuntu:~$ sudo echo 127.0.0.1 localhost.localdomain localhost d83-184-206-198 kubuntu **NorLinux** > /etc/hosts
daniel@kubuntu:~$ sudo echo  >> /etc/hosts
daniel@kubuntu:~$ sudo echo # The following lines are desirable for IPv6 capable hosts >> /etc/hosts
daniel@kubuntu:~$ sudo echo fe00::0 ip6-localnet >> /etc/hosts
[etc]

```
I hope now I've explained better than before :)

---

### Post by Norwal on 2006-01-14
No go!

The problem is "sudo" does't work.  If I just type sudo in the terminal even in recovery mode I get the error

> sudo: unable to lookup NorLinux via gethostbyname().

I feel a reinstall coming unless there are any other ideas out there.

Neo Ex, I'm going to seach the forum for other thread before I start rebuilding.

Thx for your help.

---

### Post by Norwal on 2006-01-14
I found the answer at:

[http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup](http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup)

I used the nano command in Recovery Mode and I was able to edit the /etc/hosts  file.  Now the name is as I want it, sudo is working and the log in error is fixed.

Thx again Neo for your help.  The nano command is now safely stowed in my linux bag of tricks.

Nor

---

### Post by everettattebury on 2006-01-31
[QUOTE=Norwal]I found the answer at:

[http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup](http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup)

I used the nano command in Recovery Mode and I was able to edit the /etc/hosts  file.  Now the name is as I want it, sudo is working and the log in error is fixed.

Thx again Neo for your help.  The nano command is now safely stowed in my linux bag of tricks.

Nor[/QUOTE]


The way I hosed my system was by installing Mike's adblocking hosts file.  I just copied it over the original, and then suddenly synaptic wouldn't work anymore, and I couldn't sudo.  So I booted from an Ubuntu live cd and manually mounted my hard drive, then edited the hosts file.  Next time I'll know better, and EDIT the original, appending the adblocking entries to it.

---

