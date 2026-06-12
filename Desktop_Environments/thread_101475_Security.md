---
title: "Security?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by scruffy on 2005-12-09
Having come from a windows background, where its firewalls, antivirus, spyware cleaners etc. What is the best way of securing my new ubuntu setup?

Is the above necassary on linux/ubuntu and if so what should I be looking to install/setup and if possible how and in what order?

All the best

Scruffy

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=scruffy]Having come from a windows background, where its firewalls, antivirus, spyware cleaners etc. What is the best way of securing my new ubuntu setup?

Is the above necassary on linux/ubuntu and if so what should I be looking to install/setup and if possible how and in what order?

All the best

Scruffy[/QUOTE]
You don't need to set up a firewall unless you start running services that outsiders could take advantage of.  By default, Ubuntu does not run any such services.  If you enable samba (Windows file sharing) for example, you may want to run a firewall to block outsiders from using that.  I think firestarter is the most intuitive firewall for newcomers to Ubuntu.

---

### Post by Qrk on 2005-12-09
You can install a firewall from synaptic (System-->Administration-->Synaptic Package Manager) ... firestarter is a good choice.

Antivirus isn't really needed unless you share files with a windows machine... even though Linux will be safe; you windows could get infected. The best Linux antivirus is called clamAV. It is also available on the repositories.

Be sure to enable the universe repository, that can be done in synaptic by Settings-->Repositories. Or you could just 

```
sudo gedit /etc/apt/sources.list
```

and take out the # before the address lines. 

You don't need to worry about spyware in Linux. Its one of the many advantages of Open Source software.

---

### Post by scruffy on 2005-12-09
Thanks cwaldbieser, Qrk for the speedy replys :D

I'll do those things now.

All the best

Scruffy

---

### Post by xequence on 2005-12-09
> Having come from a windows background, where its firewalls, antivirus, spyware cleaners etc. What is the best way of securing my new ubuntu setup?

You are very safe running ubuntu without a firewall or any antivirus/spyware program. Id recomend a firewall maybe if you run a web server though.

---

### Post by scruffy on 2005-12-09
Hi xequence,

Im using it as a destop only, not ventured into the realms of servers at all. So no need for the firewall then or maybe just for peace of mind?

Scruffy

---

### Post by Qrk on 2005-12-10
You should be fine without one. Ubuntu is very secure.

---

### Post by followme on 2006-02-21
I'm new to Ubuntu, so excuse me if I'm not fully understanding yet.

Since by default there are no services running in Ubuntu, are there services "listening"?  Unless of course, running and listening is the same thing(?).  

For example, my office laptop (win2k) which I bring home sometimes, is waiting for a connection from the office server, either anti-virus, or some other service.  I have a remote log-on app to my laptop.  Even though I didn't start it manually, it starts when my computer boots up.  Is there similar programs or services that do that in Ubuntu that isn't actively running, but waiting for instructions that can be activated remotely?

Another question is, if I'm playing a game like Quake or Unreal Tournament against other players online, I would be opening up a port or running a service right?  Can someone just use that same port to gain access?  

Is a firewall (firestarter+iptables) all I need to prevent intrusion from the outside, or will I need some other programs just to be on the safer side?

---

### Post by carlosqueso on 2006-02-21
AFAIK, your concept of services is correct....if a service isn't running, it cannot listen.  Windows has a crapload of services that listen by default.  Ubuntu doesn't have any of those services even installed.  It will automaticly check for updates, but that is a client process that sends requests out to the internet, but won't accept incoming requests.  That should be the same for Quake or UT unless you run a server.   A firewall (or not running any services) should be adequate as long as you keep your system up to date with security fixes.  Of course, if you post this in the security forum, you'll get people with various levels of paranoia telling you no (of course, that's good in a security forum).

---

### Post by az on 2006-02-21
Enable the breezy-security and the breezy-updates repositories and keep up to date with the updates!


[QUOTE=followme]  Is there similar programs or services that do that in Ubuntu that isn't actively running, but waiting for instructions that can be activated remotely??[/QUOTE]

No, not unless you instal them.  The two things that look on the net are the NTP (network time protocol - it sets your clock when you boot) and the update-notifier.  Both look on the net but they do not sit there, waiting for incoming packets.

[QUOTE=followme] 
Another question is, if I'm playing a game like Quake or Unreal Tournament against other players online, I would be opening up a port or running a service right?  Can someone just use that same port to gain access?  
[/QUOTE]

Ports are not doors.  The concept of an open port means that there is a process running in your computer that is looking for things which are received though the net, which are allocated that port number.  But they are just numbers.

You can't just log into someone's computer because they are running a program that is listening on port 6890.  You would have to have a program like ssh or telnet (remote terminal)  listening on that port (which they don't and you would not tell them to).
 
[QUOTE=followme] 
Is a firewall (firestarter+iptables) all I need to prevent intrusion from the outside, or will I need some other programs just to be on the safer side?[/QUOTE]

You don't even need that.  Just don't install the software that would give someone else access to your box without your permission.

---

### Post by ardchoille on 2006-02-21
I run Ubuntu 5.10 behind a router that does NAT and no outside-facing servers, so no need for a firewall on my machines. I do, however, recommend installing and using rkhunter, chkrootkit and tripwire. I've never used anti-virus software due to there being no active viruses for Linux. Windows needs all that crap because it's insecure and unstable: [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by JimS on 2006-02-21
...

If someone sent me an attachment which had a virus
on it and I in turn sent that attachment on to someone
else - I am probably protected, my friend up the line
might not be.
Right?  
If so, then it would seem to me that I have an obligation
not to forward viruses and should have an anti-virus
program or not forward anything.
Right?
It seems to me that a PC w/ Ubuntu OS is fully capable
of collecting, storing, and sending viruses.
Am I right or am I right?
[COLOR="Blue"]
JimS
Prostate Cancer Aware
[/COLOR]
...

---

### Post by followme on 2006-02-21
[QUOTE=JimS]...

If someone sent me an attachment which had a virus
on it and I in turn sent that attachment on to someone
else - I am probably protected, my friend up the line
might not be.
Right?  
If so, then it would seem to me that I have an obligation
not to forward viruses and should have an anti-virus
program or not forward anything.
Right?
It seems to me that a PC w/ Ubuntu OS is fully capable
of collecting, storing, and sending viruses.
Am I right or am I right?
[COLOR="Blue"]
JimS
Prostate Cancer Aware
[/COLOR]
...[/QUOTE]

Wow, I never thought of it that way, so I guess it would make sense to have an anti-virus.  


[QUOTE=ardchoille]...

I do, however, recommend installing and using rkhunter, chkrootkit and tripwire. 
...[/QUOTE]

Thanks, I will look into that.  


azz & carlosqueso - Thanks, that have eased many concerns and questions I had for a while.

---

### Post by RAOF on 2006-02-21
[QUOTE=JimS]...

If someone sent me an attachment which had a virus
on it and I in turn sent that attachment on to someone
else - I am probably protected, my friend up the line
might not be.
Right?  
If so, then it would seem to me that I have an obligation
not to forward viruses and should have an anti-virus
program or not forward anything.
Right?
It seems to me that a PC w/ Ubuntu OS is fully capable
of collecting, storing, and sending viruses.
Am I right or am I right?
[/QUOTE]
Except you would need to **deliberately** forward any virus-infected email on.  The virus can't forward itself - to do that it needs to infect your system.  So, if you regularly forward on messages like "try this new naked girl screensaver!!!!!111" with a .scr attachment, then yeah.  If you don't forward on random emails, then no.

While Ubuntu is perfectly capable of collecting, storing and sending viruses, you'd be manually forwarding those viruses on.

Edit: Actually, you have a point - there was once a lost-art of virus writing, whereby rather than simply exploiting the email program to get your code executed, you actually modified existing executables to run your virus (and infect other executables) first.  In this case, you could forward a perfectly reasonable executable attachment on, without knowing that it contained a virus.  
Man, that takes me back ;)

---

### Post by az on 2006-02-22
[QUOTE=JimS]...


It seems to me that a PC w/ Ubuntu OS is fully capable
of collecting, storing, and sending viruses.
Am I right or am I right?

...[/QUOTE]

Who cares?  My pc is also able to collect, store and send a lot of things.   I cannot take responsability for everything around me.  

Running a mail server is a different story.  If your computer functions as a mail relay, yes it becomes your responsability to scan for viruses.  

But this is not your responsability as a desktop user.  You are not being paid like your internet service provider to provide internet services!

---

### Post by JimS on 2006-03-07
...

azz writes:
"Who cares? My pc is also able to collect, store and send a lot of things. I cannot take responsability for everything around me.

Running a mail server is a different story. If your computer functions as a mail relay, yes it becomes your responsability to scan for viruses.

But this is not your responsibiiity as a desktop user. You are not being paid like your internet service provider to provide internet services!"

-------------------------

azz --- I have a different outlook.  To me it is like driving a car.
In North America and Europe one must buckel their seat belt.
The driver is responsible for seeing that passangers are
buckeled up.  When I drive I am responsible for my vehicle,
passengers, luggage, etc.  Driving your PC down the Internet
highway is a similar responsibiilty, IMHO.  Seeing that your PC
does not transfer a virus to others is YOUR responsibility.
Best way to meet your responsibility is to keep your PC clean,
don't let viruses in, and kill those that get by your first line
of defense.

"Do not figure on opponents not attacking;
Worry about your own lack of preparation."
Sun Tsu

JimS
I care.  Some people are responsible, some aren't.

,,,

---

