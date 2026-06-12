---
title: "Issues with KDE/root user"
date: 2005-05-15
forum: Desktop Environments
---

### Post by Phoenix590 on 2005-05-15
This problem has plagued me since I installed kubuntu (I think I may just reinstall it as Ubuntu then use apt grab). MY system is a dual boot and I have 2 NTFS partitions on my harddrive I would like to access with Kubuntu. I can mount them every time I start up by doing a sudo mount /dev/hda1 /media/windows/ ...., and it works, but when I got tired of telling it to mount the drives everytime it started I read up and found if I modified FSTAB, (when i do a sudo mount it writes to mtab) it would mount everytime I boot, but I found only the root user could modify it. Since I am running Kubuntu, kate wont run from konsole, so I have to get on root user via KDE login, but sadly KDE wont let me login as root. Is there anyway around this? I think I also need to be on KDE as root user in order to install NDISWRAPPER. Any comments appreciated. Thanks,
                                          Phoenix.

---

### Post by Hokputooy on 2005-05-15
If you want to run a program with root you can type:
kdesu <progam>

---

### Post by Phoenix590 on 2005-05-15
although that helped alot, another question, when adding drives for mounting in fstab do you press tab between each column, because i notcied unlike the drives kubuntu has already put in FSTAB, when i add mine theres a . after the end of each column and it doesnt want to work right(gives me the error that: [mntent]: warning: no final newline at the end of /etc/fstab) and displays nothing when I mount the drives and gives me the error: the process for the media protocol died unexpectantly (im sure there should be files in there). Thanks,
                                              Phoenix

---

### Post by DerekInGermany on 2005-05-15
No you must not use the tab, a space is fine. And there must be a blank line at the botton of the file.  Just hit enter at the end of the last line.  This is what my fstab file has for my ntfs partition:

/dev/hda1       /windowsc       ntfs    auto,users,exec,ro,umask=000,uid=derek,gid=users 0 0

I hope this helps a little

Derek

---

### Post by Wrenchman9 on 2005-05-15
You can right click on fstab in Konqueror and go down to actions and then choose Edit as root. Put your user password in at the prompt and you're in.

---

