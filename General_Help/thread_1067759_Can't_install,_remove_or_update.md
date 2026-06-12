---
title: "Can't install, remove or update"
date: 2009-02-12
forum: General Help
---

### Post by Bo Rosén on 2009-02-12
I've obviously done something very stupid, and I think I know what.

I was following the instructions for installing gmailfs at [https://wiki.ubuntu.com/GmailFS](https://wiki.ubuntu.com/GmailFS) which said to use sudo -s -H. Once I'd done that, I forgot to exit as superuser before I fired up the repository manager to add the Dropbox repos. Bad Idea!

Now, I can't do anything with apt-get or synaptic without getting a seg fault. The update notifier is a Big Red sign telling me there was a problem.

Any ideas for how to get out of this mess?

---

### Post by rozbarwinek on 2009-02-12
Have you tried to use "fix broken packages" from synaptic menu?

---

### Post by Bo Rosén on 2009-02-13
Synaptic won't even start, it just segfaults I'm afraid.

---

### Post by Kevbert on 2009-02-13
From terminal can you run
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
```
If you can then it's the Synaptic Package Manager that's the problem.
Please post back with any errors.

---

### Post by Bo Rosén on 2009-02-13
Hi, 
thanks but it fails at the first command.

```
brosen@brosen-desktop:~$ sudo apt-get install -f
[sudo] password for brosen: 
Läser paketlistor... Färdig
Segmenteringsfelräd... 1%   
brosen@brosen-desktop:~$ 

```The kernel log has the following message if it's any help;
_Feb 13 10:08:16 brosen-desktop kernel: [ 4628.018242] apt-get[16200]: segfault at 570e78a8 ip b7e74952 sp bfc04cc0 error 4 in libapt-pkg-libc6.8-6.so.4.6.0[b7e14000+bf000]_

---

### Post by 3rdalbum on 2009-02-13
This could be a serious problem... but first try rebuilding the package list in case you have a corrupted package list that's causing the segfaults:

```
sudo apt-get update
```

---

### Post by Bo Rosén on 2009-02-13
> **3rdalbum said:**
> 
```
sudo apt-get update
```

That fixed it. I got several error messages about IN/OUT error, unreadable files and other cheerful things. Then the computer more or less froze and I had to do a hard reboot.
When it came on again everything was fine!

So, thank you very much. I really appreciate it.

---

