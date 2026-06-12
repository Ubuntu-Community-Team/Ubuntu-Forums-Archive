---
title: "I can not install wolfenstein enemy territory. PLEASE HELP! I BEG"
date: 2009-04-09
forum: General Help
---

### Post by krine11 on 2009-04-09
Hi there. I switched to ubuntu and updated everything and so on. I than was instlling a game called Wolfenstein Enemy Territory (the game i played all day on windows) so now when i try installing it on ubuntu i CAN NOT INSTALL IT!. The name of the file is : et-linux-2.55. x86.run and when i double click on it this is what i recive, here is a screenshot of what i mean : [img]http://img382.imageshack.us/img382/8027/screenshot1.png[/img] 

Can you please tell me what i did wrong??

---

### Post by Yvan300 on 2009-04-09
In terminal:

cd file/location/
e.g cd Documents
chmod +x et-linux-2.55. x86.run
sudo ./et-linux-2.55. x86.run

And let the fun begin :)

---

### Post by krine11 on 2009-04-09
> **Yvan300 said:**
> In terminal:

cd file/location/
e.g cd Documents
chmod +x et-linux-2.55. x86.run
sudo ./et-linux-2.55. x86.run

And let the fun begin :)

The fun did not start yet. Look what i recive after that

sharma@rohit-sharma:~$ cd file/location/
bash: cd: file/location/: No such file or directory
sharma@rohit-sharma:~$ e.g cd Documents
bash: e.g: command not found
sharma@rohit-sharma:~$ chmod +x et-linux-2.55. x86.run
chmod: cannot access `et-linux-2.55.': No such file or directory
chmod: cannot access `x86.run': No such file or directory
sharma@rohit-sharma:~$ sudo ./et-linux-2.55. x86.run

---

### Post by Vaphell on 2009-04-09
remove space from the file name (between 2.55. and x86) :D

and dont take cd file/location literally, insert path to actual directory, for example home/yourname/desktop or whatever it is :D

in short steps are:
1. go to directory containing install file
cd <path>
2. change permissions (allow executing)
chmod +x <filename>
3. execute file (with superuser proviledges - sudo)
sudo ./<filename>

---

### Post by krine11 on 2009-04-09
the path is really desktop

---

### Post by Vaphell on 2009-04-09
so correct commands would be:
cd Desktop
chmod +x et-linux-2.55.x86.run
sudo ./et-linux-2.55.x86.run

there were 2 problems. You didn't go to Desktop (terminal starts in /home/yourname)
and there was space which broke file name into 2 parts and system couldn't figure it out

---

### Post by krine11 on 2009-04-09
I still dont get it. I am a NOOB at ubuntu so can you please tell me step by step (CLEARLEY) please!

---

### Post by krine11 on 2009-04-09
harma@rohit-sharma:~/Desktop$ chmod +x et-linux-2.55.x86.run
sharma@rohit-sharma:~/Desktop$ sudo ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/sharma/.setup8243: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
sharma@rohit-sharma:~/Desktop$ 


now whats wrong?

---

### Post by Vaphell on 2009-04-09
missing library libgtk-1.2
in terminal:
sudo apt-get install libgtk1.2

---

### Post by krine11 on 2009-04-09
It works thanksss!!!

---

### Post by krine11 on 2009-04-09
Ok it works fine but IT LAGS LIIKE HELL and the mouse control is off. Can you help me again your doing a good job :)

---

