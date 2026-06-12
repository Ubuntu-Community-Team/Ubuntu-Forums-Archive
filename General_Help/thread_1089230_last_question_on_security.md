---
title: "last question on security"
date: 2009-03-06
forum: General Help
---

### Post by grubster on 2009-03-06
in windows you have key loggers viruses trojans ect ect are you telling me there are no security problems with linux? Im sorry for posting the same thread, wont happen again. I wont ask about security again also but i just cant believe its that secure from all threats and if so why isnt this system used by the masses. Just to let you know im not knocking the system in any way, I like it more and more every day. I see no reason for windows!

---

### Post by martrn on 2009-03-06
Yes you can get key-loggers that either sore key-logging events and send them somewhere or else store them and do whatever.

A trojan-horse is just a program pretending to be one thing but is in fact something else.  Someone could write a program to pretend to sit in a task bar and be a reminder to send an email but in fact is sending emails to your address book, yes you could get one.

Whats a virus ?

---

### Post by Mud.Knee.Havoc on 2009-03-06
Enough with the insults, guys...

Anyway, no system is completely safe.  With Linux, you don't have the problem of viruses "in the wild" like Windows does.  Still, you have to be smart.  Use a firewall, use non-standard ports, don't go to shady websites, use strong passwords (and different ones on each site you go to).  Never reuse your system passwords when signing up for some website.  

If somebody really wants to get into your system and has the time, dedication and patience to do it, I'd say that he's got a decent chance.

---

### Post by Slim Odds on 2009-03-06
> **Mud.Knee.Havoc said:**
> Enough with the insults, guys...

Anyway, no system is completely safe.  With Linux, you don't have the problem of viruses "in the wild" like Windows does.  Still, you have to be smart.  Use a firewall, use non-standard ports, don't go to shady websites, use strong passwords (and different ones on each site you go to).  Never reuse your system passwords when signing up for some website.  

If somebody really wants to get into your system and has the time, dedication and patience to do it, I'd say that he's got a decent chance.

Despite what some others might say, my point was that when you run and installer with "sudo", you are giving it **full access to your machine.**

The ".deb" packages have post-install scripts that **run as root.** This means that they have **total control** of your machine.

They can do anything they want. This is how new kernels are installed. How much plainer can it be?

That's why I was mentioning that you **really do** need to trust the repositories that you use.

P.S. Viruses in window get into your system through various insecurities. That is different than running an installer from just anyone (which is what happens when you use a repository from who knows where).

---

### Post by mb_webguy on 2009-03-07
> **grubster said:**
> in windows you have key loggers viruses trojans ect ect are you telling me there are no security problems with linux? Im sorry for posting the same thread, wont happen again. I wont ask about security again also but i just cant believe its that secure from all threats and if so why isnt this system used by the masses. Just to let you know im not knocking the system in any way, I like it more and more every day. I see no reason for windows!

Read the link in my signature.  You might also want to read [this post]("http://ubuntuforums.org/showpost.php?p=6650020&postcount=3").

The simple fact of the matter is that programs do not install themselves or run themselves in Linux, and Linux file permissions prevent programs run by regular user accounts from doing damage to your system.  

So, can you get something like a keylogger?  Sure -- if *you* install one.  But such a program absolutely can *not* install itself without your knowledge as it can in Windows.  Could such a program run automatically without your knowledge, should you happen to install one?  Well, maybe, if you don't pay attention to what's going on.  It could install itself as a service, but those are easy enough to spot and kill.

If you install software from a deb, removing that software is as simple as a single command in the terminal, or a couple of clicks in Synaptic.  If you install software from an installer script, it's easy enough to look at the script to see what files were installed, and then delete them.  Even if you compile software from source, you can use the makefile to remove all files installed (and since you can actually look at the source code to see what the software does, it's not likely that malicious code would be distributed this way anyway).

The only real risk when installing software is if you should install software using a binary installer.  But these are somewhat rare on Linux, and generally come from large commercial developers, such as Adobe, Google, or nVidia, and so are generally trustworthy (since businesses generally don't want to piss off their customers).  And even here, you have to download the binary, change the permissions, and then run it.  It can not run itself.

Basically, as long as you use a modicum of common sense when it comes to adding software, and particularly if you stick to using open-source software, you really shouldn't be worried about malware on Linux.

---

### Post by entr3p on 2009-03-07
> **mb_webguy said:**
> Read the link in my signature.  You might also want to read [this post]("http://ubuntuforums.org/showpost.php?p=6650020&postcount=3").

The simple fact of the matter is that programs do not install themselves or run themselves in Linux, and Linux file permissions prevent programs run by regular user accounts from doing damage to your system.  

So, can you get something like a keylogger?  Sure -- if *you* install one.  But such a program absolutely can *not* install itself without your knowledge as it can in Windows.  Could such a program run automatically without your knowledge, should you happen to install one?  Well, maybe, if you don't pay attention to what's going on.  It could install itself as a service, but those are easy enough to spot and kill.

If you install software from a deb, removing that software is as simple as a single command in the terminal, or a couple of clicks in Synaptic.  If you install software from an installer script, it's easy enough to look at the script to see what files were installed, and then delete them.  Even if you compile software from source, you can use the makefile to remove all files installed (and since you can actually look at the source code to see what the software does, it's not likely that malicious code would be distributed this way anyway).

The only real risk when installing software is if you should install software using a binary installer.  But these are somewhat rare on Linux, and generally come from large commercial developers, such as Adobe, Google, or nVidia, and so are generally trustworthy (since businesses generally don't want to piss off their customers).  And even here, you have to download the binary, change the permissions, and then run it.  It can not run itself.

Basically, as long as you use a modicum of common sense when it comes to adding software, and particularly if you stick to using open-source software, you really shouldn't be worried about malware on Linux.

Thank you for a very detailed post. I agree fully :). *cough*

---

