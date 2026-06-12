---
title: "Easy Peasy (ubuntu 8.10) for Eee PC 1000 and VirtualBox"
date: 2009-01-14
forum: General Help
---

### Post by bioshake on 2009-01-14
Hey guys. I'm having problems getting Virtualbox to run in Easy Peasy 1.0 (which is based on ubuntu 8.10 - geteasypeasy.com).

I tried the 2.0.4 OSE version (found in synapic) and it installed fine but kept giving me an error when I tried to start a VM that I had configured for the first time. The error was something to do with DKMS (which I have the latest version of installed). And it was telling me to run /etc/init.d/vboxsrv setup (or something close to this). I tried to do this as root but this version of the software doesn't seem to allow the 'setup' parameter.

So i removed it and tried 2.1. It has an install wizard that tries to run that same command, fails and then refers me to the install log to see what happened.

Which is as follows:

> 
    Attempting to install using DKMS
    removing old DKMS module vboxdrv version

    Error! Invalid number of parameters passed.
    Usage: remove -m <module> -v <module-version> --all
    or: remove -m <module> -v <module-version> -k <kernel-version>
    removing old DKMS module vboxdrv version

    Error! Invalid number of parameters passed.
    Usage: remove -m <module> -v <module-version> --all
    or: remove -m <module> -v <module-version> -k <kernel-version>

    ------------------------------
    Deleting module version: 2.1.0
    completely from the DKMS tree.
    ------------------------------
    Done.

    Creating symlink /var/lib/dkms/vboxdrv/2.1.0/source ->
    /usr/src/vboxdrv-2.1.0

    DKMS: add Completed.

    Error! Your kernel source for kernel 2.6.27-8-eeepc cannot be found at
    /lib/modules/2.6.27-8-eeepc/build or /lib/modules/2.6.27-8-eeepc/source.
    You can use the --kernelsourcedir option to tell DKMS where it's located.
    Failed to install using DKMS, attempting to install without
    Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.


I'm stumped.. 

Could one you fine gentlemen please help me get this working? Thanks!

---

### Post by redilyn on 2009-01-14
I think this will help

```

sudo apt-get install linux-headers-$(uname -r) build-essential


```

After you run that command try to install OSE again

---

### Post by bioshake on 2009-01-14
> **redilyn said:**
> I think this will help

```

sudo apt-get install linux-headers-$(uname -r) build-essential


```

After you run that command try to install OSE again

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.27-8-eeepc

---

### Post by redilyn on 2009-01-14
Hummm, I have it using eeebuntu.

The eeebuntu files are added in third party under software sources. I'm looking for directions to help you add them. I'll get back to you

---

### Post by redilyn on 2009-01-14
I think you can add the necessary files by doing the following

Open Software Sources -> Third Party Software -> Add

Apt Line - deb [http://www.array.org/ubuntu](http://www.array.org/ubuntu) intrepid eeepc

Then run

```

sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential

```

Let me know how you make out

---

### Post by bioshake on 2009-01-14
> **redilyn said:**
> I think you can add the necessary files by doing the following

Open Software Sources -> Third Party Software -> Add

Apt Line - deb [http://www.array.org/ubuntu](http://www.array.org/ubuntu) intrepid eeepc

Then run

```

sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential

```

Let me know how you make out

Hey - thank you so much for your help thus far!

I added the apt line and afterwards it asked me to reload (which I did) then I got:

W: GPG error: [http://www.array.org](http://www.array.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B25830FFD0C2C24

I'm going to try the rest anyways but I'm thinking it probably needs the key first?

Update:  This is what I got when I did the apt-get update:

Fetched 198B in 1s (177B/s)
W: GPG error: [http://www.array.org](http://www.array.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B25830FFD0C2C24
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by redilyn on 2009-01-14
Opps ya i forgot about the key.

Try this, gonna start from scratch so you should remove the entry i suggested above

```

wget http://www.array.org/ubuntu/array-intrepid.list
sudo mv -v array-intrepid.list /etc/apt/sources.list.d/
wget http://www.array.org/ubuntu/array-apt-key.asc
sudo apt-key add array-apt-key.asc
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential

```

This should do it, sorry about taking the long way to get there.

---

### Post by bioshake on 2009-01-14
> **redilyn said:**
> Opps ya i forgot about the key.

Try this, gonna start from scratch so you should remove the entry i suggested above

```

wget http://www.array.org/ubuntu/array-intrepid.list
sudo mv -v array-intrepid.list /etc/apt/sources.list.d/
wget http://www.array.org/ubuntu/array-apt-key.asc
sudo apt-key add array-apt-key.asc
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential

```

This should do it, sorry about taking the long way to get there.

OK - well it all went and seemed like it was going to work so I tried to run Virtualbox and it gave me the same error, so i ran the setup util and it did the following:

sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.

Then I ran:

VirtualBox

and got:

WARNING: The compilation of the vboxdrv.ko kernel module failed during the
         installation for some reason. Starting a VM will not be possible.
         Please consult the User Manual for build instructions.
No protocol specifaied
Qt WARNING: VirtualBox: cannot connect to X server :0.0


Any other ideas?   Oh and just in case I need to revert any of these changes after, is there any easy way to do so?

Update:  very weird.  I rebooted and tried to run VirtualBox again and it gave that same message and said Vms won't work but I'm installing win Xp on one as we speak!

Also, a lot of stuff change in my Gnome UI - is this because of the kernel changes?

I hope nothing is broken that I was using before :)

I'll keep you updated.

---

### Post by redilyn on 2009-01-14
Yes, I'm sorry I should have mentioned the following...

After enabling the eeebuntu repos you only wanted to install the kernel headers and build-essential.

It is possible that you now have elements of eeebuntu in your easypeasy distro.

This shouldn't break anything but as you already noticed it probably made changes to gnome.

I hope your virtual box works, I am out of here for the night but if you are still having problems I will try to assist tomorrow.

Cheers

P.S. Since you have the repos enabled now and you are using an eeepc I would suggest trying to eeepc lean kernel. It is faster then the default kernel. I am using it on my eeepc 900HA without issue.

---

### Post by bioshake on 2009-01-15
Well - its working now.  There are some minor issues with gnome now (ie: it boots and my sound is muted for example and when I restart it's not closing my smb shares down properly so i have to hold the power button in).

How can I go about trying the lean kernel?

---

### Post by redilyn on 2009-01-15
Hey,

I'm sorry I don't know how to resolve your gnome issues .... Maybe go into software sources -> third party and uncheck the eeepc entry. This should disable the eeepc repo.

Then try 

```

sudo apt-get update
sudo apt-get upgrade

```

That might replace the eeepc files with your easypeasy files though I can't say for sure.

To install the eeepc lean kernel do the following before disabling the eeepc repo.

```

sudo apt-get install linux-eeepc-lean 

```

More information about the lean kernel before you install it

> 
eeepc-lean

    Indicates only the bare-minimum EeePC-related configuration options are enabled. Most of the drivers normally compiled in as modules in the generic/eeepc kernels have been compiled in-line. This kernel typically responds faster and requires less boot-up time. 


---

### Post by bioshake on 2009-01-15
OK - sounds good.  By the way I got these messages during the download / install:

> 

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-8-eeepc-lean        
 *  vboxdrv (2.1.0)...                                                          vboxdrv (2.1.0): Installing module.
  Kernel source for 2.6.27-8-eeepc-lean not installed.  Cannot install this module.
                                                                         [fail]
 *  vboxnetflt (2.1.0)...                                                       vboxnetflt (2.1.0): Installing module.
  Kernel source for 2.6.27-8-eeepc-lean not installed.  Cannot install this module.
                                                                         [fail]





VirtualBox works right now.  But I haven't rebooted yet.  Going to do that and be back... I'll keep you posted.

Thanks again!

---

### Post by bioshake on 2009-01-15
OK - It's all working now - thanks again for all your help.

FYI:  The wifi toggle using eee-control is broken in the lean kernel so I had to use the stable version :D

---

