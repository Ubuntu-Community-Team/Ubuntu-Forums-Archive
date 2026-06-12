---
title: "Ubuntu Virus Protection"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-20
Hi I'm a newbie.  Since I am from the Windows world, I am used to having to keep up with all the virus protection, spyware, etc.  Is there virus protection for Ubuntu 704 desktop ed?  I do plan on using this machine as a quasi file server and DNS.

I am a newbie to this.  Could someone give me a step by step.  Thank you so much!

---

### Post by g2g591 on 2007-08-20
welcome to linux, there are no viruses or spyware for linux, so there is no virus protection needed. if you want, you can look in synaptic package manager for an antivrus if you really feel you need one

---

### Post by arvadawest on 2007-08-20
ru serious?? No virus protection?  Why?  Wow!

---

### Post by newlinux on 2007-08-20
Linux has some better security built in and people just aren't as interested in writing linux viruses. however, you can pass on windows viruses to other computers. ClamAV might be an antivirus program to look into. I believe it is in the repos.

---

### Post by newlinux on 2007-08-20
oh and for firewall protection you can look into firestarter, if you feel you need it.

---

### Post by arvadawest on 2007-08-20
Hi newlinux,
Thank you.  I did install Firestarter.  It is not as complex as other firewalls programs, but I guess I can write some rules for it.

How to I get to clamav?  I think I need to read into this repository and where it is located.  Thanks, but I am new to this.

---

### Post by newlinux on 2007-08-20
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Anti-virus](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Anti-virus)

Make sure to enable extra repositories.

In general, the ubuntuguide.org site is good for newbies, but feel free to ask questions here anyway.

---

### Post by arvadawest on 2007-08-20
Thank you so much.  Everyone on this site has been so nice and helpful.  I will check out the sites you typed.  Thank you again!  -aw

---

### Post by arvadawest on 2007-08-20
Hi Thanks.  What is the difference between the nod32 and clamav?  Are they both good?  thanks.  -aw

---

### Post by newlinux on 2007-08-20
I think they are both good, I've heard of both - but I'm more familiar with clamav. It's more popular in my circles...

---

### Post by mtbsoft on 2007-08-20
I can't comment on NOD in the Linux world (don't need it) but found it to be one of the best of the Windows choices.

---

### Post by gutterballk7 on 2007-08-20
Personally, I like Avast! Antivirus for Windows... and if I felt I needed antivirus for Linux that ran real-time, I would also use Avast! for Linux. It's free after you register. You can register as much as you want, and each registration works for 14 months. Pretty easy to do.

---

### Post by Perfect Storm on 2007-08-21
F-prot: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

AVG: [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by arvadawest on 2007-08-21
Excellent and thank you all so very much.  I will look into all these.  This is a great Forum!

Dr. AW

---

### Post by arvadawest on 2007-08-22
Hi,
I found the clamtk virus scanner.  I  think this is what I need?  Problem is, is that I cannot get the updates.  It tells me I need to be "root"

Please keep in mind that I am a newbie, so I do not know how to logon as root.  I am lost.  Thanks.

---

### Post by saru411 on 2007-08-22
to be root you must type in sudo before the command. when you type sudo before a command it will ask you for your password, this is to make sure you know you are about to write over configuration files. so only use sudo when it is needed.

---

### Post by arvadawest on 2007-08-22
Hi Saru,
I typed in:  sudo and it gave me this:

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

I typed in su and it prompted me for a password.  When I typed it in, it would not authenticate.

How do I setup my root password and/or profile?  Thanks.  -aw

---

### Post by saru411 on 2007-08-22
think of sudo as "mother may i" or "the king says" you put it in front of a command to make it run as root. if you type the command into terminal with sudo before it like this"sudo do_my_laundry.exe" it will run the program(unlikely to actually fold your clothes too) ;)
i would recommend just taking it easy. you will not need a virus scanner for the moment so just get the things you need to enjoy yourself..too much work will make you tired and stressed about not getting everything running. i have faith in ya. good luck

---

### Post by newlinux on 2007-08-22
for more info on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mtbsoft on 2007-08-27
> **saru411 said:**
> do_my_laundry.exe
Where can I download this from?!?!

> **saru411 said:**
> unlikely to actually fold your clothes too
Damn!

---

### Post by alfredeneuman on 2007-08-28
Obviously you can pass a virus along using Linux. I was downloading music from frostwire onto my sansa mp3. My mp3 disk became corrupted from a virus, i lost 1500 songs, and I wound up reformatting. Luckily I have backup copies. I didn't think this was possible with Linux. A hard lesson learned for me. Just thought I'd pass this along.

---

