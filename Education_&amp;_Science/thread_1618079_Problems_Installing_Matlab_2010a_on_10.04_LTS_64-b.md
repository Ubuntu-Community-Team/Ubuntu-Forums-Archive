---
title: "Problems Installing Matlab 2010a on 10.04 LTS 64-bit"
date: 2010-11-10
forum: Education &amp; Science
---

### Post by alion1234 on 2010-11-10
I was hoping somebody could help me with installing Matlab 2010a on my desktop, basically I followed the instructions on their website ([http://www.mathworks.com/downloads/web_downloads/manual_download_instructions](http://www.mathworks.com/downloads/web_downloads/manual_download_instructions)), here is what I did on the terminal:

[FONT=Courier New]"

james@james-desktop:~/Downloads/matlab$ ls
matlab_installer_glnx86.tar  stu_matlab_glnx86.tar
james@james-desktop:~/Downloads/matlab$ tar -xf matlab_installer_glnx86.tar
james@james-desktop:~/Downloads/matlab$ ls
activate.ini  install  license.txt  matlab_installer_glnx86.tar  stu_matlab_glnx86.tar  update
james@james-desktop:~/Downloads/matlab$ ./install

Extracting student file stu_matlab_glnx86.tar

Extracting ftp files . . . [please wait]
Extracting matlab.common
Extracting matlab.glnx86
Finished extracting ftp files.
Starting installer ...
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/james/Downloads/matlab/update/install/main.sh: 178: /home/james/Downloads/matlab/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

james@james-desktop:~/Downloads/matlab$

"

[FONT=Verdana]I basically don't have a clue what it means by 'X[/FONT]' 

[FONT=Verdana]
I have tried to use other software like octave and free-mat, but matlab is what I have been using for almost 3 years now and some of the projects [/FONT][/FONT]for my degree have to be done on matlab and I have already paid for the licence (£50!)

If anybody knows how I can solve this problem, I would be very happy.

Cheers

---

### Post by Blutkoete on 2010-11-11
You have to set the permissions of xsetup to "executable".

See this thread ([http://ubuntuforums.org/showthread.php?t=1607315](http://ubuntuforums.org/showthread.php?t=1607315)), just use your own directories.

Best regards,

Blutkoete

---

### Post by Blutkoete on 2010-11-11
Wait --- sorry, the error is a different one. I was too fast.

I think there is no 64bit version of student's MATLAB, so the installer can't find the 64bit setup program. I'll have a look at my installation to look how to force it to use the 32bit installer.

**EDIT:** Check this blog entry: [http://saravananthirumuruganathan.wordpress.com/2010/02/10/installingrunning-matlab-and-compiling-matlab-extensions-in-a-64-bit-ubuntu-system/](http://saravananthirumuruganathan.wordpress.com/2010/02/10/installingrunning-matlab-and-compiling-matlab-extensions-in-a-64-bit-ubuntu-system/)

---

