---
title: "Network: Pushing a file to multiple computers"
date: 2009-04-29
forum: General Help
---

### Post by dmcdaniel on 2009-04-29
The Problem:

I have one file and about 40 computers. I need to put this file on all of these computers without manually going to them. I have all of the IP addresses and login information. What is the most effective way for me to do this?

Thanks,
dmcdaniel

---

### Post by shel-hall on 2009-04-29
> **dmcdaniel said:**
> The Problem:

I have one file and about 40 computers. I need to put this file on all of these computers without manually going to them. I have all of the IP addresses and login information. What is the most effective way for me to do this?
Unless you have some sort of file transfer server (ftpd, rsyncd, etc.) or remote access (rsh, rexec, ssh, etc.) server running on the 40 remotes, probably the best thing is to use "expect" to create a script that, given the IP address, will log into a machine and request the file.

The "expect" package normally has a facility to watch what you do and write a script for you, but I'm new enough to Ubuntu that I don't know the details of the Ubuntu/Debian package.

-Shel

---

### Post by dmcdaniel on 2009-04-29
Thanks for the reply. I did find out that I have SSH on all the machines (Still fairly new to this) 

So I created a script that looks like this:

scp /LocationOfFile/FileName ipaddressofmachine:/LocationOfFile


That sent it to the computer. I only have to do this 40 times but its better than walking to each station :)

---

### Post by Kareeser on 2009-04-29
Yes, scp is probably the best way to do this.

shel's suggestion involves manually logging in into each station and pulling the file. That would work too, but it's a little roundabout :)

---

### Post by shel-hall on 2009-04-29
> **Kareeser said:**
> shel's suggestion involves manually logging in into each station and pulling the file. That would work too, but it's a little roundabout :)
But I suggested it only for the case where he had no remote-access software running on the remotes.  With "expect", you'd do it manually once, then let the generated script do it the other 39 times, feeding it a list of the remote machines' IP addresses.

"scp" is a whole lot better than writing an expect script, but you have to have "sshd" running on the remotes for it to work.

To the OP or someone else in the same boat ... if you want to push that file to every machine on a subnet, it's easy enough to write a "bash" script to find all the IP addresses on your subnet, then execute the "scp" command for each IP address.

-Shel

---

