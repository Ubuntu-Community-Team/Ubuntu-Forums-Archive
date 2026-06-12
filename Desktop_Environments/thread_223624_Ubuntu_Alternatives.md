---
title: "Ubuntu Alternatives"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Mr_ on 2006-07-26
I wasn't sure where to put this thread, sorry admins if you have to move it.

Seens as in my previous [post]("http://www.ubuntuforums.org/showthread.php?t=222131") I couldn't come up with a solution, I'm going to as some suggested try a few other linux distubutions to see if I have any problems with them. So far I've shortlisted it down to fedora and knoppix. Any other suggestions?

Also in another last ditch effort to get ubuntu installed is it possible to install debian and then upgrade to ubuntu ? I only ask as i'm new to linux and it popped up in my mind so ....


thanks

---

### Post by tzulberti on 2006-07-26
I think that if you install a basic debian, you could use the ubuntu repos. Nevertheless, you should try debian...

---

### Post by PilotJLR on 2006-07-26
I'd recommend checking out Fedora Core 5... it's a solid distribution, and is more user friendly than most people think.

---

### Post by cptnapalm on 2006-07-26
One nice thing about Debian is that you can burn a minimal system, boot off of that, and do a net-install.  Back when I ran Debian, that was my preferred method of install.

---

### Post by daniel of sarnia on 2006-07-26
SUSE SLED 10 is nice.

---

### Post by aysiu on 2006-07-26
Try this:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by Mr_ on 2006-07-27
> **tzulberti said:**
> I think that if you install a basic debian, you could use the ubuntu repos. Nevertheless, you should try debian...


Anychance someone could elaborate on what an ubuntu repos is and how I go about getting/installing it after I install debian please?

thanks for the ereplies

---

### Post by kikinovak on 2006-07-27
If you want to learn about Linux, use Slackware ([http://www.slackware.com)](http://www.slackware.com)). Docs: [http://www.slackbasics.org](http://www.slackbasics.org).

Then (after a few months), dig LFS ([http://www.linuxfromscratch.org)](http://www.linuxfromscratch.org)).

Then take a long holiday, and use Ubuntu :D 

Enjoy.

---

### Post by tturrisi on 2006-07-27
> **Mr_ said:**
> Anychance someone could elaborate on what an ubuntu repos is and how I go about getting/installing it after I install debian please?

thanks for the ereplies
If going to build up from a debian install then best to just use the debian repositories, not ubuntu repositories.  There could be conflicts or dependency issues when using the ubuntu repositories because ubuntu is not pure debian.

---

### Post by igul222 on 2006-07-27
[FONT="Arial"]but if you're going to anyway...

1. Install Debian, get it working.
2. Uninstall just about everything that the system doesn't need (you can reinstall later)
3. Go to this website, and download the file to your home directory:
   [http://www.sendmefile.com/00442158](http://www.sendmefile.com/00442158)
3. open up Terminal, (or Konsole, depending on what window manager Debian uses)
4. type in:
cd ~
sudo mv ~/sources.txt /etc/apt/sources.txt
sudo rm /etc/apt/sources.list
sudo mv /etc/apt/sources.txt /etc/apt/sources.list
sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get -y upgrade
sudo apt-get -y -f install
sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get -y upgrade
sudo apt-get -y -f install

(YES, i know i typed the last 4 lines twice, not a typo!)

5. Reboot, and you're done!

---

