---
title: "SOS: Error installing MATLAB for All"
date: 2008-07-22
forum: Education &amp; Science
---

### Post by yuxuanqk on 2008-07-22
hello, everyone,

I tried to install matlab in directory "/usr/local/matlab", but I encountered some problems. The error messages like this:

Error installing MATLAB Toolbox for All
Error installing MATLAB Kernel for Linux (x86)
Error installing MATLAB for All
Error installing MATLAB for Linux (x86)
... and so on.

Although errors occured, the installation didn't stop. After it is completed, I can't find the executable file "matlab" in the directory "/usr/local/matlab/bin"

I have installed Java6 correctly (I can compile and execute java programs).

Are there anyone have the similar or same problems? I appreciate any helpful advices from you. my email address is [email]thinker_qk@hotmail.com[/email].

Thanks a lot.

---

### Post by sawjew on 2008-07-22
Did you install it as administrator?  In other words put sudo in front of the install command.

I presume you ran ```
install_unix.sh
``` in a terminal.

you need to run ```
sudo install_unix.sh
```

I have matlab installed for all with no problems but I did have to do it with sudo as a regular user does not have write permissions to /usr/local/

you may also need to create the matlab directory first ```
sudo mkdir /usr/local/matlab
```

---

### Post by Sef on 2008-07-23
Moved to Education and Science.

---

### Post by yuxuanqk on 2008-07-23
> **sawjew said:**
> Did you install it as administrator?  In other words put sudo in front of the install command.

I presume you ran ```
install_unix.sh
``` in a terminal.

you need to run ```
sudo install_unix.sh
```

I have matlab installed for all with no problems but I did have to do it with sudo as a regular user does not have write permissions to /usr/local/

you may also need to create the matlab directory first ```
sudo mkdir /usr/local/matlab
```

Yes, I did it as root.

---

### Post by sorrisosv on 2008-09-09
i am having the same problem in the installation
the same messages
can some one help???
tks

---

### Post by sawjew on 2008-09-09
Are you installing on a 32 bit system or 64 bit?

Do you have a 32 bit version of MATLAB or 64 bit?

I have successfully installed 32 bit MATLAB student edition on 64 bit Ubuntu as follows;

[LIST=1]
[*]install the 32 bit libraries;
```
sudo apt-get install ia32-libs
```
[*]make the directory to install MATLAB to;
```
sudo mkdir /usr/local/matlab
```
[*]change to the MATLAB directory;
```
cd /usr/local/matlab
```
[*]run the MATLAB installer;
```
sudo /cdrom0/install-unix.sh
```
*Note: I am not entirely sure about the path here as I do not have my MATLAB cd here at work and your path may be slightly different so check it first.*

[*]start MATLAB;
```
linux32 matlab
```
[*]Create menu entry;

Right click on the Applications menu, select edit menu, create an entry wherever you would like it to be and enter the command as mentioned in the previous point.


[*]get menu icon;

you can get a menu icon by following this link [http://www.mathworks.com/favicon.ico]("http://www.mathworks.com/favicon.ico")
[/LIST]

If you are on a 32 bit system you can leave out step one and change the command in step 5 and in the menu entry to simply ```
matlab
```

This has worked every time for me with no problems.  Just make sure you have java installed to run it but that won't stop the installation.

It's a good idea to run it from the terminal initially before you create the menu entry so you can see any error messages.

ONE EXTRA POINT: I have found that to make the menu entry work I have to set it to run the application from the terminal otherwise I just see the splash screen but it never opens.  This may be something to do with the linux32 command and may not apply on a 32 bit system.

EDIT: another easier option is to make sure you have the backport repositories enabled and then enter ```
sudo apt-get update
sudo apt-get install qtoctave
```

This will give you a free opensource alternative to MATLAB that works quite well and doesn't require jumping through hoops to get it working.

---

