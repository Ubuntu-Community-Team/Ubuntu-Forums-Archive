---
title: "Can't &quot;Create New...&quot; in Konqueror in storage media hd"
date: 2005-06-21
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-06-21
Hi

I've got a laptop with Kubuntu. 

The problem is that I have two 2Gb HD that is pluggable. I have seen to it that fstab-sync mounts the removable media as rw. But still while in Konqueror i can't right-click with the mouse and choose "Create New". The option is greyed. At first I thought I missed something with Hal config but I can create folders and files in the Konsole and sometimes in Konqueror. If I choose to go directly to home and then direct my way to the removable media I seem to be able to choose the "Create New", but still never when I go directly thrue 'Storage Media (Media:/)'. This is a quite annoying thing since I want to know when I can be able to choose "Create New" or not.

Not sure why konqueror chooses to gray the option sometimes...maybe it is the "media:/" thingy that does something, but i haven't been able to find any file were to configure it.

Would appreciate the help...i've looked high and low for this but I haven't come across a suitable solution.

Thank you for your time

---

### Post by GoldBuggie on 2005-06-22
I also noticed today on my stationary computer that when i go thrue "storage media (media:/)" to get to my 2nd fat32 HD i can't write to it. But when I click on the icons that I have on desktop I get the option to do "Create New". Strange!!!!

---

### Post by tristian on 2005-06-22
Maybe you do not have permission to edit anything... mess with /etc/fstab and this might solve the problem (careful not to screw anything up and make a backup incase)

---

### Post by GoldBuggie on 2005-06-22
This is my fstab line for the stationary 2nd HD:
/dev/hdc1       /mnt/hdc        vfat    rw,users,exec,umask=000       0       0

But since I haven't managed to find a solution to the problem...found more peeps with the problem thou...I now think it is a KDE media:/ problem. For a good workaround to this I have used "Quick Browser" on the kicker and linked it to a directory where I have created "Links to Device". These links goes direcly to "/mnt/hdc" instead of "media:/hdc" and this works perfectly. I can now choose to create etc without any fuss. Not happy that I need to do a workaround thou...but it works great.

Thanks for the answer.

---

### Post by tristian on 2005-06-23
Ahh never mind I was going to write something but it seems a problem has been solved.

---

