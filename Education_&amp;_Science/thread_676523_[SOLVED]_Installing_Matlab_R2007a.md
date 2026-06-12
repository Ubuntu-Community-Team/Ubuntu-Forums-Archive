---
title: "[SOLVED] Installing Matlab R2007a"
date: 2008-01-23
forum: Education &amp; Science
---

### Post by QED314159 on 2008-01-23
I need help installing Matlab r2007a student version on Ubuntu 7.10. When I try to run the installation DVD I get:

unable to execute /cdrom/install_unix.sh: Permission denied

Also I have read about several other problems involved with installing matlab. Any advice or experiences to make this good smoother would be very welcomed. 

Thanks.

---

### Post by amd-64 on 2008-01-24
Do you run it as root. in r2007b, the command is install not install_unix.sh

In a terminal, try

sudo /cdrom/install_unix.sh

---

### Post by QED314159 on 2008-01-24
I did run the command using sudo however i get the same reply of permission denied.

---

### Post by kbless7 on 2008-01-24
I'm not too sure about that. I did mine from an iso file. From looking at my iso file the installer isn't a shell script so you wouldn't need the ".sh" part. Is yours a script?

-Matt

---

### Post by QED314159 on 2008-01-24
I'm not sure. There is a file on the dvd named install_unix.sh However I can't this to run even as root.

---

### Post by kbless7 on 2008-01-24
> **QED314159 said:**
> I'm not sure. There is a file on the dvd named install_unix.sh However I can't this to run even as root.

Try 

```
sh /cdrom/install_unix.sh
```

Thats how you run scripts

---

### Post by QED314159 on 2008-01-25
I tried this:
root@sinx:~# sh /cdrom/install_unix.sh

and got:
exec: 4: /cdrom/unix/install: Permission denied

---

### Post by kbless7 on 2008-01-25
> **QED314159 said:**
> I tried this:
root@sinx:~# sh /cdrom/install_unix.sh

and got:
exec: 4: /cdrom/unix/install: Permission denied

Does it do the same thing when your not running in root? If that doesn't work try extracting it as an iso and mounting it. Then you should be able to do it then.

---

### Post by QED314159 on 2008-01-25
I get the same result using sudo. What do i need to do to extract it as an iso and mount?

---

### Post by kbless7 on 2008-01-25
> **QED314159 said:**
> I get the same result using sudo. What do i need to do to extract it as an iso and mount?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_create_Image_.28ISO.29_files_from_CD.2FDVD](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_create_Image_.28ISO.29_files_from_CD.2FDVD)

Go to that website. There is a section thats says how to create an iso image from cd/dvd. The website also tells you how to mount the iso

---

### Post by sfabel on 2008-01-25
It helped actually using the bash shell when I had that problem. Instead of 'sh', make sure that it is 'bash' ('sh' somtimes is a link to a stripped down version of the shell).

YMMV

Stephan

---

### Post by QED314159 on 2008-01-25
Thank you kbless7 creating an iso and going from there worked perfectly. I have included the code below for anyone else who may encounter this problem.
```

:~$ sudo umount /dev/cdrom
:~$ readcd dev=/dev/cdrom f=file.iso

Read  speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Write speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Capacity: 638960 Blocks = 1277920 kBytes = 1247 MBytes = 1308 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file 'file.iso'
end:    638960
addr:   638960 cnt: 48
Time total: 298.845sec
Read 1277920.00 kB at 4276.2 kB/sec.

:~$ sudo mkdir /media/iso
:~$ sudo modprobe loop
:~$ sudo mount -t iso9660 -o loop file.iso /media/iso
:~$ cd /usr/local
:/usr/local$ sudo mkdir matlab74_sv
:/usr/local$ cd matlab74_sv
:/usr/local/matlab74_sv$ sudo /media/iso/install_unix.sh

```

After the installation is complete
```

:~$sudo unmount /media/iso/

```

---

### Post by kbless7 on 2008-01-25
> **QED314159 said:**
> Thank you kbless7 creating an iso and going from there worked perfectly. I have included the code below for anyone else who may encounter this problem.
```

:~$ sudo umount /dev/cdrom
:~$ readcd dev=/dev/cdrom f=file.iso

Read  speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Write speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Capacity: 638960 Blocks = 1277920 kBytes = 1247 MBytes = 1308 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file 'file.iso'
end:    638960
addr:   638960 cnt: 48
Time total: 298.845sec
Read 1277920.00 kB at 4276.2 kB/sec.

:~$ sudo mkdir /media/iso
:~$ sudo modprobe loop
:~$ sudo mount -t iso9660 -o loop file.iso /media/iso
:~$ cd /usr/local
:/usr/local$ sudo mkdir matlab74_sv
:/usr/local$ cd matlab74_sv
:/usr/local/matlab74_sv$ sudo /media/iso/install_unix.sh

```

After the installation is complete
```

:~$sudo umount /media/iso/

```

Good. I'm glad it worked for you. 

Enjoy the best calculating program ever.

-Matt

---

### Post by confused! on 2008-02-10
Hey -- got same problem looks like you had. i.e. can't run the installer file. But trying that script i get an error: unmount comand not found.

Any ideas?

---

### Post by kbless7 on 2008-02-10
> **confused! said:**
> Hey -- got same problem looks like you had. i.e. can't run the installer file. But trying that script i get an error: unmount comand not found.

Any ideas?

the command is "umount" not "unmount"

---

### Post by confused! on 2008-02-14
> **kbless7 said:**
> the command is "umount" not "unmount"
Ah £$%"^&££", what a muppet. Cheers Kbless.

---

### Post by twistadias on 2008-04-11
ive installed matlab r2008a but I cant launch it. 

When I press Alt+F2 and type matlab, the splash screen shows up and later disappears.

Any clue on what to do??

---

### Post by arkangel on 2008-04-11
can you open a terminal and run matlab  from there 

i dont know where you installed matlab  , but   just  type

 matlab 
 or
 /opt/matlab2007a/bin/matlab

or wherever you have matlab 

it might a license problem,  hope you have a legal copy , otherwise we cannot help you !!

---

### Post by twistadias on 2008-04-11
cheers matlab does work from the terminal.

is there any way I can close the terminal after opening matlab without quitting matlab too??

---

### Post by arkangel on 2008-04-11
yeah i remember!!!     matlab from  one reason  needs a terminal.  maybe there is a hidden  option you need to digg  

I never tried without terminal it  never bothers me , just minimize it 

you can  add matlab to the menu 

open alacarte (the menu editor)   and then  add it to the corresponding menu item you want (this works exactly like windows )  and there is one check it says something like " open in terminal "   

Warning: in alacarte there is a button that says  "revert"  don't preset you will set the menus  to the default options (as when you installed linux firt time )  

I'll try to take a look at the matlab script   (yeath the matlab comd is a script that calsl another program , actual matlab)  if i can figure out how to run it w/o terminal i will post

---

### Post by twistadias on 2008-04-11
Sweet I now have a nice little link to matlab in the education section.

---

### Post by kbless7 on 2008-04-11
the option to run without the shell of a terminal is with
```
matlab -desktop
```
just add the -desktop on the end of whatever command you use

---

### Post by sancho panza on 2008-04-11
Thats a tip I never used, always ran it from the terminal...thanks!

---

### Post by arkangel on 2008-04-11
damn  it!!  so simple  

thanks

---

### Post by twistadias on 2008-04-11
thank you so much.

---

### Post by bhaskarsanta on 2011-05-09
> **QED314159 said:**
> Thank you kbless7 creating an iso and going from there worked perfectly. I have included the code below for anyone else who may encounter this problem.
```

:~$ sudo umount /dev/cdrom
:~$ readcd dev=/dev/cdrom f=file.iso

Read  speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Write speed:  4234 kB/s (CD  24x, DVD  3x, BD  0x).
Capacity: 638960 Blocks = 1277920 kBytes = 1247 MBytes = 1308 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file 'file.iso'
end:    638960
addr:   638960 cnt: 48
Time total: 298.845sec
Read 1277920.00 kB at 4276.2 kB/sec.

:~$ sudo mkdir /media/iso
:~$ sudo modprobe loop
:~$ sudo mount -t iso9660 -o loop file.iso /media/iso
:~$ cd /usr/local
:/usr/local$ sudo mkdir matlab74_sv
:/usr/local$ cd matlab74_sv
:/usr/local/matlab74_sv$ sudo /media/iso/install_unix.sh

```After the installation is complete
```

:~$sudo unmount /media/iso/

```
What the user QED 314159   said is absolutely working fine. I came with some other problem. when i try to install MATLAB it was producing error as "/var/lib/libc.so.6" not found. The matlab is installing and working fine after immediate installation, but when i quit from this matlab after installation it was not restarting. Even i searched through command prompt as well as graphical environment for matlab and search doesn't came with any result.
I tried to install that libc through synaptic package manager but there was no file with the name libc.so.6 found in /var/lib directory. Please give me a solution to how can i overcome with this problem.

---

