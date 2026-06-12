---
title: "Command to find windows partition"
date: 2009-06-10
forum: General Help
---

### Post by jmondo on 2009-06-10
Hello everyone,

I am working on an automated backup solution for some of my customers. I am currently using Jaunty combined with partimage to duplicate ntfs partitions, effectively backing them up.

Everything seems to be working well on my machine, but the problem I have run into is the need to figure out which partition windows runs from. On some computers, there is a restore partition that changes windows from /dev/sda1 to perhaps sda2. 

Since my customers don't understand how to use fdisk, I am looking for a way to automate the windows detection process. Perhaps this can be done by searching for the ntfs partition on the drive (since restore partitions are usually fat32), or searching for the boot partition, or finding media that includes a "Windows" folder, or something else?

Does anyone know of a command or a solution to this problem so that it would automatically output the /dev/sda? format into the partimage command where it asks for the partition?


Thanks in advance to all helpful suggestions and suggesters! LOVING Ubuntu, and even more so, the Ubuntu community!


Jmondo

---

### Post by unutbu on 2009-06-10
Install the os-prober package and run
```

sudo os-prober
```

---

### Post by jmondo on 2009-06-10
Thanks. I ran your command and this is what I got for output:

```
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows Vista (loader):Windows1:chain

```

First, it's too bad that the vista recovery looks exactly like actual vista OS partition. It makes this a lot less helpful.

But also, I'm looking for something that will automatically (or even via GUI), let the user choose which partition has windows on it. Then that choice would need to be saved somewhere so that it can be input into the partimage command.

Do you, or does anyone, know of something or a combination of tools that would allow me to piece this together? Somewhere to start may be that the partition I want will be marked as "boot"? I don't know. How does the Ubuntu installer figure out where Windows is?


Thanks.

Jmondo

---

### Post by unutbu on 2009-06-10
jmondo, looking at the boot flag is not a robust solution, though for many cases it could be helpful. 
If the machine is a multi-boot machine, only one partition should have the boot flag set, but the user could have multiple Windows OS's installed. I believe there is also a way to use GRUB to boot Windows partitions that do not have the boot flag set (by using the makeactive command). (GRUB can boot Windows installed on a logical partition, and logical partitions never have the boot flag...) Thus it is possible to miss Windows partitions if you rely on just the boot flag.

> 
I'm looking for something that will automatically (or even via GUI), let the user choose which partition has windows on it

You could rig something up in bash which uses the output of "sudo os-prober"
to create a command like this:
```

zenity --list --checklist --column "Backup" --column "Partition" TRUE /dev/sda1 TRUE /dev/sda2
```

If asking the user to make the decision is an acceptable solution, then the problem is not too hard.

On the other hand, if you want the script to determine which partitions are true Windows partitions then I don't know the answer for sure.

What happens when you mount /dev/sda1 and /dev/sda2:
```

sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
```

When you look inside /mnt/sda1 and /mnt/sda2, is there a noticeable difference?
Does one have a particular directory, and the other doesn't? If you can make up a rule to distinguish valid Windows installations from recovery partitions, then you could use that in a script.

Figuring out how the Ubuntu installer does it would be another alternative. Unfortunately I don't know how it does it.

---

### Post by jmondo on 2009-06-13
Hey thanks for all the helpful advice. For now, my friend created a script that checks whether a partition is marked as boot and it is formatted as ntfs. Based on what you said, this isn't going to be a very robust solution, but that's what I'm going with for now. 

Thanks for the help. Later on I'll experiment with the options presented in your advice.


Jmondo

---

