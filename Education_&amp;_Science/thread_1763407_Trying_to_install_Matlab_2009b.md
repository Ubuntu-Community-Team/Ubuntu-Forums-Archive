---
title: "Trying to install Matlab 2009b"
date: 2011-05-20
forum: Education &amp; Science
---

### Post by zmall88 on 2011-05-20
Hello,

I'm a complete newbie to Linux and this Unix thing. I'm trying to install Matlab 2009b from some downloaded files (not CD).

I am using the directions available at the Ubuntu documention, [here]("https://help.ubuntu.com/community/MATLAB/R2009b"). I get the following error:

> 
/usr/local/matlabR2009b$ sudo sh /matlab2009b/install
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /matlab2009b/update/install/main.sh: 178: /matlab2009b/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
I also tried gksudo. I also tried doing the install*-t but it still doesn't work, giving me a permission denied error. 

I don't know how to use the line that is suggested in step 3:

> 
sudo sh /media/cdrom0/install_unix.sh -glnx86
I think that maybe where the problem is. I'm really stuck here, any help is welcome!

---

### Post by Lateralis on 2011-05-21
First question: is /matlab2009b/update/bin/glnx86/xsetup executable?  Do you need to chmod the file to give it executable permissions?  

Second question: This "step 3" - are you installing from a CD or a downloaded file/directory from the Matlab site?  If the former, and your cdrom is mounted at /media/cdrom0 then you can run that command from a terminal.

---

### Post by zmall88 on 2011-05-22
> **Lateralis said:**
> First question: is /matlab2009b/update/bin/glnx86/xsetup executable?  Do you need to chmod the file to give it executable permissions?  

Second question: This "step 3" - are you installing from a CD or a downloaded file/directory from the Matlab site?  If the former, and your cdrom is mounted at /media/cdrom0 then you can run that command from a terminal.


Thanks! I set the permissions via the GUI but the installation still didn't work. I then did chmod 777 * and it worked like a charm.

---

