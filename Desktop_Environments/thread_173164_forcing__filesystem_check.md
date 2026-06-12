---
title: "forcing  filesystem check"
date: 2006-05-09
forum: Desktop Environments
---

### Post by seatea on 2006-05-09
I had a system freeze today that I could not get out of without doing a reset on my computer. I was trying to use kbdrate to adjust the repeat of my  keyboard keys. I seem to be getting a lot of double spaces when typing and was trying to cut down on this occurrence. I won't do that one again. Anyway- after hitting  reset, my computer rebooted, but the  system did not run fsck. I thought the system would run it anytime the computer was not shut down properly.  What I did was to boot into the Live CD and run fsck which reported everything as "clear". I keep expecting more information about what it is checking when it runs plus  it runs so fast I keep wondering if it did anything at all. There must be a simpler way. I read in a post to create a file: "sudo touch /forcefsck" and that would cause fsck to run after a restart. What I keep wondering about with this recommendation is how will this be carried out without already having mounted the filesystem which would seem to make it run fsck on  a mounted volume. I am guessing that my thinking on this is wrong, so how would this result in fsck being run only when the  filesystem is not mounted?

---

### Post by ubuntu_demon on 2006-05-10
you can change the repeat speed here : system->preferences->keyboard
I don't understand your question. Does this help ? :

$ sudo touch /forcefsck
If you reboot after that. Then the filesystem will be checked during the bootproces. You will see that it is being checked.

---

### Post by Ramses de Norre on 2006-05-10
Ubuntu checks the filesystems before mouting them, it checks the mountrate (for automated fsck) and whether there is a forcefsck or fastboot file, then it runs fsck when needed and mounts it after that. Check your boot messages, you'll see;)

You can also shutdown with ```
sudo shutdown -hF now
sudo shutdown -hf now
```
The first one will force fsck (make a forcefsck file), the second will skip any automated fsck (make a fastboot file).

---

### Post by seatea on 2006-05-10
Thanks. I didn't describe  what I was trying to change  very well. I have noticed when  typing in ubuntu that  I  get a lot of double spaces between words. I think this may be  due to an overly sensitive space bar and not to an excessive  repeat rate as I was originally thinking since  it doesn't happen with the other  keys. I thought  for a while too that I had been hitting the  space  bar twice inadvertently, but even when I tried to be  more careful, it seems to still happen a lot. I had made adjustments in  the keyboard preferences to the delay time and repeat rate, but that didn't have any impact on the occurrence of the spacing problem. I  think I will try to turn off "Repeat Keys" for a while. If that  doesn't help either, I'll just live with it.

---

### Post by seatea on 2006-05-10
[QUOTE=Ramses de Norre]Ubuntu checks the filesystems before mouting them, it checks the mountrate (for automated fsck) and whether there is a forcefsck or fastboot file, then it runs fsck when needed and mounts it after that. Check your boot messages, you'll see;)

You can also shutdown with ```
sudo shutdown -hF now
sudo shutdown -hf now
```
The first one will force fsck (make a forcefsck file), the second will skip any automated fsck (make a fastboot file).[/QUOTE]

Thanks. That is what I was looking for. If  I want to reboot and  run  fsck, I could type "sudo shutdown -rF", right?

I am a little paranoid about running fsck on a mounted system after reading comments about the potential to damage the filesystem by doing that. What is odd  is that in the book  *Running Linux*, fsck is run on  a mounted filesystem. The author goes on to say that it's not a good idea to run fsck on a mounted filesystem, but he doesn't really say that it might cause damage to the filesystem or why it is not a good idea. He does point out that if any errors are found and corrected with fsck while it is mounted, the system will have to be rebooted to propagate the changes to the internal knowledge of the filesystem layout.

About the boot mounting of the filesystem, I was unclear  on the  mounting process. The boot loader scans all the files at the  root level such  as bin, var, usr, ... then mounts the  filesystem? I was thinking that in  order to read any information, the whole filesystem had to be mounted which led to my concern that a forcefsck file at root level would have to be mounted before it was interpreted. I have to confess that I looked  through the syslogs and could  not tell what was going on. I haven't been able  to wrap my mind around what is sequencing at  startup despite my efforts. I am starting to think I  am a little slooow.

---

### Post by Ramses de Norre on 2006-05-10
In your boot messages you'll see 'checking root file system' and that's where it may find a forcefsck file and start fsck, after the checking message you'll see 'mounting root file system'.
The same happens for 'all file systems' a bit later.

---

### Post by seatea on 2006-05-10
[QUOTE=Ramses de Norre]In your boot messages you'll see 'checking root file system' and that's where it may find a forcefsck file and start fsck, after the checking message you'll see 'mounting root file system'.
The same happens for 'all file systems' a bit later.[/QUOTE]


I checked all the logs available in the System Log Viewer for gnome(Applications>System Tools>System Log) and there is nothing in there about checking the file system. I looked in /var/log, but I did not see a  boot log file or folder. Where are the boot messages stored?

---

### Post by seatea on 2006-05-10
I think  I  know now  why I have not been able to find the messages about the  filesystem being mounted or checked. From what I can determine, there is no boot log on my computer at the present. I did a google seach and, by default on debian systems, boot logs are not enabled. I did change the /etc/default/bootlogd file to start keeping boot logs.

---

### Post by ubuntu_demon on 2006-05-11
You don't need to change anything. You can see the boot messages by typing : 
$dmesg

the file is :
$/var/log/dmesg

---

### Post by Ramses de Norre on 2006-05-11
The messages I mean aren't in my dmesg, I mean the ones appearing under the splash image. You can see them through ctrl-alt-F8.

---

### Post by seatea on 2006-05-11
[QUOTE=Ramses de Norre]The messages I mean aren't in my dmesg, I mean the ones appearing under the splash image. You can see them through ctrl-alt-F8.[/QUOTE]

I am using ubuntu ppc and have an Apple keyboard. I am not sure all the typical keyboard commands work on my system. If I try ctrl+option(the Apple eqivalent to alt)+F, nothing happens. I can get to console mode with ctl+opt+F7.

---

