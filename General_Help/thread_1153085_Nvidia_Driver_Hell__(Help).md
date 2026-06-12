---
title: "Nvidia Driver Hell  (Help)"
date: 2009-05-08
forum: General Help
---

### Post by dearmrdear on 2009-05-08
I'v gone as far as I can with research in the forums now I'll need some help.  I've tried to install the Nvidia drivers with no luck at all. Every time Jaunty starts to load it stops on "checking battery state" line. Each time I need to re-install the os to get it working again.
I'm runing 9.04 on a EVGA 780i ftw mobo with 9800gtx+ SLi. 
It runs in standard VGA mode.
I've insatlled 180.xx and 177.xxtwice from the update manager. 
I've manual intstall as descirbe on a couple of different threads. This is about the eighth time installing 9.04 ](*,) These installs have been on a dedicated hd dual booting with XP on a separate one.
This is really taking away from the whole Linux "charm" BUT It's well worth it considering how bad Vista sucks!

---

### Post by BslBryan on 2009-05-08
Hello, dearmrdear. :-)

Okay, first, you *did* restart your computer between changing drivers, right?  It sounds rather pointless, but it is very important.

Also, in your xorg.conf file, did you change your driver to "nvidia" in your "Device" section as opposed to anything else?

If you've done all of this, uninstall the drivers you've installed.

Then restart your computer.

Next, open up your terminal and paste this command
```
sudo apt-get install envyng-qt
```

Now, either go to Applications --> System Tools --> EnvyNG, or if you prefer the terminal, and want to run a textual interface, instead of a GUI,
```
sudo envyng -t
```

Just follow the instructions and restart your machine, and hopefully you'll be all fixed up.

Please keep us posted.  

Best to you, dearmrdear, and good luck. :-)

---

### Post by johnjust on 2009-05-08
For my laptop, when Envy and Restricted Drivers failed miserably, I found this post in the forums -> [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

It worked perfectly for me.  He even give directions on how to remove botched installs (of which I had one from Restricted Drivers, and another from EnvyNG)

---

### Post by dearmrdear on 2009-05-08
Thansks BslBrian, but i can't restart 9.04 it hangs on "Checking Battery.." I have to re-install the OS. I've tried installing this driver on a fresh install (no prop. drivers installed)
JohnJust: I tried that install about two hours ago and same thing. after installing it hangs on  "checking battery" 
Whats so wierd about this is theres a thread called "Nvidia rocks!" or something to the effect with so many people with simmilar setups as mine have no problems. The answer is here somewhere. I'm not giving up, ubuntu is just too cool.

---

### Post by DeMus on 2009-05-08
> **dearmrdear said:**
> Thansks BslBrian, but i can't restart 9.04 it hangs on "Checking Battery.." I have to re-install the OS. I've tried installing this driver on a fresh install (no prop. drivers installed)
JohnJust: I tried that install about two hours ago and same thing. after installing it hangs on  "checking battery" 
Whats so wierd about this is theres a thread called "Nvidia rocks!" or something to the effect with so many people with simmilar setups as mine have no problems. The answer is here somewhere. I'm not giving up, ubuntu is just too cool.

Can you boot into recovery mode? When you see Grub choose the second line. It has the same kernel but it is used to recover from problems like yours.

---

### Post by dearmrdear on 2009-05-08
Lemmy check! ...dual boot in progress.. shutting down.....brb

---

### Post by dearmrdear on 2009-05-08
Yes! Recovery mode available. I remember doing this a couple of days ago. I got the screen and did "try to repair graphic problem" but still hangs on "checking battery" then gives me the line
Ubuntu 9.04  tty 
then typical login

Xtra: when shutting down it did say "shutting down Gnome"

---

### Post by DeMus on 2009-05-08
> **dearmrdear said:**
> Yes! Recovery mode available. I remember doing this a couple of days ago. I got the screen and did "try to repair graphic problem" but still hangs on "checking battery" then gives me the line
Ubuntu 9.04  tty 
then typical login

Xtra: when shutting down it did say "shutting down Gnome"

Do I understand you correctly when I ask if you can log in now? If so, then please follow the advise BsiBryan gave you. Work from there.
Success

---

### Post by dearmrdear on 2009-05-08
Thanks DeMus! and sorry for the confusion I've only been working with linux for about 2 weeks.
Also:
Whats the cli command for uninstalling the nvidia driver?

---

### Post by dearmrdear on 2009-05-08
Sad news... Followed BslBrian's install to the letter and it still hung-up on "Checking battery state" Hmmmm, what now?
Would falling back to 8.4 do any good?

---

### Post by DeMus on 2009-05-08
> **dearmrdear said:**
> Sad news... Followed BslBrian's install to the letter and it still hung-up on "Checking battery state" Hmmmm, what now?
Would falling back to 8.4 do any good?

Can it be something else? I mean you always get this same error. It seems to me there is something else wrong in your PC.
Could you try to boot from the live CD to see if you also get the same error?
If so, there is something wrong in your PC, if not it is the installation on your hard disk.

---

### Post by dearmrdear on 2009-05-08
It might be a hardware problem but I kinda doubt it. I've looked at the hardware incompatibility list and haven't found anything. Here's my rig:

Intel E8400
EVGA 780i ftw mobo with 2gb ram
2 x XfX Geforce 9800gtx+ (running in SLi)
Seagate 500gb hd with XP pro
Seagate 250gb hd with Ubuntu 9.04

In XP my games (Crysis, etc) run like a charm, not one problem. I've installed and run 9.04 just fine. It boots and runs fast. I have'nt tried running any graphic heavy app (dvd). Without the nvidia driver it won't let me enable any desktop animation eye candy (no big deal).
I really think it is something I'm doing wrong. I seem to be the weak link in the chain, even though I've learned a huge amount in the last two weeks. I will not surrender! I love the philosophy of linux and WILL figure it out! :biggrin:

---

