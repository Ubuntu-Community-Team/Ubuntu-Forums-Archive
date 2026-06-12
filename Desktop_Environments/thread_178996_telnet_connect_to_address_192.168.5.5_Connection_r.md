---
title: "telnet: connect to address 192.168.5.5: Connection refused"
date: 2006-05-18
forum: Desktop Environments
---

### Post by baomike on 2006-05-18
How to get telnet to work.
This the message I get when attempting to connect from 192.168.5.4.
I have been thru synaptic and all looked OK. rebooted, but still connection refused. There is someplace I need to enable inetd,but I can't find it.   On Debian I manually put an entry in the inetd.conf file, but this seems crude.

---

### Post by dermotti on 2006-05-18
Have you tried using sshd instead?

---

### Post by nanotube on 2006-05-18
telnet is not enabled by default. 
at any rate, i would recommend you to use ssh instead, as it is more secure. it is generally considered bad practice nowadays to use telnet at all.
to install ssh, just do "sudo apt-get install ssh", it will be automatically installed and configured, with sane defaults, no further configuration necessary (like magic :) ). and then you can just use "ssh 192.168.bla.bla" instead of "telnet 192.168.bla.bla", and it gives you all the same functionality (and more).

---

### Post by baomike on 2006-05-18
<<telnet is not enabled by default.>>  Tell me about it!!!
Really don't need SSH, internal network. 

I need a terminal session on 5.5 so I can see what I am doing ,  the ubuntu machine has a very crappy monitor. 

Next step , if I ever get telnet working, is to set my machine 5.4 as the Xserver,
and kill the server on 5.5. .  With everything on 5.5 (a slackware box)  I can try out VMware are a few other things.

While I am here, how is is GRUB going to respond to my compiling a new kernel?
With Debian I ended up installing LILO.

---

### Post by baomike on 2006-05-18
Never mind.
Used SSH , and got the Xserver killed off. 
never did figure out how to get telnet to work, doesn't matter.
I was surprised to find the /usr/src/ was empty.  No kernel compile.
I did the "download the kernel "  thing with Debian, and I think I will pass on this one. 
Oh well, off to try Mandriva.



NB: It looks like Ubuntu would be a good replacement for a windows user, but it seems , initialy anaway , to be resistant to mucking around in it's configuration.

---

### Post by harisund on 2006-05-19
If you *really* want telnet do this instead: 
```
sudo apt-get install inetutils-inetd inetutils-telnetd
```
And then add this line onto your /etc/inetd.conf file with sudo permissions of course
```
telnet stream tcp nowait root /usr/sbin/tcpd /usr/sbin/telnetd
```
And to start your telnet server you would do ```
sudo invoke-rc.d inetutils-inetd restart
```

---

### Post by nanotube on 2006-05-19
[QUOTE=baomike]Never mind.
Used SSH , and got the Xserver killed off. 
never did figure out how to get telnet to work, doesn't matter.
I was surprised to find the /usr/src/ was empty.  No kernel compile.
I did the "download the kernel "  thing with Debian, and I think I will pass on this one. 
Oh well, off to try Mandriva.
[/QUOTE]
kernel source is not installed by default (to save space, since most people have no need to recompile the kernel). you can install kernel sources from the repositories. (just search for "kernel" :) ).

---

### Post by RadioHam on 2006-08-06
Hi. I really want telnet as I would like to use it from a windows workstation to carry our maintenance etc remotely on ubuntu server i am building.

Where do I get the package from. sudo apt install fails unable to locate the package inetutils-telenetd. 
I've enabled universe and backport in /etc/apt/soures.list but still fails. 

A pointer to how to loate packages would be useful. Have looked in the HOWTO's but must have missed it!

TIA

---

### Post by harisund on 2006-08-06
As far as I can tell, I installed my inetutils-inetd from the universe repository 

Did you do apt-get update after editing the sources file? (How did you add the repos? Through the command line or through Synaptic?) 

And are you sure you spelled it right? inetutils-inetd ?

---

