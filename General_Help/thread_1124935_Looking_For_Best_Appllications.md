---
title: "Looking For Best Appllications"
date: 2009-04-13
forum: General Help
---

### Post by Tanner2007 on 2009-04-13
I dont know much about ubuntu, My Im sorry if this wrong forum, I did not really know which other one it fit in.

Well Iwhould Like to know what do you guys think the best

Anti-Spyware
Anti-Virus
Firwall

That I Can Download For Free

Please And Thanks

---

### Post by Ericyzfr1 on 2009-04-13
Anti-Spyware...I don't have one
Anti-Virus..You can use Clam, Avast lot of folks here will tell you it is not necessary
Firewall included UFW, you can install firestarter so you can have a GUI for it.
To enable the firewall type:
sudo ufw enable
sudo ufw default deny

---

### Post by leonardo_neo on 2009-04-13
> Anti-Spyware
Anti-Virus

You don't need any to protect ***your*** system.

Ubuntu already has a firewall, which is not activated by default. To activate that, run the command as mentioned in above answer, or if you like to have a GUI for that, then you can install gufw. After installation, find the application in system--->administration, and then click the box next to enable firewall, and you are done.

---

### Post by lovinglinux on 2009-04-13
> **Ericyzfr1 said:**
> Firewall included UFW, you can install firestarter so you can have a GUI for it.
To enable the firewall type:
sudo ufw enable
sudo ufw default deny

Firestarter is not recommended anymore due to reasons already covered extensively in the forums. Anyways, Firestarter and UFW are not firewalls, they are just firewall managers, which means they are tools that allow you to create iptables rules (the real firewall) without knowing the commands.

As already mentioned, if you want a gui, then use gufw, which is the gui for ufw.

Recommended reading:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by mb_webguy on 2009-04-13
You don't really need anti-virus or anti-spyware, and you most likely don't need to mess around with the firewall.

I'd suggest reading the links in my signature about security before making any changes to your system in terms of security.  With Linux, being safe doesn't mean having certain software installed, but rather using good judgment (such as not using terminal commands beginning with "sudo" without first knowing exactly what they do, or installing and running random software from untrusted sources).

---

### Post by u.2 on 2009-04-14
Hi,
I was wondering why firestarter wasn't recommended any longer?

---

### Post by Chemical Imbalance on 2009-04-14
> **u.2 said:**
> Hi,
I was wondering why firestarter wasn't recommended any longer?

Firestarter has been out of development for over a year now, among other reasons that are debatable...

---

### Post by Tanner2007 on 2009-04-14
So then do you guys recommend a firewall and anti virus

or think its safe enough, right now on my windows besides windows firewall the only other firewall I have is built into my router (with also is plug into my pc I run ubuntu on)

Since as I said before I dont know almost anything about ubuntu but im learning, I just want to be sure everything is safe but if I dont need anything then just say so, or if the system is safe alone but still chances things can happen then I would want to use one of these anti virus and firewall applications

---

### Post by mb_webguy on 2009-04-14
Please read the links in my signature, and all will be explained.

No, you don't need to change the firewall settings in Ubuntu as a desktop user.  If you start setting up servers, you might want to start looking into configuring iptables.  

And the only practical reason to run anti-virus software on Linux is to prevent passing viruses along to Windows computers.  And personally, I think it's the responsibility of Windows users to adequately protect their own systems, and not yours as a Linux desktop user to prevent passing viruses to them.  If you have a dual-boot system, on the other hand, you may want to scan any shared partitions for viruses before booting into Windows.  But you shouldn't worry much about your Linux system becoming infected.

---

### Post by soltanis on 2009-04-14
Infecting a Linux computer, as opposed to a Windows computer, usually requires deliberate stupidity/trickery (i.e. unlike in Windows, where whoops Outlook auto-downloads/executes some application, file extensions are hidden behind other file extensions, and a complete lack of coherent security model means your system is compromised easily, infecting a Linux computer requires elevated priviledges).

This doesn't mean Linux is *immune* to viruses/worms. In fact, they can still attack your system, but the point is they cannot simply rely on a poor security model to infect your system, they have to actually exploit a program you're running in some way to escalate their priviledges and take over your system.

Unless you run a server or you execute random files you download from the Internet with root priviledges without checking them first, you don't usually have a lot to worry about. Serious exploits, when they are discovered, are usually patched very quickly in the open source community.

And iptables, your firewall, in its default configuration protects you fine.

The kind of security you should be worried about is the kind that is usually the weakest anyway; the length, strength and how often you change your password is pretty important if you are security-minded. A super-firewall and the most up-to-date anti-virus software cannot help you if you have a weak password.

---

### Post by lovinglinux on 2009-04-14
> **soltanis said:**
> And iptables, your firewall, in its default configuration protects you fine.

That's not true. The default configuration for iptables allows all traffic, so it doesn't protect anything. That doesn't mean the system is in danger, because the default Ubuntu installation also doesn't  have any listening servers. So all ports are closed. 

Anyways, the OP machine is behind a router firewall, so he probably doesn't need another firewall on the machine.

---

### Post by Tanner2007 on 2009-04-14
From what I read and hopefully correct the system is pretty much safe on its own

but win32 virus still can be in there just cant do anything and with that I dont want them to spread to my windows partition

---

### Post by Chemical Imbalance on 2009-04-14
All you have to worry about for now is using strong passphrases with mixed characters (no dictionary words), not downloading installable apps from the internet (use the repos, i.e. Add/Remove,Synaptic,sudo apt-get/aptitude install) unless you are sure of their credibility/safeness, not falling for social engineering tricks, etc...

Have fun with Ubuntu!

---

### Post by Tanner2007 on 2009-04-16
Thanks for the help guys, Heres another question so I wont have to start another post, unless no one answers it.

How can I make my windows vista the default loading OS, im so used to letting it load up while I do something else I keep forgetting it loads ubuntu instead of windows, I rather have windows load first

---

### Post by lovinglinux on 2009-04-16
> **Tanner2007 said:**
> Thanks for the help guys, Heres another question so I wont have to start another post, unless no one answers it.

How can I make my windows vista the default loading OS, im so used to letting it load up while I do something else I keep forgetting it loads ubuntu instead of windows, I rather have windows load first

You should create a separate thread for this topic, since it has anything to do with current topic.

Anyways, this might help you [http://www.google.com/search?q=boot+order+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0](http://www.google.com/search?q=boot+order+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0)

---

