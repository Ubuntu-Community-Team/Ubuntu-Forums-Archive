---
title: "Conky info via SSH"
date: 2007-12-18
forum: Desktop Environments
---

### Post by p_quarles on 2007-12-18
So, I have a conkyrc script for my desktop that I like. It looks nice, and it helps me catch the occasional runaway process. 

What I would *like* to do is to be able to display much of the same information for my headless home server. I already have my server configured to accept passwordless, rsa-based authentication, so all of the same information is available without entering my password. It seems like I should be able, at the cost of a little LAN bandwidth, to monitor the uptime, CPU & memory usage, net connections, and bandwidth usage via this SSH connection. 

Is this possible? I'm still pretty new to conky's scripting method, so maybe the answer is obvious to others. And, yes, I know there are other network monitoring apps that are designed specifically for this, but I like conky. ;)

---

### Post by Prospero2006 on 2007-12-19
I monitor a primary server in my classroom much the same way. 
Go to 
Preferences->sessions->startup programs

Add command to desktop login that looks like this:

```

/usr/bin/ssh -X ip_addy_of_headless_server 'conky' &

```

This will execute conky on the remote machine and show it on the local display.

---

### Post by p_quarles on 2007-12-19
That would definitely work, but I don't want to run X on this server -- I want to keep running processes and power consumption at a minimum. 

Just to clarify, what I'm looking for is a way of culling the remote system info via SSH from within a conky script running on my desktop.

---

### Post by Prospero2006 on 2007-12-20
Ok, the cpuinfo and memory info are located in the /proc directory

So, you could write a script that does something like this

```

cat /proc/cpuinfo | grep 'infoyouwant'

```

The same would go for meminfo or whatever you're looking for.
Although someone may have something more elegant, all the information you 
are looking for can be located in the proc directory in clear text. 
The key is finding the time to write a script that reads in the file, cuts out
the important information, and then relays that information every X seconds.

Maybe?

---

### Post by p_quarles on 2007-12-20
Yeah, thanks, that's a very good idea. Could be a bit of work, like you said, but that should definitely do the trick.

I'm assuming that's pretty much how Conky works anyway, so I'm gonna go have a look at the source and see if I can make heads or tails of it.

---

### Post by tgalati4 on 2007-12-20
Try ruptime.

>sudo apt-get install rwhod

---

### Post by p_quarles on 2007-12-20
> **tgalati4 said:**
> Try ruptime.

>sudo apt-get install rwhod
That just displays uptime, though, and the other tool in the package only displays current users. I'd also like to be able to keep an eye on memory and network usage. 

Have looked at the Conky source code now, and it's too much for my level of knowledge. Anyway, I'll attempt to write a script using cat and grep to accomplish this, and will post it here if I get it working. Otherwise, I'll probably end up using Nagios.

---

### Post by tekknokrat on 2008-02-19
Today I had the same idea when playing with nagios. 
How much effort is it to use nagios in an conky view :-)

What conky would need is definitly some kind of button to switch between different hosts. did you did more investigation in that?

---

### Post by BDNiner on 2008-03-31
> **tekknokrat said:**
> Today I had the same idea when playing with nagios. 
How much effort is it to use nagios in an conky view :-)

What conky would need is definitly some kind of button to switch between different hosts. did you did more investigation in that?

What a great idea. I am also looking into the same thing at work. I would like it to function like the nagios plugin for firefox. Just alert me in conky with the status of services that nagios is reporting down. I don't know much about nagios but we have a website with all the statuses posted so i should be able to pull that data into a local database and get the info for conky from there.

---

