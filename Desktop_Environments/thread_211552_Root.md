---
title: "Root?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by That Guy X on 2006-07-08
Hi im useing Kubuntu and i need root privlages to install a driver i have. But theres no root acount what do i do to give my acount root privlages?

---

### Post by FredB on 2006-07-08
There is - by default - no full access to root account.

If you need root's right :

sudo + commands

That's all ;)

---

### Post by aysiu on 2006-07-08
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by That Guy X on 2006-07-08
I tryed the sudo command and it asked me for a password then when i typed it in it said sudo + command not found.

---

### Post by Thund3rstruck on 2006-07-08
You can enable the root account if you want. 

```

sudo passwd root

```

---

### Post by aysiu on 2006-07-08
Instead of describing what happened, can you copy and paste exactly what you typed and exactly what the error message was?

---

### Post by aysiu on 2006-07-08
> **Thund3rstruck said:**
> You can enable the root account if you want. 

```

sudo passwd root

```
Why would you want to do that? If you want to log in as root from the terminal, you can just do ```
sudo -s
```

---

### Post by That Guy X on 2006-07-08
I cant copy/paste the error messages im getting becouse i dont have internet. I have to restart my comp and go back to windows to reply. Ive probily tried about every linux distro there is and my internet never works. So i thought my DSL just wasnt compadible and gave up. But yesterday i installed linux on my xbox and the internet works on that. So i think my motherboard isnt compadible wich is why ive been lokking for drivers for it.

---

### Post by FredB on 2006-07-08
> **That Guy X said:**
> I tryed the sudo command and it asked me for a password then when i typed it in it said sudo + command not found.

I meant by "+ command" the command you need to make work as root !

/me is tired...

---

### Post by FredB on 2006-07-08
> **Thund3rstruck said:**
> You can enable the root account if you want. 

```

sudo passwd root

```

And kill one of the best security on ubuntu linux ?

---

### Post by benmoreassynt on 2006-07-08
> **That Guy X said:**
> Ive probily tried about every linux distro there is and my internet never works. So i thought my DSL just wasnt compadible and gave up. But yesterday i installed linux on my xbox and the internet works on that. So i think my motherboard isnt compadible wich is why ive been lokking for drivers for it.

That's funny - are you running a very old computer? Should be a matter of just sticking the cable into the back of your PC, unless you want wireless networking. Wireless can be tricky to set up, but general networking is incredibly simple.

You can use alacarte (In Applications/Accessories) to add 'run as a different user' to your System Tools. That is a bit more friendly than messing about with the terminal if you are new to Linux. However you still need to know the command for the application you want to use (eg "gedit" for text editor with root privileges, 'nautilus' for a file browser with root privileges). Unless you have changed it the password for root will be the same as the one you use to login to Ubuntu.

It's one of the things that takes a while to get used to when you are new to Ubuntu.

---

### Post by That Guy X on 2006-07-08
Its acualy a fairly new pc. I have a Emachines T6216  hooked up to verizon DSL modem model 327W westell. Its wierd it works fine on windows but on every linux it fails to configure with DHCP. eth0 is there it just doesent work for some reason :-({|=

---

### Post by benmoreassynt on 2006-07-08
> **That Guy X said:**
> Its acualy a fairly new pc. I have a Emachines T6216  hooked up to verizon DSL modem model 327W westell. Its wierd it works fine on windows but on every linux it fails to configure with DHCP. eth0 is there it just doesent work for some reason :-({|=

I did a quick Google search and there seems to be a problem with network recognition for the T6216. Take a look at this page: [http://www.oceanpark.com/~donc/emachines.html](http://www.oceanpark.com/~donc/emachines.html)
The page is talking about Fedora Core, but it sounds like the problem you are having. If so it may relate to the Linux kernal - although I would expect Ubuntu to already have the requisite version. I don't know much about kernal stuff, but other people on these forums will do.

Frustrating for you, but if you can be bothered to tinker you will be able to get it working, I am sure.

If nothing else, buy an external network card which works with Linux and use that.

---

### Post by That Guy X on 2006-07-08
hmm i guess i just need to buy a new ethernet card.

My frend said not to buy emachines becouse there not good with compadibility.Probily should have listned :mad:

---

### Post by That Guy X on 2006-07-08
Ubuntu should probily add emachines next time they update there drivers though.

---

### Post by shivs on 2006-07-29
I also have a T6216, I personally havent had any network problems other than the fact my onboard lan is assigned to eth1 and pci network adapter is eth0.  But my machine was plagued with problems with the 2.6.15 kernel, couldnt even boot off the dapper cd without having to FULLY disable apic (bios and kernel options) but just today I updated my firmware to 3.9(previously i had 3.6) 

The motherboard is a MSI RS480M2, [http://www.msi.com.tw/program/support/download/dld/spt_dld_detail.php?UID=639&kind=1)](http://www.msi.com.tw/program/support/download/dld/spt_dld_detail.php?UID=639&kind=1)).  
Since this machine doesnt come with a floppy drive and I had windows on another partition I used the Live Update and flashed it in windows (probably the preferred method would be to flash off a boot cd, or hook up a floppy drive).  But now pretty much everything works FINALLY :D

---

### Post by jgcamp99 on 2006-07-30
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For obvious reasons. You can always go backwards to disable graphical logons, relock the password if you feel that going back to a solely sudo setup is more desirable. I prefer the flexibility of being able to use root. I still can't understand the claim that having root being able to login graphically is any more or less secure. I guess, if you're counting attempts or keystrokes, then the extra headache of the attempts makes sudo more secure. If an expert is hacking your computer, and only got a user password such as the default user id and password. It would take an expert one attempt to figure out that root wasn't enabled, they would use sudo commands just the same as anyone else that has posted to do so indicates. The secure sudo user id and password has been compromised. They could just as easily reenable root and it would be no more or less secure at that stage or any other stage of the process of being hacked.

---

