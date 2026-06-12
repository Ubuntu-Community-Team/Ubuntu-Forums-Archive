---
title: "jaunty extreme iowait"
date: 2009-06-09
forum: General Help
---

### Post by thebinaryblob on 2009-06-09
Periodically, my system-monitor applet will show either 50% (one core) or 100% (both cores) for iowait on the CPU. This causes extreme lag and makes the computer almost unusable until I kill the process.
I tried using iotop to monitor the process, but because I only notice it while I run other applications, the output moves too fast for me to keep track of. All I know is that something launches a find command and the user is 'nobody'.
Has anyone else had this problem? I would like to at least know what is thrashing my hardrive.

---

### Post by 123456789123456789123456 on 2009-06-09
I've never run into this problem with Ubuntu, have had very simular problems with windows machines, usually allways caused by Viruses/mileware infections.  Though Ubuntu is extreamly secure, it could be possible that some sort of virus has infected the machine.  To determine disk thrashing, do you notice the hard drive working extreamly hard, for instance, the hard drive indicator led go and stay on for extream time limits, for instance 30 min or more., or does the light blink, but continually without non activity for a long period of time, longer than usual.  You can also check under system monitor, for the disk section, IO requests to the hard disk, mainly read/write.
When have you noticed that the find command is activated?
is it random, or when a certian program/programs are accessed?
the user nobody is a system process
the system that I have noticed uses 5 non existant users, nobody is one of them, I can't remember exactly what type of system process this refers to being used though.  the only real user for system processes is root.

---

### Post by thebinaryblob on 2009-06-09
nobody is the user for anonymous network access and anything else that should not write to any filesystem, but that does not stop it from scanning the entire contents of my hardrive and using all of the CPU.

looks like i'll just have to wait until it starts again, and take a screenshot of a maximized terminal to find out exactly what its arguments were

---

