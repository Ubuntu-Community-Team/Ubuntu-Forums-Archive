---
title: "Manually downloaded program..."
date: 2009-02-12
forum: Desktop Environments
---

### Post by sreister on 2009-02-12
Hello, I am currently enrolled in a python course at the U of Iowa and we are using a program called JES(Jython Environment for Students).  Basically I couldn't find the program in the repositories and went to the site to download it.  Now the folder is on my desktop and when I try to move it, it won't let me.  How can I get this off my desktop, in the right spot, and where I can access it from the 'Applications' menu.  Thanks.

---

### Post by mikewhatever on 2009-02-12
I don't quite understand where to and why you want to move the folder from the desktop. Elaborating on that would have been nice of you. A google search turned up the following page with instructions:
[http://coweb.cc.gatech.edu/mediaComp-teach/26](http://coweb.cc.gatech.edu/mediaComp-teach/26)
>  For Linux and others
Here is the release for Linux and other Unixes. Extract the zip file and run JES.sh to start JES. You'll need to have already installed Java 1.6. Strange errors will probably result with earlier Java versions! You may need to chmod JES.sh to be able to execute it.
jes-3-1-1-linux.zip


---

### Post by sreister on 2009-02-12
OK well I downloaded the ZIP file onto my desktop and unzipped it on my desktop as well assuming I could later move the folder to it's rightful spot as I'm not familiar with ubuntu yet.  I basically want to use JES like any other program I got from the repositories.  I have the folder "JES" on my desktop and I want it in it's rightful spot so...

1.) it's not on my desktop
2.) it's in it's rightful spot where all the other program folders are
3.) so that it shows up in the 'Programming' menu under the 'Applications' menu

Hope that explains it more..

---

### Post by mikewhatever on 2009-02-12
Well, it's quite obvious that JES is not just any other program and not from the repositories. What is the 'rightful spot' you refer to, and why can't you move it there? It's important to understand that just by moving something somewhere, be it rightful or not, wouldn't place a launcher in the menu.
Did you follow the instructions after unpacking?

---

### Post by sreister on 2009-02-12
Yes, I realize that moving it to a folder won't make it magically appear in my 'Programming' menu, but I guess what I'm asking is where should I unpack this folder usr/lib64(I have the 64-bit)?  Somewhere else?  And after that, how can I get the JES to show up in a desired menu?  

As for instructions after unpacking, I don't follow you there.  I have no real instructions to go on.  

Thanks.

---

### Post by mikewhatever on 2009-02-12
I think it matters little where to unpack it. Make sure it runs, then manually create a launcher by editing the menu.

---

### Post by sreister on 2009-02-12
OK well then my question now is, where should I unpack it?  It seems to me, after a little digging, that the usr/lib64 would be where it needs to go, but I'm not sure on that.  

Also I don't seem to know how to make it manually appear like you said to edit the menu?  Like give me some code to put into the terminal or whatever.  

Thanks again for taking time to help a newb like myself.

---

### Post by mikewhatever on 2009-02-12
I don't know where to unpack it, nor why you think /usr/lib64 is the place. As mentioned above, it doesn't matter.
Let's say it's unpacked in your home folder, and the path is /home/sreister/jes-3-1-1-linux/JES.sh. To add a launcher, right click on the menu, select Edit Menu, pick the section you want the launcher in, click New Item and enter the info.

---

### Post by sreister on 2009-02-12
OK it seems to work for me.  Thanks.

---

