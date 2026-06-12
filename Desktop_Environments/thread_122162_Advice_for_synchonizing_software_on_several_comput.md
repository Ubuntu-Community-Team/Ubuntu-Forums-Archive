---
title: "Advice for synchonizing software on several computers/laptop"
date: 2006-01-26
forum: Desktop Environments
---

### Post by jasonwjones on 2006-01-26
Not quite sure what forum this should go in... but I have a laptop and my main computer both running Ubuntu.  For the most part I have the two installed with the same software... but I spend more time on my desktop and sometimes neglect the lappy so that when I get on it, sometimes I'm lacking some of the software and tweaks that I've made to make the desktop more comfortable.  Does anyone know of another approach I could take to keep the two synchronized other than just installing everything twice? Thanks for any suggestions!

---

### Post by SuperMike on 2006-01-26
Tough question.

Well, this is similar to my clone question I posted a few days ago. In that, I found that the latest Symantec Ghost will clone Ubuntu's EXT3 filesystem. I also found that if you get a base, minimal Ubuntu going on a separate PC, you can combine netcat (nc command) and/or scp, as well as dd, in such a way to create an image, transfer it fast, and install it on top of another system. Someone also told me that g4u is a program that does the nc/dd function to clone a system.

Although cloning is not what you're asking, I believe you can use the scp/dd or nc/dd technique on an /etc/crontab schedule to transfer changes. The problem is writing a Bash script that determines what the differences are between the two systems, or that some daemon Bash script sits in memory and tracks each time you make a change to a particular file type like *.conf and keeps a log of it so that it can replicate those changes to the other system.

In addition to investigating what I suggest above, there might already be something written. I would also suggest that you do keywords searches with Google against the sites freshmeat.net or sourceforge.net, as in:

site:freshmeat.net replicate files
site:freshmeat.net synchronize files

---

### Post by slux on 2006-01-27
If all you're after are package selections. try:
```

host1# dpkg --get-selections > selections
( copy the file selections to target machine)
host2# dpkg --set-selections < selections && apt-get dselect-upgrade

```

If you're also thinking of your home dir settings, files and everything the nicest choice would be a distributed (network) filesystem that can support synchronisation, something like afs, but a simple rsyncing will go a long way...

---

