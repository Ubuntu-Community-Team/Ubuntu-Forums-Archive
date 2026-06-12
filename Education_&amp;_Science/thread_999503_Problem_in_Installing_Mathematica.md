---
title: "Problem in Installing Mathematica"
date: 2008-12-01
forum: Education &amp; Science
---

### Post by aprashanth on 2008-12-01
Hello all .. i am trying to install Mathematica6.0 on ubuntu..
it is never prompting for the password.. instead it is directly giving the Error as below.

Error: The installer was unable to check for a valid password file. Your
Mathematica installation may be incomplete or corrupted.

Can any one please help me with this..i am toling with this from past one week.. i am posting the entire terminal listings..

--------------------------------------------------------------------------------
                     Wolfram Mathematica 6.0.0 Installer 
--------------------------------------------------------------------------------

Copyright (c) 1988-2007 Wolfram Research, Inc. All rights reserved.

WARNING: Mathematica is protected by copyright law and international
treaties. Unauthorized reproduction or distribution may result in severe
civil and criminal penalties and will be prosecuted to the maximum extent
possible under law.

Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/6.0:
> 

Now installing...

[*****************************************************************************]

Type the directory path in which the Mathematica script(s) will be created,
or press ENTER to select /usr/local/bin:
> 

The scripts 'MathKernel', 'Mathematica', 'math', 'mathematica', 'mcc' already
exist in the directory /usr/local/bin. The following actions can be performed
on the existing file(s).

  (1) Overwrite
  (2) Rename

Type your selection, or press ENTER to select (1):
> 1


Error: The installer was unable to check for a valid password file. Your
Mathematica installation may be incomplete or corrupted.


Installation failed. See /usr/local/Wolfram/Mathematica/6.0/InstallErrors.

root@tsrinu-desktop:/media/cdrom/Mathematica-6_linux/Unix/Installer#

---

### Post by gunksta on 2008-12-02
I have never installed Mathematica, but I would start by looking at the file listed in the error output:

 /usr/local/Wolfram/Mathematica/6.0/InstallErrors

Look at this file with something like Gedit or

```
less /usr/local/Wolfram/Mathematica/6.0/InstallErrors 
```

This will probably tell you more.

It also looks like you are acting as root. What process did you use to "become" root. I usually just do everything through sudo which is typically the "ubuntu way" of doing things.

---

### Post by gunksta on 2008-12-02
EDIT: I accidentally double posted.

---

### Post by cpgos on 2008-12-02
aprasanth,
I installed Mathematica a few months ago and got a similar message, on contacting Wolfram support the following advice was given :

[COLOR="Blue"]There are two things you need to check:
1. Check you have installed libstdc++5 by typing:
   sudo apt-get install libstdc++5

2. If you go to /usr/local/bin (default directory) and see Mathematica
scripts are there, that means installation is complete. Please type ./math
under this directory and you should be asked to enter license number,
organization and password. Please go to [http://register.wolfram.com](http://register.wolfram.com) to
register your information to acquire the valid password.[/COLOR]

I hope that this is of help.

Best regards,
cpgos

---

### Post by skintythe1andonly on 2008-12-03
I installed mathematica only a few days ago... cpgos is correct. You need libstdc++5 installed.

---

