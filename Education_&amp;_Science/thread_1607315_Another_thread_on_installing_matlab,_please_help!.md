---
title: "Another thread on installing matlab, please help!"
date: 2010-10-27
forum: Education &amp; Science
---

### Post by madambaf on 2010-10-27
Hi,

I am tried to install Matlab following [this]("https://help.ubuntu.com/community/MATLAB") instructions however I have encountered an error. In the 3rd step:

3. Run the MATLAB installer: 
```
sudo sh /media/MATHWORKS_R2010A/install 
```I input the code however I encounter this error:

3. Run the MATLAB installer: 
sudo sh /media/MATHWORKS_R2010A/install ```
 An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/MATHWORKS_R2010A/update/install/main.sh: 178: /media/MATHWORKS_R2010A/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

```

I follow what they say and input this line:

```
sudo sh /media/MATHWORKS_R2010A/install* -t
```

I feel like I am in the clear when I get this message:

```
 Welcome to the MATLAB Installer

   ---------------------------------------------------------------------------
   | Please review the license agreement on the next set of screens.  On any |
   | screen the options to proceed are at the bottom.  Type your response    |
   | at the prompt.                                                          |
   ---------------------------------------------------------------------------

                      The MathWorks, Inc. [screen 1 of 87]
                      -------------------                 
Software License Agreement 


IMPORTANT NOTICE

READ THE TERMS AND CONDITIONS OF YOUR LICENSE AGREEMENT CAREFULLY BEFORE 
COPYING, INSTALLING, OR USING THE PROGRAMS OR DOCUMENTATION.
----------------------------------------------------------------------------
                >>>>>>>> For this License Agreement <<<<<<<<
Enter either:  <return>       a        r        p      ^C
To:          [next screen] [accept] [reject] [print] [abort]

```

However as soon as I press "a' I get this: 

```
/media/MATHWORKS_R2010A/update/install/main.sh: 582: /media/MATHWORKS_R2010A/update/bin/glnx86/xsetup: Permission denied

```

I've been trying for quite a while now on installing Matlab on ubuntu but I keep getting the same problem. I tried different ubuntu versions as well as Matlab versions however its the same error. 

If someone could help me I would really appreciate it, thanks in advanced!

---

### Post by Blutkoete on 2010-11-01
Try

```
sudo chmod +x /media/MATHWORKS_R2010A/update/bin/glnx86/xsetup
```

and then again

```
sudo sh /media/MATHWORKS_R2010A/install
```

---

### Post by meierbac on 2010-11-03
The response from Blutkoete was correct; you need to modify the permissions of both the install file and xsetup. Follow the instructions and it should work just fine.

** Note: this error can occur even when installing from downloaded files with no DVD drive to mount!

---

### Post by AbidUllah on 2011-07-25
I have the same error as above.I followed the instructions but I still get the same error. any help?

---

### Post by tommpogg on 2011-07-26
> **meierbac said:**
> The response from Blutkoete was correct; you need to modify the permissions of both the install file and xsetup.


Then, shouldn't they type also the following command?
```

sudo chmod +x /media/MATHWORKS_R2010A/install

```

---

### Post by andybrownandy on 2011-07-26
i m also getting the same problem for quite some time.

---

### Post by AbidUllah on 2011-07-26
The above method worked for me. Just a helping note... you need to check with ls -l command if the file have to execute permission or not.

---

