---
title: "Considering moving back to XP"
date: 2006-09-14
forum: Desktop Environments
---

### Post by stuart_75 on 2006-09-14
Hi all,

After several months with ubuntu, all was well. But in the last week things have took a turn for the worse and now Im giving serious thought to going back to windows.

First of all I moved my linux hard drive into another desktop machine, with an indentical motherboard. Now firestarter doesnt work saying it cant see eth0 (or eth1) tried running the wizard without any luck.

Secondly amule has stopped running, it wont even start when I run the the launcher.

Now ive tried going into synaptic package manager and uninstalling and reinstalling but keep getting error messasges that dont mean a lot to me.

Is there a "system restore" option anywhere that I could use to roll it back a couple of weeks?

Or can I reinstall ubuntu on top of the current installation or do I need to start froim scratch???

Many Thanks

Stuart

---

### Post by yota on 2006-09-14
Even if the motherboard is 'identical' it's not exactly the same, so probably the problems with firestarter and everything net-related came from the different mac address of the network card of the new board.
In the file /etc/iftab there is an association between the mac address and the logical name of the periferal (ethX).
> 
yota@linbook:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac **00:C0:9F:50:BB:EC** arp 1
wlan0 mac 00:0E:35:4D:DD:13
yota@linbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **00:C0:9F:50:BB:EC**
          inet addr:1.6.49.9  Bcast:1.6.51.255  Mask:255.255.252.0
          inet6 addr: fe80::2c0:9fff:fe50:bbec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32387063 (30.8 MiB)  TX bytes:6387419 (6.0 MiB)
          Interrupt:6

You have to correct that file so your card (that now has probably became eth1) returns to be eth0.

About those messages that doesn't mean much... It's hard to help without seeing them: please post details instead of just complaining. ;) 

Hope this helps.

---

### Post by skymt on 2006-09-14
[COLOR="Silver"]I need more information to help you.

* Are you using ethernet built into your motherboard, or on a card?

* If you run amule from a terminal, what errors does it give you?

* What errors do you get from Synaptic?

Also, I should point out that 99% of users have no use whatsoever for Firestarter. It's pretty much a waste of time.[/COLOR]

EDIT: See the post above me. Don't bother with mine. I hate it when a simulpost gives much better advice than mine.

---

### Post by stuart_75 on 2006-09-14
got this so far...

gunny@gunny-desktop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:87:96:7d:c0 arp 1
gunny@gunny-desktop:~$


ethernet built in on both boards.

Stuart.

---

### Post by yota on 2006-09-14
Ok, 00:0d:87:96:7d:c0 is the mac (physical) address of your old net card.
```

ifconfig -a

```
will tell you the one of the new card.

---

### Post by stuart_75 on 2006-09-14
Now this...........

eth1      Link encap:Ethernet  HWaddr 00:0D:87:37:89:17
          inet addr:10.0.0.14  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:87ff:fe37:8917/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3065185 (2.9 MiB)  TX bytes:746708 (729.2 KiB)
          Interrupt:201 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by JamesAguilar on 2006-09-14
About going back to XP: I'm not experienced enough to help with your problem.  But, I do know that moving a working XP HD to another computer, even with "identical" hardware, probably will not work either.  ;)  Just wanting to encourage you to stick with it!

---

### Post by yota on 2006-09-14
Ok, 00:0D:87:37:89:17 is the physical address of the new net card (as you can see now it's called "eth1")

Correct /etc/iftab (sudo gedit /etc/iftab) to look like this
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0D:87:37:89:17 arp 1


and reboot: everything should be as before the M/B change, and the net card should be called eth0.

---

### Post by someguyouknow on 2006-09-14
> **JamesAguilar said:**
> About going back to XP: I'm not experienced enough to help with your problem.  But, I do know that moving a working XP HD to another computer, even with "identical" hardware, probably will not work either.  ;)  Just wanting to encourage you to stick with it!

lol i tried it once... didnt work out.

---

### Post by moore.bryan on 2006-09-14
*what's your kernel?  the most recent kernel needs to be config'd to allow firestarter to work.  why do you need it, any way?*

---

### Post by lagagnon on 2006-09-14
> **stuart_75 said:**
>  now Im giving serious thought to going back to windows 
Feel free to do as you like.
> 
First of all I moved my linux hard drive into another desktop machine, with an indentical motherboard. Now firestarter doesnt work saying it cant see eth0 (or eth1) tried running the wizard without any luck.

That sort of move is dangerous with any operating system. When ANY operating system installs it senses ALL hardware and installs correct drivers-modules. You should always reinstall - swapping an already loaded OS from another machine will rarely work. This is NOT a Ubuntu problem, this is not the right way to do things.

> 
Secondly amule has stopped running, it wont even start when I run the the launcher.

Launch amule from a terminal and tell us what error messages you are getting. We cannot help you unless you provide more details,
>  
Now ive tried going into synaptic package manager and uninstalling and reinstalling but keep getting error messasges that dont mean a lot to me.
 But they mean a lot to us!!!

---

### Post by stuart_75 on 2006-09-14
Ive changed the mac address thingy (i think) and rebooted.

Im prompted to reinstall firestarter when I try to run it. So I reinstall getting this message...
E: amule-common: subprocess post-removal script returned error exit status 2

I also see this in the terminal window of package manager.....

eth1: error fetching interface information: device not found.

When I try to run the launcher i get this....

A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.


Thanks.

---

### Post by yota on 2006-09-15
Hi Stuart,

sorry that fixing the mac address has not been enough... probably something has moved (maybe in the first tries you made after the m/b switch) in the configuration.

But don't lose hope: we can continue to resolve problems one after the other. And it's a good opportunity to learn something more about your ubuntu system's internals.

The error in post-remove script prevent the removal of amule-common, let's force it:
```

sudo dpkg -P --force-all amule-common

```
After this the package management should be working again.

Let me know.

---

### Post by stuart_75 on 2006-09-15
hi, tried what you said, this was the result........

gunny@gunny-desktop:~$ sudo dpkg -P --force-all amule-common
Password:
(Reading database ... 98285 files and directories currently installed.)
Removing amule-common ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/ed2k by amule'
  found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 amule-common
gunny@gunny-desktop:~$

What do I do now?

Stuart.

---

### Post by sonixau on 2006-09-15
windows has simular problems with near-identical hardware.

you could have the same model hardware, but maybe a different revision etc...

---

### Post by wkulecz on 2006-09-15
Hmmm....

I have two nearly identical Ubuntu 6.06 systems, one cratered from a mysterious gdm xauth failure.  Gave up trying to fix it and "cloned" it from the other working system using Norton's Ghost 2003 and have had no networking problmes.  I did have to use Knoppix to edit /boot/grub/menu.lst and /etc/fstab to compensate for a different hard drive layout (the system I'd cloned from was dual boot Ubuntu and Vista RC1, I'm not impressed with Vista YMMV).

As to going back to XP, don't let the door hit you in the butt on the way out.  Search on my username and you'll see my Ubuntu experience has not been smooth but its still far less hassles than I've had with every version of Windows going back to 3.0, for my code, Vista seems to be the worst one yet!

If package management is broke, I'd bite the bullet and re-install.  You can get a cheap USB memory stick and boot the live CD or Knoppix to recover any files you need from the broken system before you re-install.

FYI, Ubuntu out of the box reads the Vista RC1 ntfs partition, even some of the *.wma sample files will play (I didn't try them all but all I did worked), can't get the *.wmv sample files to play back though.  The Vista sample jpegs look as good on Ubuntu as they did on Vista (1920x1200 Sony LCD display).

--wally.

---

### Post by yota on 2006-09-15
> 
gunny@gunny-desktop:~$ sudo dpkg -P --force-all amule-common
Password:
(Reading database ... 98285 files and directories currently installed.)
Removing amule-common ...
dpkg-divert: mismatch on package
when removing `diversion of /usr/bin/ed2k by amule'
found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--purge):
subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
amule-common

mhh... it seems that two packages (amule-common first and amule-utils after) installed the same file (/usr/bin/ed2k) generating a conflict. Amule-common does not want to remove it cause it's not the same file it had installed (it's file has been renamed ed2k.xmule by amule-utils).
Try to remove amule-utils first:
```

sudo dpkg -P --force-all amule-utils

```
and if it works continue with amule-common.

If it doesn't work remove by hand the problematic file:
```

sudo rm -f /usr/bin/ed2*

```
and then retry the removal of packages.

If even this doesn't work the last chance is to remove the entry that informs the system of the conflict in act.
The information is stored in /var/lib/dpkg/diversions, the format is like this:
> 
gimp-print <- package
/usr/bin/locate <- file
/usr/bin/locate.notslocate <- diverted file

removing the whole section that contains /usr/bin/ed2k will force the system to continue, ignoring this problem.
Please backup /var/lib/dpkg/diversions before modifying it, because an error in that file prevents the package manager to work.

---

### Post by stuart_75 on 2006-09-15
Tried the above with no luck.

When I open package manager and search for amule, I get a list of amule files but the amule-common is a higher version than the rest and has the red cross in its box, marking for complete removal is the only option not greyed out, but when clicking apply id doesnt remove. Do I need to delete that repositry and get it to point to the older version which is the same as the other amule files???

Now the automatic software update doesnt work. I get the orange notification symbol, i click it then the says "building dependancy tree" then shuts down.

Very strange!!!

Stuart.

---

### Post by yota on 2006-09-15
One more try: please can you post the output of
```

sudo dpkg-divert --remove /usr/bin/ed2k
sudo dpkg -P --force-all amule-utils
sudo dpkg -P --force-all amule-common

```
and
```

ls -l /usr/bin/ed2*

```

---

### Post by stuart_75 on 2006-09-17
Results.....

gunny@gunny-desktop:~$ sudo dpkg-divert --remove /usr/bin/ed2k
Password:
Removing `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
gunny@gunny-desktop:~$ sudo dpkg -P --force-all amule-utils
dpkg - warning: ignoring request to remove amule-utils which isn't installed.
gunny@gunny-desktop:~$ sudo dpkg -P --force-all amule-common
(Reading database ... 97285 files and directories currently installed.)
Removing amule-common ...
No diversion `diversion of /usr/bin/ed2k by amule', none removed
Purging configuration files for amule-common ...
gunny@gunny-desktop:~$ ls -l /usr/bin/ed2*
ls: /usr/bin/ed2*: No such file or directory
gunny@gunny-desktop:~$

Well amule is working now, albeit at 2.1.0, which is better than nothing I guess. Now I just need to get eth1 removed and make firestarter see eth0.

Thanks for the help everyone

---

### Post by stuart_75 on 2006-09-17
Now when I try and install firestarter I get error messages.

When I expand the terminal window to see the results I can see alot of errors.

One of them being eth1: error fetching interface information: Device not found.

This is printed in the terminal serveral times.

I dont understand why it is lokking for eth1 when im connected via eth0.

Any ideas?

---

### Post by yota on 2006-09-17
Hi Stuart,

I'm happy we are coming to the end of this journey :-)
I suppose that automatic updates are working now too, please confirm.

The last step is to remove references to eth1 and correct configurations eventually ponting to it.
The file that contains network configuration is /etc/network/interfaces, and it probably still contains a stale entry about eth1.
Edit it with:
```

sudo gedit /etc/network/interfaces

```
probably you'll find something like this:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address ********
netmask ********
gateway ********

[B]auto eth1
iface eth1 inet static
address ********
netmask ********
gateway ********[/B]



Backup the file, and then remove (be carefull not to remove anything else) the entry about eth1 (in bold) and reboot.

If a program still complains about eth1 do a full remove (package and configuration files) and reinstall it.
This applies to firestarter too, and it's probably the easiest way to fix it; another way is to manually correct firestarter configuration:

```

sudo gedit /etc/firestarter/configuration

```
and search&substitute eth1 with eth0

Let me know how it goes.

---

### Post by stuart_75 on 2006-09-17
I cant save the changes to the firestarter configuration file. The message says its read-only. 

If I try to remove it using packge manager it says....E: firestarter: subprocess post-removal script returned error exit status 1

But it does seem to be removed.


When I reinstall it Firestarter boots up, but keeps erroring over eth1, even though I tell it in the wizard to use eth0. Firestarter is gash IMHO.

---

### Post by yota on 2006-09-17
Oh, you're right: the configuration file is readonly indeed, we have to set rw perms to modify it:
```

sudo chmod 660 /etc/firestarter/configuration

```
and after the change made with 
```

sudo gedit /etc/firestarter/configuration

```
again change perms with
```

sudo chmod 440 /etc/firestarter/configuration

```
to restore original settings

What about /etc/network/interfaces?
And what happens if you try to force firestarter removal as we did with amule?
```

sudo dpkg -P --force-all firestarter

```

---

### Post by stuart_75 on 2006-09-17
If I try to force the removal of firestarter i get this....

gunny@gunny-desktop:~$ sudo dpkg -P --force-all firestarter
(Reading database ... 97411 files and directories currently installed.)
Removing firestarter ...
 * Stopping the Firestarter firewall...                                  [ ok ]
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter
gunny@gunny-desktop:~$

I changed the interfaces file without any problems

---

### Post by stuart_75 on 2006-09-17
> **stuart_75 said:**
> If I try to force the removal of firestarter i get this....

gunny@gunny-desktop:~$ sudo dpkg -P --force-all firestarter
(Reading database ... 97411 files and directories currently installed.)
Removing firestarter ...
 * Stopping the Firestarter firewall...                                  [ ok ]
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter
gunny@gunny-desktop:~$

I changed the interfaces file without any problems


Its now working!!!!!!!!!!!

Thank you everyone who helped on this one.

Now I would love to upgrade amule to allow 4gb+ file support but Im to scared to touch it now!

Does the linux ext3 disk format accept files over 4gb???

Thanks!!!!!!!!!!!!!!!

---

### Post by oscartheduck on 2006-09-17
According to <a href=http://www.suse.de/~aj/linux_lfs.html> this article on Large File SYstems</a>, Ext3 supports larger than 2 gig files. <a href=http://en.wikipedia.org/wiki/Ext3> Wikipedia</a> says it supports files up to 2 terrabytes, so 4 gig isn't going to stretch it too much.

SOmething really cool about linux systems, about debian, about Ubuntu, is that once something is fixed, it's fixed. That's it. You shouldn't need to worry about upgrading amule as long as you're doing it from one of the official repos. The community stuff is a little less firm, but I've never had a problem with it.

I also wanted to tell you that I really really appreciate where your frustration was coming from; windows is designed to hide  a lot of stuff under the surface, so when it works it seems great and like there's little effort. HOwever, if it doesn't work, you get issues which you cannot actually address at all. In ubuntu, when something doesn't work it's 99.9% of the time a simple matter of using a text editor to edit a few files, maybe do a forced uninstall of something. And ubuntu makes these things simple to do, as long as you know what they are. And if you don't know what they are, but you can get to the internet (even through a library or some place) you can usually find *someone* who knows how to fix it. Stick with ubuntu and that freedom to repair anything in a simple way is so liberating that using windows feels cripplingly constictive.

---

### Post by mgmiller on 2006-09-17
> Does the linux ext3 disk format accept files over 4gb???

Yes it does.  I have several .iso's that are larger than 4 gig, no prob.

---

