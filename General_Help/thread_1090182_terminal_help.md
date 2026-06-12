---
title: "terminal help"
date: 2009-03-08
forum: General Help
---

### Post by r0k on 2009-03-08
when i try to run a file through the terminal this is the error i receive!  please help


Could not display "/home/jake/Desktop/hxplay-11...inux-2.2-libc6-gcc32-i586.bin"

There is no application installed for this file type

---

### Post by dzark on 2009-03-08
ummm.. what is the file and what are you trying to do?

is it a program? a disk image? etc? etc?

---

### Post by r0k on 2009-03-08
im trying to install realplayer11gold.bin

---

### Post by taurus on 2009-03-08
Is it realplayer11gold.bin or RealPlayer11GOLD.bin?  Unix/Linux is case sensitive so those two files are _not_ the same.

```
ls -la ~/Desktop
```

---

### Post by DarthBrady on 2009-03-08
Try this:

Open places, and locate the file on the desktop. Right-Click it, choose 'properties'. Under the 'basic' tab (should open to it by default) you will see the file's location/path. copy and paste the location.

Then you can paste it to a cd command in the terminal, to ensure you are using the correct path to the file. Was a big help to me, and sometimes still is ;) Also, make sure you are using the correct command for the job, and double check the filename at the end of the path is typed correctly.

Hope that helps-

---

### Post by dzark on 2009-03-08
run it with

```
sudo ./hxplay-11...inux-2.2-libc6-gcc32-i586.bin
```

note the period (fullstop) before the first slash

---

### Post by r0k on 2009-03-08
i tried both methods and have received pretty much the same error



jake@jake-desktop:~$ /home/jake/desktop/RealPlayerGOLD.bin
bash: /home/jake/desktop/RealPlayerGOLD.bin: No such file or directory

---

### Post by taurus on 2009-03-08
> **r0k said:**
> i tried both methods and have received pretty much the same error



jake@jake-desktop:~$ /home/jake/**[COLOR="Red"]d[/COLOR]**esktop/RealPlayerGOLD.bin
bash: /home/jake/desktop/RealPlayerGOLD.bin: No such file or directory

Are you sure you have ~/desktop instead of ~/Desktop?  Again, Unix/Linux is case sensitive so Desktop is _NOT_ the same as desktop.

Run these two command from a terminal and post the output of the second one here.

```
cd ~/Desktop
ls -la
```

---

### Post by cyfur01 on 2009-03-08
Try following [this]("http://taufanlubis.wordpress.com/2008/09/24/how-to-install-real-player-11-gold-for-linux/").

---

### Post by r0k on 2009-03-08
jake@jake-desktop:~/Desktop$ ls -la
total 32404
drwxr-xr-x  2 jake jake     4096 2009-03-07 23:20 .
drwxr-xr-x 31 jake jake     4096 2009-03-08 00:47 ..
-rw-r--r--  1 jake jake  3551629 2009-03-07 22:53 hxplay-11.0.0.4052-linux-2.2-libc6-gcc32-i586.bin
-rw-r--r--  1 jake jake 21755497 2009-03-07 23:20 NVIDIA-Linux-x86-180.29-pkg1.run
-rw-r--r--  1 jake jake  7815081 2009-03-07 22:54 RealPlayer11GOLD.bin

---

### Post by dzark on 2009-03-08
cases buddy... desktop is _D_esktop

open up terminal and type..

```
cd De(then press the tab button)
``` and it'll fill out the rest of Desktop

then type ```
ls *.bin
```

which will _l_i_s_t the files ending in .bin

then, run the program with

```
sudo ./whateveritscalled
```

again you can do the tab-autocompletion trick, try after the first or second letter..

---

### Post by taurus on 2009-03-08
Now, you need to change the permissions to executable so you can run it.

```
chmod +x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin
```

---

### Post by r0k on 2009-03-08
thank you so much again torus i really appreciate the help!  this is very alien to me but i am very interested in learning this OS so i hope everybody in this community has patience! LOL

Thanks to everybody else who dedicated any thoughts to this matter!!

---

