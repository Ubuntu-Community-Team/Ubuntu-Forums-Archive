---
title: "sudo: unable to resolve host"
date: 2009-03-02
forum: General Help
---

### Post by Tripledrop on 2009-03-02
I am a newbie at linux in general, but managed to set up a ovh server using ubuntu.

I restarted the server the other day as it had frozen, and whenever I try to connect, I get "Network error: connection refused". I can ping my server, and still access using ftp, and I understand that this is due to the ssh port being closed. 

I searched a little online, and found someone with similar problems, and they installed and started the ssh server using:

sudo apt-get install openssh-server

I tried this, but I get "sudo: unable to resolve host rescue.ovh.net" errors. I also tried starting the ssh server, but can't remember how!

Any ideas? I really am stuck now! This happened before, and I ended up reformatting and starting my server again, and I would rather not do that this time!

EDIT: I can access the server using rescue mode.

---

### Post by caljohnsmith on 2009-03-02
Usually that type of sudo error is because the host name of your computer is not exactly the same in the /etc/hosts and /etc/hostname files. Try editing either of those files so your computer host name is the same in both files (including if you decide to keep the domain suffix), and let me know if that solves your problem.

---

### Post by Tripledrop on 2009-03-02
Any chance you could walk me through doing that? I am a *proper *newbie at this!

---

### Post by caljohnsmith on 2009-03-02
Sure, so while you are in rescue mode, try:
```
cat /etc/hosts
cat /etc/hostname
```
And check if the host name of your computer exactly matches in those files. If not, then modify either file using nano:
```
nano /etc/hosts
```
And change the host name so it is the same. Let me know how that goes or if you run into problems.

---

### Post by Tripledrop on 2009-03-02
Thanks for the help :)

This is what I found:

rescue:~# cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1       localhost.localdomain localhost rescue.ovh.net
# The following lines are desirable for IPv6 capable hosts
#(added automatically by netbase upgrade)
::1     ip6-localhost ip6-loopback
feo0::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

--------------------------------------------

rescue:~# cat /etc/hostname
rescue.ovh.net

---

### Post by caljohnsmith on 2009-03-02
OK, it looks like you are missing an entry for 127.0.1.1 in your hosts file:
```
127.0.1.1 rescue.ovh.net
```
Try adding that to the /etc/hosts file right after the 127.0.0.1 entry, and let me know if that works OK or not (you'll probably need to reboot).

---

### Post by Tripledrop on 2009-03-02
Ok, thanks again! I have added that line, and exited... What do I do now? Do I reboot and then try to install the ssh server again? Or something else?

---

### Post by caljohnsmith on 2009-03-02
Go ahead and reboot, and then try using sudo again. To test sudo you could do something like:
```
sudo pwd
```
If that doesn't return an error, you should be fine.

---

### Post by Tripledrop on 2009-03-03
Ok, I rebooted, and tried sudo pwd, and that gave me:

```
sudo: fixed mode on /etc/sudoers
/root
```


I then tried the ssh server again and got:

```
rescue:~# sudo apt-get install openssh-server
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```

Any ideas on how to open my ssh port?

---

### Post by Tripledrop on 2009-03-04
Anyone have any ideas?

---

### Post by Tripledrop on 2009-03-04
Don't worry, I realised it was because I wasn't in the root of rescue mode... Just started ssh, updated everything, and rebooting the server out of rescue mode now. We'll see if I can log in!!

---

### Post by Tripledrop on 2009-03-04
Still can't access the server! Same error :(

I have entered rescue mode again, and typed:

```
nano /etc/ssh/sshd_config
```

And I now remember that I changed the ssh port to 54322. Is this significant?

---

### Post by InfamousUrge on 2009-03-05
I too seem to have this problem. Does anyone have a solution?

Thank you :)

---

### Post by Tripledrop on 2009-03-06
anyone?

---

