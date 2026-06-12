---
title: "unable to run own generated executables"
date: 2006-09-30
forum: Desktop Environments
---

### Post by hecato on 2006-09-30
Hi there, I dont know if this is a strange problem, Im out of space in the partition that I select for mount point **/home**, then I decided to move the major directory in my user **/home/hecato** (checked with Filelight) and this was **Programs**, inside this one I have some source codes of mine and other projects from some CVS's that I compile with gcc, g++, make et all. I decide to move the contents of **Programs** to **/mnt/hda8/Programs** and that worked fine however when I compile something there, I cannot runnit, I do a simple programm and compiled on command line and when runned it say some like

```

hecato@hecatombe-64:/mnt/hda8/Programs$ vi x.c
hecato@hecatombe-64:/mnt/hda8/Programs$ gcc x.c
hecato@hecatombe-64:/mnt/hda8/Programs$ ./a.out
bash: ./a.out: Access denied
hecato@hecatombe-64:/mnt/hda8/Programs$ cd ~
hecato@hecatombe-64:~$cp /mnt/hda8/Programs/a.out a.out
hecato@hecatombe-64:~$ ./a.out
hecato@hecatombe-64:~$

```Like you see I can **read**/**write** to the path, even run gcc and the a.out writed there, but Im **not able** to run my programm, if I copy it to a subfolder  of **/home/hecato** then Im able to runnit like the anterior example.




In fact, for example I have a source code from a CVS, and in the instructions say that is needed to run **./bootstrap** before doing **./configure** and it run well under **/home/hecato**, but in /**mnt/hda8/Programs**


```

hecato@hecatombe-64:/mnt/hda8/Proyectos/fromCVS/$ ./bootstrap
bash: ./bootstrap: /bin/sh: incorrect intrepret: Access denied
hecato@hecatombe-64:/mnt/hda8/Proyectos/fromCVS/$ sh bootstrap
hecato@hecatombe-64:/mnt/hda8/Proyectos/fromCVS/$

```First line dosent run OK, second line run OK.
```

hecato@hecatombe-64:/mnt/hda8/Proyectos/fromCVS/$ ./bootstrap
bash: ./bootstrap: /bin/sh: incorrect intrepret: Access denied
hecato@hecatombe-64:/mnt/hda8/Proyectos/fromCVS/$ sh bootstrap

```the first line dosent work, the second run, but configure catch that Im not able to run programs there :S... here is the ouput
> 
hecato@hecatombe-64:/mnt/hda8/Proyectos/reps/_CVS/ogrenew$ sh configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: [COLOR=Red]error[/COLOR]: **cannot run C compiled programs**.
If you meant to cross compile, use `--host'.
See `config.log' for more details.


Like you guess if I move the "fromCVS" folder inside a subfolder of /home/hecato, then doing the anterior run just fine without complain about something wrong.

See that I dont whant to cross compile, is a single build, even Im unnable to run the simples c program (the one I say at start)
```

int main(){return 0;}

```But copying the ./a.out file from **/mnt/hda8/programms** folder to a subfolder of **/home/hecato** work just fine.





By the way, programms maked and runed via mono run in **/mnt/hda8/Programms** and under **/home/hecato** without problems or complains... tought I know that mono != than C,C++,./bootstrap et all... dont know if that mean something for you.

---

### Post by hecato on 2006-10-01
Or at less say me if the bahaviour also happend tou you... if you have a partition mounted in /mnt called for example **hda4** and is not the /home mount point, then...


do then next

```

$ mkdir /mnt/hda4/simpletest
$ cd /mnt/hda4/simpletest
$ vi x.c

```

In x.c put (press "i" for enable input press ESCAPE for enable commands)
```

int main(){return 0;}

```
and ESCAPE to commands and enter 
```

:wq

```
For write and quit
```

$ gcc x.c
$ ./a.out

```

and say me if running ./a.out outside your home folder cause troubles to you, in that way I will know that something is wrong with my settings or some like that... or know that is a security thing not being able to run programs even that you are the owner and that you can run the same programm under the home folder of your user.

---

### Post by ebash on 2006-10-01
Could it be that the partition /mnt/hda8 is mounted without execute rights?

If you take a look at the man page of the command mount you can see that there's an option called noexec which will forbid you to execute binaries found under a specific mount point.

Can you show us the results of the command mount, you should see the options used for each mount point?

---

### Post by hecato on 2006-10-01
```

~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
#,umask=777 en opciones
# <file system> <mount point>   <type>      <options>              <dump>  <pass>
proc            /proc           proc        defaults               0       0
/dev/hda7       /               reiserfs    notail                 0       1
/dev/hda6       /home           reiserfs    defaults               0       2
/dev/hda5       none            swap        sw                    0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto           0       0

#,umask=0222
/dev/hda3       /mnt/hda3    reiserfs    defaults,user     0       2


/dev/hda8       /mnt/hda8    auto    defaults,user     0       2

```In fact is partition 8, it use reiserfs also.


and mount...
```

:~$ mount
/dev/hda7 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-amd64-generic/volatile type tmpfs (rw)
/dev/hda6 on /home type reiserfs (rw)
/dev/hda3 on /mnt/hda3 type reiserfs (rw,noexec,nosuid,nodev)
/dev/hda8 on /mnt/hda8 type reiserfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

I see the **noexec** there, thanks for the help, I guess I need to add **user,defaults,exec** for this to work.

---

