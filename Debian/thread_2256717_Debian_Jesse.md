---
title: "Debian Jesse"
date: 2014-12-14
forum: Debian
---

### Post by d-cosner on 2014-12-14
I like Gnome Shell as my desktop environment and of course I wanted the current 3.14 version because I like the refinements that have been made. I installed Jesse some time ago but started having problems with the root partition filling up, or so I thought anyway. The system kept freezing up too and became unusable. I just happened to come across a thread on these forums where someone else was having the same problem with their drive filling up. It turned out to be a problem with LVM giving false information.

I had used LVM on my original install of Jesse and decided to re-install with ext4 and the default partitioning, this seems to have solved the problem. Regular updates seem to have fixed the remaining problems with the system freezing for the most part. In 3 days of regular use the system has only froze up once after using the "apt-get clean" command. I have since used the command a couple of times with no problems.

Jesse seems to be running fine now. Memory use has improved with updates and for being under development it has been doing well for daily use now. I originally used LVM and had a separate Home partition. Has anyone else had problems using LVM? I have seen updated versions of LVM but they have not made it into the repos just yet. I wonder if the freezing could have possibly been caused because the system thought the root partition was almost full? I never had a problem with using LVM before and was just trying to figure out what went wrong with my original install.

---

