---
title: "Unsolved Dependencies"
date: 2005-11-09
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-09
I was trying to install K3b. I cant do it. The message says that some things need to be uninstalled and that there are unresolved dependencies. I guess the question is how do I solve the dependencies? 
    My theory would be to try to google for a repository that has them and add that.
    Please go easy on me I am a newbie.

Thanks
Charlie

---

### Post by Pablo_Escobar on 2005-11-09
Please, post Your > /etc/apt/sources.list file contents so we can troubleshoot :)

---

### Post by Miguel on 2005-11-09
Hi Charlie,

Could you tell us what packages does k3b need that are not installed? Also, the output you get when you type in a terminal
```

$ sudo apt-get install k3b

```

Also, it would help if you told us what repositories you are using.

EDIT: Heck, Pablo beat me

---

### Post by CharlieC on 2005-11-09
Thanks for the reply:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


cc@linuxfour:~$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: k3blibs (>= 0.11.23) but it is not going to be installed
       Depends: kdelibs4 (>= 4:3.4.0) but it is not going to be installed
       Depends: kdebase-bin but it is not going to be installed
       Depends: kcontrol but it is not going to be installed
E: Broken packages
cc@linuxfour:~$

    Any help would be appreciated.

Thanks again

Charlie

---

### Post by Pablo_Escobar on 2005-11-09
If You're on Hoary You sources.list look OK.
Try this:
> sudo apt-get -f install - cleaning the dep problems

Secondly, I'd comment out Backports (it helps sometimes, trust me)

---

### Post by Who on 2005-11-09
Hi,
We need to know how you are trying to install K3B - because if you are using Synaptic then it should solve the dependency problems for you automagically, providing of course they are all present on your current repository...
So - one possible solution is to use Synaptic in System-->Administration, if you are not already doing this (If you are not then I should add that this is pretty much the main way to add software packages to a Ubuntu system, excepting the command line).

If you are already doing that, then you can use Synaptic to add a mirror:
Start Synaptic. Go to Settings Menu, choose Repositories option and then click 'Add Repositories'. I tend to have all the binary ones possible; so security, updates, base in universe, multiverse and the other option (I am not on my Ubuntu PC now - sorry). I would be very surprised, though, if the dependencies needed for K3B were not part of the standard set of packages (I.E the ones that aren't Multiverse or Universe, and are 'officiall supported').

The other option to you, if you feel like feeling like more of a pro :P, is to manually edit a (text) file at  /etc/apt/sources.list. In order to do this I would yuse the following two commands.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_BACKUP
sudo gedit /etc/apt/sources.list 

Sudo means 'make me an administrator for the following commands', cp means copy [source file] to [new file] - so the first line backs up the file before you do any editing. Gedit is a nice little text editor like notepad.
Now you can change the settings in that file. You should just need to 'uncomment' some lines by removing the hashes from in front of them. The file itself has quite a lot of info in it about what to do in it that I needent talk about here unless you get stuck (if you even choose this method!).

Good luck!

Who

Looks like others got there first - aren't people helpful :P

---

### Post by CharlieC on 2005-11-09
Thank you very much for your help. I did have a repository problem so I checked all the boxes you suggested and it added a bunch of stuff. K3b got installed and I had a bunch more updates to apply.
    This problem was 100 percent self inflicted. I was trying to install libdcdcss2, it seemed not to be on the Ubuntu sites so I went to the unofficial documentation page and updated my repositories based on the instructions. I think that caused the problems. I'm new to this and very error prone.
    Is it possible to download debian repositories and install stuff in Ubuntu, which is supposed to be based on debian.

Thanks again for the help.

Charlie

---

### Post by Pablo_Escobar on 2005-11-09
Some packages from Debian can be installed and seem to be working. Some don't. By using then You may get serious package problems so it's not recommended.

---

