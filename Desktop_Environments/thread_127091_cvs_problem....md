---
title: "cvs problem..."
date: 2006-02-08
forum: Desktop Environments
---

### Post by buildid on 2006-02-08
"can't create temporary directory /tmp/cvs-serv22979
No space left on device
can't create temporary directory /tmp/cvs-serv23034         
No space left on device
can't create temporary directory /tmp/cvs-serv23115         
No space left on device"

iam getting these messages , but i have soace enough on my HDD so i wonder what problem i have, cannot figure it out , any help is welkom..

---

### Post by marsian on 2006-02-08
your HDD has certainly enough space, but what about the partition dedicated to /tmp ?
You could type:
df -H 
to know the available space  for /tmp (1st column gives you the partition name and last one gives you the mounting point)

---

### Post by buildid on 2006-02-08
Here is my output:

buildid@Breezy:~$ df -H 
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2              134G    61G    67G  48% /
tmpfs                  265M      0   265M   0% /dev/shm
tmpfs                  265M    13M   252M   5% /lib/modules/2.6.12-10-386/volatle
/dev/sda1               21G    14G   7,2G  66% /media/0 GB Disk (sda1)

Hope you can help me out ......

---

### Post by GTvulse on 2006-02-08
[QUOTE=buildid]"can't create temporary directory /tmp/cvs-serv22979
No space left on device
can't create temporary directory /tmp/cvs-serv23034         
No space left on device
can't create temporary directory /tmp/cvs-serv23115         
No space left on device"

iam getting these messages , but i have soace enough on my HDD so i wonder what problem i have, cannot figure it out , any help is welkom..[/QUOTE]
The messages you see are sent by the server, running out of temporary scratch space. That's a remote server you are using, right? Contact the administrator or wait paitiently until the problem is sorted out.

---

### Post by buildid on 2006-02-08
thats right, thank you for your answer..........

---

