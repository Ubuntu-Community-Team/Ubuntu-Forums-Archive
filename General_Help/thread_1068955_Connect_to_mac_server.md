---
title: "Connect to mac server"
date: 2009-02-13
forum: General Help
---

### Post by gabetz08 on 2009-02-13
i was wondering if there is anyway to connect to a mac server. normally on a mac you would click "go" then "connect to server". I am on a college campus and i need to be able to porjects off the server from my room. on the mac computer you also need a username a password, i do not know if this effects anything or not. It would be an extreme help if any one could help. thanks in advance

---

### Post by gabetz08 on 2009-02-17
can anybody please help me.

---

### Post by DGortze380 on 2009-02-17
What type of server is it? 

Probably AFS or FTP ... if it's FTP you can connect by using the ftp command line utility, or click places, connect to server.

---

### Post by gabetz08 on 2009-02-17
> **DGortze380 said:**
> What type of server is it? 

Probably AFS or FTP ... if it's FTP you can connect by using the ftp command line utility, or click places, connect to server.

it is not ftp, i have tried to get on it from windows and it does not work, on the mac computer when you go connect to server, i type afp://server/, so what do i use for afp protocol

---

### Post by DGortze380 on 2009-02-17
> **gabetz08 said:**
> it is not ftp, i have tried to get on it from windows and it does not work, on the mac computer when you go connect to server, i type afp://server/, so what do i use for afp protocol

Do you have OS X Server installed?? 
I would enable FTP I suppose, (not the most secure solution).

EDIT: Looks like you need to start googling afpfs-ng
[http://ubuntuforums.org/showthread.php?t=301504](http://ubuntuforums.org/showthread.php?t=301504)

---

### Post by gabetz08 on 2009-02-17
> **DGortze380 said:**
> Do you have OS X Server installed?? 
I would enable FTP I suppose, (not the most secure solution).

EDIT: Looks like you need to start googling afpfs-ng
[http://ubuntuforums.org/showthread.php?t=301504](http://ubuntuforums.org/showthread.php?t=301504)

thanks for the advice about afps-ng, the problem is that it is not my server, it is a school server  that they have set up so students can save their projects to it

---

### Post by DGortze380 on 2009-02-17
> **gabetz08 said:**
> thanks for the advice about afps-ng, the problem is that it is not my server, it is a school server  that they have set up so students can save their projects to it

afps-ng is for YOUR  ubuntu machine if I understood that thread correctly.

---

### Post by gletob on 2009-02-17
I think your looking for afpfs-ng

[http://sourceforge.net/project/showfiles.php?group_id=179882&package_id=208206](http://sourceforge.net/project/showfiles.php?group_id=179882&package_id=208206)

There are no 64 bit binaries so I hope your on 32 bit

you would install that package and in a comand line run

sudo mount_afp afp://username:passwd@[SERVER IP HERE]/usernam /where/you/want/to/mount/at

For Example if your username was jack and password was jill and your servers ip was 10.0.0.53 then you would run

sudo mkdir /media/afpfs
# That's to make the directory to mount the files to.

sudo mount_afp afp://jack:jill@10.0.0.53/jack /media/afpfs
#To mount the network folder in the folder we just made

P.S. The folder that you mount the files to (the second one) doesn't have to have a specific name it just has to exist before you run the second command I gave you.

---

### Post by wirelessmonkey on 2009-02-18
I just verified this works on my work OS X server afp share, though I did have to compile afpfs-ng manually for my x86_64 bit system.

---

### Post by gabetz08 on 2009-02-18
thank you everyone for your help it works perfectly

---

### Post by balkce on 2010-10-20
I know I'm reviving a year-old thread, but this is the first hit I got when I googled "compile afpfs-ng", so I'm hoping people will get to this faster if I post my experience here.

afpf-ng is a wonderful piece of software that lets you connect to AFP shares, however it is only provided in 32-bits. so if you have a 64-bit arch installed, you'll need to compile it yourself. to do this go to synaptic and install the following packages (the names in parenthesis are the ones that i used in my 10.10 x64 install):

libgcrypt   and its -dev      (libgcrypt11, libgcrypt11)
libgmp      and its -dev      (libgmp3c2, libgmp3-dev)
readline    and its -dev      (readline-common, libreadline6, libreadline6-dev)
libfuse      and its -dev      (libfuse2, libfuse-dev)

download the afpfs-ng tarball and

```
tar -xzf afpfs-ng*
cd afpfs-ng*
./configure --prefix=/usr
sudo make install
```i used version 0.8.1 of afpfs-ng and with all the packages above installed, it compiled without any errors. notice the prefix argument in the configure command. this is necessary as, for some reason, the compiled commands look for their libraries in /usr/lib/

when that's done, test that there is a server running in the host or ip that you want to mount by running either one of these commands:

```
afpgetstatus 192.168.1.1
afpgetstatus TimeCapsule.local
```i recommend that your mount point be a folder inside your home directory, for permissions sake, as the uid isn't set well and you may not be able to browse inside your mount if you mount inside /media or /mnt. i created a "capsule" folder inside my home directory, and i'm able to browse my Data directory inside my time capsule without requiring anything else but the following line of code:

```
mount_afp afp://user:password@server_host_or_ip/Data ~/capsule

```to unmount do:

```
afp_client unmount ~/capsule
```no sudo is needed for neither of these commands.

hope this helps. cheers.

EDIT: i just noticed that afpcmd throws a buffer overflow. the rest of the commands run perfectly, though. i'll keep digging.

---

### Post by Zookalicious on 2010-10-28
I just wanted to say that this is one of the most useful posts I've seen in a while. Worked perfectly for me on both my machines. Thank you very much for the great tutorial!

---

### Post by Edelbo on 2011-02-27
Hi and thanks for the howto

I do however get the following error messag:

Mounting 127.0.0.1 from Data on /home/remmi/timecapsule
Volume Data does not exist on server remmi-laptop.
Choose from: Home Directory

But why?

---

### Post by JockeF on 2011-03-08
Big thank you Balkce! This is good stuff, saved me a lot of time.

---

