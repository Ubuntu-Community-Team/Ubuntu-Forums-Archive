---
title: "Virus found on my ubuntu / linux machine // plz advice!?"
date: 2009-01-27
forum: General Help
---

### Post by hihihi on 2009-01-27
Virus found on my ubuntu / linux machine // plz advice!?

running ubunut 8.10, 64bit.
AVG 7.5 with the latest def. discovered a virus in my linux-system:

"Downloader.Obfuskated" in /lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_transport_fc.ko 
and
/lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_mod.ko

i've found someone reporting this in a SUSE-forum aswell, but there are no useful answers: [http://forums.opensuse.org/pre-release-beta/386021-obfuskated-meta-virus-discovered.html](http://forums.opensuse.org/pre-release-beta/386021-obfuskated-meta-virus-discovered.html)

and on ubuntu-forum another report yet with no informative answers:
[http://ubuntuforums.org/showthread.php?t=969436&highlight=obfuskated](http://ubuntuforums.org/showthread.php?t=969436&highlight=obfuskated)

i think the highest risk we have in the linux world is the blind trust everyone has, that no security-threat could ever be a risk to linux users. if we look back to history, than this would be the perfect circumstances, think of troja and the trojan-horse, the greeks used trojas self-in-sureness and killed them from the inside...

**my questions:**
1) why is it there?
2) how could it find a way to the kernel?
3) what threat does it really mean? is it dangerous?
4) how can i remove it?

pls advice what to do from here, i am clueless...

---

### Post by mb_webguy on 2009-01-27
It is possible for you to download a virus-infected file, but it cannot infect your Linux installation.  The only real danger is that you can pass this infected file to a Windows computer, where it *can* do damage.

Btw, you might want to read the link in my signature on security in Ubuntu.

---

### Post by bgerlich on 2009-01-27
It's a false alarm.

This is a windows virus.

---

### Post by PC_load_letter on 2009-01-27
Does AVG run under Linux? Isn't it a Windows only antivirus? So are you running AVG with WINE?

---

### Post by redseventyseven on 2009-01-27
> **PC_load_letter said:**
> Does AVG run under Linux? Isn't it a Windows only antivirus? So are you running AVG with WINE?

AVG have produced software native to Linux as well as Windows - here's an announcement from about 3 years ago: [http://free.avg.com/4040](http://free.avg.com/4040)

The first advice I can give you about how to get rid of it is to calm down, and not panic. Then give yourself plenty of time to sort it out - enough time so that you can read instructions carefully and patiently.

I do agree to some extent that Linux users can seem complacent when it comes to viruses and spyware, but in my opinion that complacency is somewhat justified because it's far less easy to accidentally run a virus program in such a way as it has all the privileges it needs to do significant harm. On the other hand, however, the fear and panic approach embodied in the Windows attitude of "the more security software I have running on my system the better" is arguably more damaging - it's lead to the creation of fake antivirus software such as the despicable "Antivirus 2009" ([http://www.2-spyware.com/remove-antivirus-2009.html](http://www.2-spyware.com/remove-antivirus-2009.html)).

---

### Post by apiman on 2009-01-27
AVG realeased a version of it's anti-virus for Linux, but I couldn't find it today:
[http://free.avg.com/4040]("http://free.avg.com/4040")

First of all, I'm a Linux only user and I'm very happy with it. 

I'm quite concern about how Linux users believe they could never get infected by a computer virus. Since a virus is just a computer program that does nasty things, there is no reason for a virus not to run on Linux. It's true that it wouldn't be easy for it to break the system since it would run as our own user. That's the big problem, the worst things for a user can be done within it's user account. As your own user, a virus could read and delete all documents you use (documents, images, videos...), it can read your web browser profile (with saved passwords if you haven't encrypt them) and many other information that we appreciatte much more than our linux installation.

Macs are Unix based systems as well and there are virus for them as well. As linux will become more and more used, virus could become a real threat for it's users and it would be very bad for linux if the community doesn't open it's eyes.

My advice would be: "Be as careful as you would be in a Windows box."

---

### Post by mlentink on 2009-01-27
> **apiman said:**
> 

My advice would be: "Be as careful as you would be in a Windows box."

Agreed

Any OS is only as secure as its user...
That  being said, some OS's do help the user more in being secure than others do

---

### Post by mb_webguy on 2009-01-27
Also agreed.  

On Linux, any virus that does get on my system can automatically run itself without me actually entering the command to run it.  Even then the damage it could cause is limited to my userspace, unless I was silly enough to run it as root.  And if I'm that careless about how I use my computer, I probably do more damage on a regular basis than the virus ever could.

In Windows, the virus can run itself when the file it's hiding in is opened, and since the default Windows user account has administrator privileges, it can run through a system like a squirrel after a can of Red Bull.

But in both cases, the virus wouldn't have gotten on the system in the first place if it hadn't been for the guy at the keyboard.  

Besides, viruses aren't the only security risk faced in this brave new world of the internet.  A cracker can still exploit system vulnerabilities to access a system, and then who cares about a silly virus?

---

### Post by hihihi on 2009-01-27
> **PC_load_letter said:**
> Does AVG run under Linux? Isn't it a Windows only antivirus? So are you running AVG with WINE?

hello, thx everyone for being with me on this one.

yes AVG has a linux version and it is being updated regularly.
for those who want to try AVG-linux version, go here:
[http://free.avg.com/download](http://free.avg.com/download)
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)
perhaps some of u would be so kind and scan their boxes and see, if this is a single problem or if this concerns like the whole community...
i am going to scan my other ubuntu-pc and see what it says...


I am asking myself how this virus could install itself in the kernel?
being so, it should gain highest rights, being able to execute what it is supposed to do? 
there is nearly no information about this virus, nothing that clearly indicates that this is a windows-only virus.
its threat is regarded as low. but what it could do, as far as i could find out, is downloading spyware and trojan-horses or other malware that will connect my internet browser to the malwares site!? 
i am quite puzzled....
does this virus come with the kernel-updates?
thx>

---

### Post by mb_webguy on 2009-01-27
Everything I'm reading about this virus is that it's a Windows-only virus, and that AVG for Linux pings false-positive when scanning Linux systems, particularly the SCSI subsystem of the kernel.

Relax, it's nothing to worry about.

---

### Post by geirha on 2009-01-27
It could be a false positive; the two files might coincidentally have similarities with that virus. One way you could check if this is the case, is to first take a checksum of those files right now.
```
md5sum /lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_transport_fc.ko /lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_mod.ko
```

Save the checksums in a temporary file. Then, find which package installs those files:

```
dpkg -S lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_transport_fc.ko /lib/modules/2.6.27-XX-generic/kernel/drivers/scsi_mod.ko
```
Should be linux-image-2.6.27-XX-generic, but whichever package it is, reinstall it:
```
sudo aptitude reinstall linux-image-2.6.27-XX-generic
```

Run md5sum again and compare it with the previous md5sums. If they are equal, then it's very likely a false positive.

---

### Post by TheLions on 2009-01-27
> **apiman said:**
> 

I'm quite concern about how Linux users believe they could never get infected by a computer virus. Since a virus is just a computer program that does nasty things, there is no reason for a virus not to run on Linux. It's true that it wouldn't be easy for it to break the system since it would run as our own user. That's the big problem, the worst things for a user can be done within it's user account. As your own user, a virus could read and delete all documents you use (documents, images, videos...), it can read your web browser profile (with saved passwords if you haven't encrypt them) and many other information that we appreciatte much more than our linux installation.
"

virus couldn't do much damage on Linux and Mac but Trojan could! Trojan could start a keylogger and wait until you type a password!

---

### Post by hihihi on 2009-01-27
deleted

---

### Post by hihihi on 2009-01-27
thank you.
i am quite critical about lack of info...

@ geirha,: good tip here, thanks, i will do that...

---

### Post by Richardcavell on 2009-05-29
Hi.  For the record, I'm getting it too.  Ubuntu 9.04 64-bit on a Mactel.

/lib/modules/2.6.28-11-generic/kernel/drivers/scsi/scsi_transport_fc.ko  Virus found Downloader.Obfuskated

I'd see it as a false positive.  I cannot fathom how my Linux box could have been infected by a Windows virus.  I don't use SCSI at all!

Richard

---

### Post by VMC on 2009-05-29
Here's [another]("http://www.linuxquestions.org/questions/linux-security-4/avg-anti-virus-699450/") discussion on the subject. I have that file and here are my sum results:

> $ sha1sum /lib/modules/2.6.28-11-generic/kernel/drivers/scsi/scsi_transport_fc.ko
10e0f41e8a7a694e2d7f5d4698f3d34b30b13241  /lib/modules/2.6.28-11-generic/kernel/drivers/scsi/scsi_transport_fc.ko

---

### Post by haiyun211 on 2009-06-04
Hey guys,

I am new to linux and I agree that a virus can very easily be used on linux systems and was just wondering what kind of protection I could use to be on the safe side some say avg is good and others say its not so kind of on the fence with this one.  I dont know much so I dont want a false positive that will screw up my computer when removed.  Any adivce apretiated thanks.

---

### Post by Iusedtowearatie on 2009-06-04
Try this: [http://www.clamav.com/about](http://www.clamav.com/about)

---

### Post by haiyun211 on 2009-06-04
Is there an easy way to install it or do you have to download the tar and compile it?

---

### Post by Celauran on 2009-06-04
> **haiyun211 said:**
> Is there an easy way to install it or do you have to download the tar and compile it?

```
sudo aptitude install clamav
```

Waste of resources, though, as far as I'm concerned.

---

### Post by albinootje on 2009-06-04
> **haiyun211 said:**
>  I am new to linux and I agree that a virus can very easily be used on linux systems 

This is not correct. 

Linux can have problems with trojans if the user downloads source code from malicious third parties etc. 
But viruses will not easily be wide-spread in Linux, at least not via the "MS-Windows autorun" and "double-click" on attachments in email-clients.
> 
and was just wondering what kind of protection I could use to be on the safe side some say avg is good and others say its not so kind of on the fence with this one.  

In my opinion AVG is not the best choice to have for anti-virus software in Linux.
Only their old obsolete version has a GUI for Linux, and newer version seem to focus on their sales for Linux ... servers.
And you need Dazuko for "real time" anti virus scanning.
Klamav might be more interesting to use imho.

See also here : 
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)

For the rest I recommend the WOT and NoScript addon in Firefox.

---

### Post by jerrrys on 2009-06-04
what good is this ??

[ATTACH]116450[/ATTACH]

---

### Post by Nexusx6 on 2009-06-04
I just wanted to swing in momentarly and drop my two cents to the new users; there seems to be a lot of unjustified panic going on in this thread.

Linux is a very, very secure operating system. Your chances of ever catching a virus are almost imeasurable small for a great deal of reasons. The anti-viruse programs that we do have are in fact generally NOT even installed to scan for linux viruses! Sys admins/dual booters/ or linux users on a windows network install them to check for windows viruses before they spread to the rest of the network. 

All things considered, many people feel that installing an anti-virus on a users system with no other purpose than to check for viruses on that linux box is a waste of resources.

---

### Post by joe26 on 2009-06-08
the virus cant hurt :KSYOUR:KS system, but any other windows os who gets neer you can get the virus

---

### Post by coffeecat on 2009-06-08
> **jerrrys said:**
> what good is this ??

[ATTACH]116450[/ATTACH]

What's wrong with it? If you click on the link under Downloads you get to this:

[http://free.avg.com/download](http://free.avg.com/download)

Where you can get the free 8.5 version.

---

### Post by michy99 on 2009-06-08
> **coffeecat said:**
> What's wrong with it? If you click on the link under Downloads you get to this:

[http://free.avg.com/download](http://free.avg.com/download)

Where you can get the free 8.5 version.

Just be aware that the 8.5 version is command-line only. No GUI.

---

