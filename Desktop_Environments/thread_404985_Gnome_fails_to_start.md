---
title: "Gnome fails to start"
date: 2007-04-09
forum: Desktop Environments
---

### Post by carnz on 2007-04-09
Hello,

I've done two things which may cause the problem:

First of all I clicked on the desktop shortcut for my windows partition and the desktop seemed to chrashed. I couldn't click any other items on it. But I thought this might go away after a reboot.

Then I tried to access a NFS directory through the panel. The directory was mounted and then I shuted down the server without umounting the directory. So I was just curious to see what could happen and clicked on the directory =)
After that the panel crashed and since almost everything wasn't responding I restartet the X Server with Ctrl+Alt+Backspace.

That's it. Now Logon still works fine but after that nothing happens. Gnome doesn't seem to load anything. Not even the Background changes.

---

### Post by heimo on 2007-04-09
Two things I'd try: pinging localhost
```
ping localhost
```should give something like:
```
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.044 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.043 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.041 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.043 ms

```If it doesn't work, check "route -n" (should have a line with 127.0.0.1, iface lo), and /etc/hosts file.

Then I'd create new user account
```
sudo adduser [newuser]
```And try logging in using that one. (If it works, I'd try moving dot files, files and directories beginning with dot away from my home directorys root. And then retry logging using my username.)

If that doesn't work either, I'd install another desktop environment until I could figure out what's wrong. (sudo aptitude install kubuntu-desktop or sudo aptitude install xubuntu-desktop).

---

### Post by carnz on 2007-04-09
Ok...so I figured out what the Problem was.
I did something...even more important before all that happened =) 
I uninstalled evolution using adept-manager which uninstalled the ubuntu-desktop, too...

How can I uninstall evolution???? I just don't need it. There is absolutely no reason keeping it. I don't get the idea behind this. Xubuntu has AbiWord, which you can't uninstall...

---

