---
title: "KDE destroyed - need to reinstall"
date: 2008-08-20
forum: Desktop Environments
---

### Post by rhardie on 2008-08-20
911 call

Damaged/destroyed my KDE desktop and need to re-install from command line.

Need guidance to re-install KDE but have massive error message codes when I attempt command line downloads.

I was in Synaptic and uninstalling some pgp packages.  I'm not sure what happened, but my system began uninstalling my applications to include my KDE desktop.  Unbelieveable!

I came back to my computer and attempted to restart and all I have is the command line.

My data files are intact (thank goodness I don't need to re-load them) so it appears that my desktop is destroyed.

My thoughts are that there are some corrupted files that prevent me from downloading the KDE desktop via the command line.


Attempted to re-install but get many,many,many error codes such as:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardie-securrity/main/i18n/Translation-en_us.bz2](http://security.ubuntu.com/ubuntu/dists/hardie-securrity/main/i18n/Translation-en_us.bz2)  Could not resolve 'security.ubuntu.com'

Lots of "could not resolve" such as 'mx.archive.ubuntu.com'

I did Apt-get update and received "Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/distrs/hardie/updates/multiverse/i18n/Translation-en_us.bz2](http://mx.archive.ubuntu.com/ubuntu/distrs/hardie/updates/multiverse/i18n/Translation-en_us.bz2) Could not resolve 'mx.archive.ubuntu.com'

A secondary concern is that my applications may not run.  Example:  I am running Virtual Box for a Windows application related to my work and I'm hoping there is a config file for desktop icons that will load up and my virtual machine can be used without having to re-install it and the guest OS.

This is a 911 call as I need to be back in operational mode in the morning for my work.

I've had "Reverse Midas Touch" this week; everything I touch turns to poop.  ;-) 

Thank you in advance for any assistance.

---

### Post by prshah on 2008-08-20
> **rhardie said:**
> 
Damaged/destroyed my KDE desktop and need to re-install from command line.

Attempted to re-install but get many,many,many error codes such as:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardie-securrity/main/i18n/Translation-en_us.bz2](http://security.ubuntu.com/ubuntu/dists/hardie-securrity/main/i18n/Translation-en_us.bz2)  Could not resolve 'security.ubuntu.com'
Lots of "could not resolve" such as 'mx.archive.ubuntu.com'



The failed to resolve errors mean that it is unable to locate the internet addresses; are you connected to the Internet? Do you need to know how to do so from the command line? In that case, we need to know how your Internet has been setup.

== OR ==

You can get hold of a Kubuntu alternate CD and use that to reinstall your Kubuntu. Post back for information on how to add the CD to your sources list and use it to reinstall Kubuntu.

== OR ==

(Warning: This is a desperate-use suggestion only). It's very likely that all the packages you require are sitting in your computer. Here's a risky shot; boot into recovery mode, and give these commands (Note, no sudo):```
cd /var/cache/apt/archives/
dpkg -i *.deb
```

This will reinstall all .deb packages found in /var/cache/apt/archives (which is where all packages are downloaded first, before being installed.)

---

### Post by rhardie on 2008-08-20
Thanks.  "Reverse Midas Touch" occurred again after a modem went down and getting it repaired was all day.  I'm going to give my brain cells a rest and then address this issue.

I'm getting VERY cautious about what I do now.

I'll give some thought to your suggestion before I start tickling the keyboard with commands.  ;-)

Thank you, again.

---

### Post by rhardie on 2008-08-20
Just ate some food.  Wow, that helps!  Now back to Kubuntu work and "Work" work.

I would like to do one of two things.

a) reload ONLY the KDE desktop but use the newer 4.1
b) move all of my data files off to another drive or DVD and then reload Kubuntu

I would like to attempt option "a" first.

There are two customers to call this evening while I wait for a reply.

Most of my work is run on Linux and I'm as happy as a pig in mud to be on Kubuntu!

Once again, I DO appreciate your assistance.

RH

---

