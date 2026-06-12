---
title: "Bare Metal Backup Strategy"
date: 2006-09-13
forum: Desktop Environments
---

### Post by klepto on 2006-09-13
I've been searching this forum for great backup software
and before when I used gentoo I used mkstage4.sh which was a script that
was easy to backup and easy to restore, but programs like dar and others
won't be easy to restore if I lost my partition.

I'd like to know what programs you have used to backup and restore your
machines.

---

### Post by szf on 2006-09-13
I've just started with [Mondo Rescue]("http://www.mondorescue.org/").

Don't have a pro/con opinion yet.

---

### Post by klepto on 2006-09-14
Last night I test a few programs to see how well they worked.

I was impressed by rdiff-backup. 
Here is the command I used to backup my whole filesystem:
rdiff-backup -v 5 --exclude /sys --exclude /media --exclude /mnt --exclude /lost+found --exclude /proc --exclude /tmp / /media/sda1/KubuntuBackups/

and you can cp -aR /media/sda1/KubuntuBackups/ / and it retains all the permissions and symlinks, which means you can restore your harddrive from the kubuntu/ubuntu desktop cd. 

Ninjabackup also works well with rdiff-backup if you need some form of ncurses gui.

Mondo is good but I've had a few issues with it and dar/kdar is really slow.

---

