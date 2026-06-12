---
title: "installed kubuntu, need help accessing disks?"
date: 2005-07-06
forum: Desktop Environments
---

### Post by disgust on 2005-07-06
again, this is also related to vmware. I'm running kubuntu in windows via vmware. I'm not sure how to access my disks- I'm also not sure if this is a problem that's just arising from my unfamiliarity w/ linux, or due to complications with vmware. 

any things I should try to access them?

---

### Post by Sye d'Burns on 2005-07-06
First things first, you'll have to make those partitions available to the virtual machine. 

Pick the machine from your favorites list. Then click 'Edit virtual machine settings'. 

Add -> Hard Disk -> Use a physical disk -> ...

... Here is where you decide to add the entire drive, or just partitions...

Once you've made your choice of which partition to allow kubuntu to see you'll want to edit your fstab... check out [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by disgust on 2005-07-06
thanks, that worked

I've noticed that mp3s tend to skip- is this just a result of running kubuntu under vmware?

---

### Post by Sye d'Burns on 2005-07-06
[QUOTE=disgust]thanks, that worked

I've noticed that mp3s tend to skip- is this just a result of running kubuntu under vmware?[/QUOTE]
 I'm not sure... I run windows 2000 under vmware and I haven't had more than the rare skip.

 If you're hosting from windows it's possible that resources are being chugged by the host running apps (antivirus and firewall particularly).  I have noticed a huuuge speed difference in running vmware from windows xp pro and running vmware from ubuntu or slackware. 

The reason that I'm not sure, however, is that I have seen a few posts complaining about skipping mp3s... It merits looking into further.

---

