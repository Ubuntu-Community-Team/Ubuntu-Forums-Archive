---
title: "&quot;my comuter&quot; folder appearance"
date: 2006-05-05
forum: Desktop Environments
---

### Post by october1917 on 2006-05-05
Hello

While i was installing Ubuntu, i had disconect the one of my 2 hard disks, in order not to destroy its data. So i mounted it ti the /mnt/files archive tha i created.

The problem is that when i go to Places-->My Computer there appear only 
1) floppy
2) cd rom
3) dvd r
4) file system (which is the one hd - the bootable one)

How can i add a new icon for the other disk -the mounted one?

And something more: what is the adress for "my computer"? For example, to go to home folder from console, i write "cd /home/username". What have to write to go to "my computer"?

Yhank you.

---

### Post by Cirrocco on 2006-05-05
Hard drives I want to show up in 'my computer' I mount in /media/

---

### Post by Ramses de Norre on 2006-05-05
The address is ```
computer:///
```

---

### Post by october1917 on 2006-05-07
You mean that if i mount the disk into /media it will automaticaly appear in "my computer folder"?

---

### Post by october1917 on 2006-05-07
Yeah, it works just right you said.
It created an icon in "my computer" but it created aslo an icon in Desktop. How can i desappear it?

[QUOTE=Ramses de Norre]the adress is > computer:///[/QUOTE]This is the adress of the master file system. Not of "my computer" folder. Do you know it? It seems that it will never use it as i did what i wanted to, but anyway...

Thank you.

---

### Post by Ramses de Norre on 2006-05-07
```
gconf-editor /apps/nautilus/desktop
``` uncheck "volumes_visible"

---

### Post by october1917 on 2006-05-26
I've installed the 6.06 Dapeer version.
There is a similar problem. In the "my computer" folder appear the following:

floppy
CD drive
DVD drive
Deposit (this is a second hard disk mounted by me)
File System (this is the boot hard disk)

and another one which is called 
17,9GB Root Volume (which is the same with "File System".)

Why?
Also, how can i rename the hard disks?

---

### Post by bicchi on 2006-05-29
[QUOTE=october1917]I've installed the 6.06 Dapeer version.
There is a similar problem. In the "my computer" folder appear the following:

floppy
CD drive
DVD drive
Deposit (this is a second hard disk mounted by me)
File System (this is the boot hard disk)

and another one which is called 
17,9GB Root Volume (which is the same with "File System".)

Why?
Also, how can i rename the hard disks?[/QUOTE]

I am having the same issue in Dapper since I upgraded. I am starting to think that this is a bug since I also show an icon with the name "tml<" which links to my windows partition that I have automounted in my /etc/fstab

As far as the "tml<" icon, I can not rename it. The problem could be with HAL and the name it assigned to it. In my case I didn't put a label on the hard drive of my windows partition so HAL could have randomly generated the name "tml<".

I have filled a bug in malone and if you are experiencing the same issues go there and add comments to it.[URL="https://launchpad.net/distros/ubuntu/+bug/47349"]
https://launchpad.net/distros/ubuntu/+bug/47349[/URL]

---

