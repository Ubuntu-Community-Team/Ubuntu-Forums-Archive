---
title: "Getting Low Disk Space Warning after Installation"
date: 2006-09-16
forum: Desktop Environments
---

### Post by saigalp on 2006-09-16
I installed ubuntu 6.06 today on my system in dual boot with Windows XP. I am getting low disk space warning right after I updated ubuntu. Although at the time of installation I had provided 18 GB space using the 1st option. I am enclosing herewith the screenshot of fdisk -l command output. Please tellme how to create more space for ubuntu. I am a new user and a detailed

---

### Post by lukew on 2006-09-16
Can you do 

$ df -h

This will show you the disk usage in a more clear form.

I suspect if you provided 18gb of space for this parition which is raising the message then you were either mistaken by the error message or you installed onto the wrong partition.

Luke

---

### Post by lamego on 2006-09-16
You can also install the program "baobab" which will give a graphical represenation of the disk usage.

---

