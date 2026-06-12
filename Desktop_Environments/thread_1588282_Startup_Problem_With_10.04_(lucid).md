---
title: "Startup Problem With 10.04 (lucid)"
date: 2010-10-04
forum: Desktop Environments
---

### Post by chicago uptown on 2010-10-04
Hi- Thanks in advance for reading through this post. I've only been a linux user for 1.5 yrs, so I'm still learning the ropes. 

I've been running 10.04 (lucid, Kernel Linux 2.6.32-25-generic, GNOME 2.30.2) for about 3 or 4 months and everything has been great, until yesterday. 

All of the sudden, bootup has started taking longer than usual and the panel at the top of the screen with "applications", "places", etc. doesn't appear until the machine has been running for at least 2 minutes. 

Also- the mouse and keyboard (and my external hard drive), all of which are usb, do not respond until about 2 minutes after startup appears to have finished. 

So, basically, here's what happens when I power the machine on:

1. Everything functions quickly, and as normal, until my desktop picture shows and the icons on it appear. 

2. Whereas before I would have had mouse and keyboard use (and use of the top panel with applications, places, etc.) at this point, I don't have use of any of these. 

3. So I just wait, without keyboard or mouse, etc. for about 2-3 min and all of the sudden the top panel emerges, the mouse and keyboards start working, and then the external hard drive appears. 

4. As if this weren't annoying enough, after everything above starts to work, opening applications (e.g. firefox) takes a lot longer than it used to. Basically, starting any application after startup takes a long time the first time it's opened. 

I don't understand why this is happening. Before this, startup was super fast, and everything was working great. I dont know how to check into recently loaded updates, but perhaps something got changed there that is causing the problem. 

I haven't changed anything hardware related at all, so I don't imagine the change in performance is due to anything on that front, but I could be wrong. 

I've looked through the forums and couldn't find anything addressing this problem, so any help is immensely appreciated. Thanks!

---

### Post by Crazedpsyc on 2010-10-04
ok open a terminal from apps>accessories>terminal and run
```
sudo apt-get install bleachbit
```
after it is finished run bleachbit from apps>System Tools>BleachBit mark everything except places under firefox and free disk space under system then run it. Try a reboot and see how it goes now

---

### Post by coffee412 on 2010-10-04
> **chicago uptown said:**
> Hi- Thanks in advance for reading through this post. I've only been a linux user for 1.5 yrs, so I'm still learning the ropes. 

I've been running 10.04 (lucid, Kernel Linux 2.6.32-25-generic, GNOME 2.30.2) for about 3 or 4 months and everything has been great, until yesterday. 

All of the sudden, bootup has started taking longer than usual and the panel at the top of the screen with "applications", "places", etc. doesn't appear until the machine has been running for at least 2 minutes. 

Also- the mouse and keyboard (and my external hard drive), all of which are usb, do not respond until about 2 minutes after startup appears to have finished. 

So, basically, here's what happens when I power the machine on:

1. Everything functions quickly, and as normal, until my desktop picture shows and the icons on it appear. 

2. Whereas before I would have had mouse and keyboard use (and use of the top panel with applications, places, etc.) at this point, I don't have use of any of these. 

3. So I just wait, without keyboard or mouse, etc. for about 2-3 min and all of the sudden the top panel emerges, the mouse and keyboards start working, and then the external hard drive appears. 

4. As if this weren't annoying enough, after everything above starts to work, opening applications (e.g. firefox) takes a lot longer than it used to. Basically, starting any application after startup takes a long time the first time it's opened. 

I don't understand why this is happening. Before this, startup was super fast, and everything was working great. I dont know how to check into recently loaded updates, but perhaps something got changed there that is causing the problem. 

I haven't changed anything hardware related at all, so I don't imagine the change in performance is due to anything on that front, but I could be wrong. 

I've looked through the forums and couldn't find anything addressing this problem, so any help is immensely appreciated. Thanks!


One place to start would be your system log file. This file is located at /var/log/messages

I find it hard to help with alot of problems unless I can actually see your log file. So, If its possible you can attach it to a post for download I will be glad to look thru it and see if there are reported issues.

:)

---

### Post by chicago uptown on 2010-10-04
Tried it, but no luck. I encountered the same problems after restart. Firefox still takes forever to load (so does any application: text editor, office, etc.).

---

### Post by Crazedpsyc on 2010-10-04
Hmmm, please post your system specs as well as the output of
```
df
```
I know that command sounds odd but it stands for disk free I think. It just shows your hard disk space

---

### Post by chicago uptown on 2010-10-04
I'm not sure what specs you mean, but I have 4 GiB ram, AMD Athlon II X2 240 processor, and 510.7 GiB of available hard drive space.

---

### Post by Crazedpsyc on 2010-10-05
Ok that'll do. I found that after switching to Lucid many people have this problem although I do not. It seems to have something to do with the IPV6 support. there is a thread here that might solve your problem: [http://ubuntuforums.org/showthread.php?t=296443](http://ubuntuforums.org/showthread.php?t=296443)
> I had the same type of problems. The fix was to make sure nothing is  funky in /etc/hostname, and /etc/hosts which I found there was. It  happened all of a sudden and fixing those files fixed everything.

/etc/hostname only has one word in it, the name of your computer.

/etc/hosts only needs to have one line in it to work.

127.0.0.1 localhost host_name

Host_name has to be the same name found in /etc/hostname.

Put a # in front of all other lines.


Also in /etc/network/interfaces if these lines are not found you computer can act the same.

# The loopback network interface
auto lo
iface lo inet loopback


Paul

---

### Post by chicago uptown on 2010-10-06
Thanks for the pointer- I'll check out that thread!

---

