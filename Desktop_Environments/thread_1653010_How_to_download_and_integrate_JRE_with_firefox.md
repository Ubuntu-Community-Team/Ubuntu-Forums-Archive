---
title: "How to download and integrate JRE with firefox"
date: 2010-12-26
forum: Desktop Environments
---

### Post by Yash Pal on 2010-12-26
OS: Ubuntu 7.04 (before you tell me to upgrade to a newer release, my computer does not support any later release- If I cannot learn on 7.04, I cannot learn the same on a newer release)

Computer: P3 800mz, ram 512mb 

My firefox browser upgraded itself (of course I did agree when I was told by it that I should upgrade).

The problem is that I have to install JRE as there are no graphics available. It has to be a manual install.

I downloaded JRE6u23 (that is what it says when mouse hovers over it) and proceeded to fix or integrate it with firefox or the os (whichever way it can be integrated) 

As instructed by the jre site, I gave the command 'chmod'; the result is below:

                                                yashpal@yashpal-desktop:~$ sudo su
 

 Password:
 

 root@yashpal-desktop:/home/yashpal# chmod a+x jre-6u23-linuxi586.bin
 

 chmod: cannot access `jre-6u23-linuxi586.bin': No such file or directory
 

 root@yashpal-desktop:/home/yashpal#



Can anyone tell me what mistake I have made.

---

### Post by sid.mallya on 2010-12-26
Okay .. I am assuming u r completely new to Linux. Anyway, sudo and su are two different commands and you should not use them together. 

sudo gives u temporary root priviledges for a particular command, su on the other hand makes u the root, until u type exit (or close the terminal). As far as possible, always use 'sudo' .. Being root gives u unlimited ways to mess up the system.

Moving on, 
1. first type "ls" in the directory to make sure you have your file in the folder u r in .. 
2. To find out what folder u r in, type "pwd" .. Then check with your browser where you downloaded the file to. 
3. Go to that folder by "cd <path/to/dir>" 
4. Then type, "chmod a+x <filename>" .. 

If it still isn't happening .. Use the GUI method. 

1. Select the file u want to make 'executable' 
2. Right click on it and goto properties and then the 'permissions' tab
3. Check the box next to "Execute" saying "allow executing file as program"

Your file is now an executable .. Then follow the rest of the instructions .. 

Btw, if u r using Ubuntu, you may need Alien to convert the JRE rpm to deb ..

---

### Post by Yash Pal on 2010-12-29
Many thanks Mr Mallaya. I am trying to learn Linux (as a desktop user) for the last 5 years on my own as the money making factories in the guise of trg institutions did not teach anything worthwhile.

I will try to implement all your suggestions.
Thanks once again.

---

