---
title: "Painfully long boot"
date: 2009-02-01
forum: General Help
---

### Post by FORCED-INDUCTN on 2009-02-01
Hey guys
I have Ubuntu 8.10 installed on my laptop and its currently using the 2.6.27-11-generic kernel. I was doing some tweaks about a month ago and they seemed to be doing good and I had restarted to check after each one, but it seems like I got a little sloppy cuz after one of the restarts it took about 4-5 times as long to boot (about 2mins, when old boot time was 30-40 seconds) Ive been probing around for a while to find the problem but all ive been able to come up with is that when I press ctrl+alt+f1 or what ever it is to get a verbose boot that it hands on "*configureing network interfaces" for a very long time, almost 60 seconds. So I installed bootchart to get some more information but I personally cant get any useful information out of it, I see some suspect areas but I dont know what to do.

hears my bootchart: [http://forced-inductn.doesntexist.org/ub.jpg](http://forced-inductn.doesntexist.org/ub.jpg)

so any ideas?

---

### Post by lavinog on 2009-02-06
Well the problem is network related.
Does the problem only happen when there is no lan connection (via ethernet port)
If so your configuration might be waiting for a dhcp request.
Do you remember doing anything to modify the network settings?
can you post: /etc/network/interfaces

---

### Post by FORCED-INDUCTN on 2009-02-06
Hey lavinog, thanx for the reply

I think it happens no matter what, unless I disable the wireless and restart, but Im not sure of this and I cant test it now (not at home) but Il try it later tonight and post back.

I don't remember doing anything to interfaces but hear is my file:
xxxx@xxxxxx:~$ cat /etc/network/interfaces
auto eth0
iface eth0 inet dhcp
auto lo
iface lo inet loopback

to my knowledge the only network related changes I made where in the /etc/sysctl.conf file but I tried commenting all of those out and rebooting with no luck, but maybe I had to restart something idk. I can post the contents of that file as well if you'd like.

One other thing is that I have a static ip set on my wireless idk if that means anything but just a bit of info, but my laptop still boots slowly at different locations like home, school where I connect it wired rather than with wifi like I do at home. So I figured that was unrelated.

---

### Post by FORCED-INDUCTN on 2009-02-06
Alright so I was able to have some one try some stuff out

First thing was disable wireless and restart, that had no change

Second was disable all networking and restart, also no affect

Third was plug in an Ethernet cord and restart and that also had no affect :(

might still be dhcp or something, uninstalling the dhcp client crossed my mind but idk.
any ideas?

btw by disable I mean just right click on the nm-applet, not run ifdown or anything, should I do it that way instead?

---

### Post by lavinog on 2009-02-06
Dont uninstall dhcp, you will regret it.

instead try commenting out the eth0 line in interfaces
```

sudo gedit /etc/network/interfaces

```
insert # on second line:
```

auto eth0
#iface eth0 inet dhcp
auto lo
iface lo inet loopback

```
see if that helps

---

### Post by FORCED-INDUCTN on 2009-02-06
omg! thank you so much lavinog! that worked beautifully! my computer now boots 3-4 times faster thank you so much I have been googling for months! hahah

I cant beleive it was that simple

well thanx again you have made me and my computer much happier haha :)

---

