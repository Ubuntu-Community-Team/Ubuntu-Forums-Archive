---
title: "Student version of MATLAB on 64-bit machine."
date: 2008-03-07
forum: Education &amp; Science
---

### Post by Raviolios on 2008-03-07
To install the student version of MATLAB 2007a under Gutsy, 64-bit, I typed the following command:

```
sudo /media/cdrom0/install_unix.sh
```

To which I got the following error:

```
    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/install/main.sh: 168: /media/cdrom0/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

```

Mathworks technical support sent the following email:
> 
There is no 64-bit Student Version of MATLAB, but it is possible to install the 32-bit version of MATLAB on a 64-bit Linux Machine.  This configuration is not officially supported, but it is expected to work. 

To install and run MATLAB, do the following:

Install MATLAB using the -glnx86 flag.  This will allow it to install properly on a 64-bit Linux machine:

./install -glnx86

Once the installer is finished, you will need to activate through mathworks.com, as the activation client will not work properly on 64-bit computers.  To do so, follow the instructions below:

[http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6](http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6)

Once MATLAB is installed and activated, you will need to run MATLAB using the same -glnx86 flag that you used to install:

./matlab -glnx86

If you try and execute matlab before activating it, you will get a java error, complaining that there is no JRE.

I followed the activation/licensing instructions, but got then error:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

when trying to execute matlab.

I logged out, restarted the X server, and then matlab worked! :) (I had also typed "xhost local:root" at the command prompt before logging out, but I don't think that is necessary for success).

---

### Post by andrew.hoell on 2008-03-26
Thanks for the excellent post!

This method will not work if 32-bit libraries are not installed, however.  Use the following command to install the 32-bit libraries.  ```
sudo apt-get install ia32-libs
```.

---

### Post by Mr. Pink on 2008-05-09
This worked excellent for me on my Macbook, but has anyone had the problem where the menu bars don't show up on the windows (like file edit etc...).  I found that if I dock figures and stuff into the main window they show up otherwise its just blank.

---

### Post by VTphilipv on 2008-08-27
Yes... Some applications seem to be unable to handle the high desktop effect settings (System-Preferences-Appearance). Set them to low while you use Matlab, and you'll be ok.
Just a shot in the dark, but could it be an X11 related problem? Someone more savvy than just the average user (me) would know...

---

### Post by arslano on 2009-10-09
Hello

I've tried this solution, but the error message still appears. When I try to install from terminal, after accepting Licence Agreement, this appears:

/home/emin/Desktop/matlab/update/install/main.sh: 582: /home/emin/Desktop/matlab/update/bin/glnxa64/xsetup: not found

What should I do?
Thanks

---

### Post by oooh on 2009-10-27
Watch out cause it also says:

[http://www.mathworks.com/support/solutions/en/data/1-1CAT7/index.html?product=ML&solution=1-1CAT7](http://www.mathworks.com/support/solutions/en/data/1-1CAT7/index.html?product=ML&solution=1-1CAT7)

So there are 64bits binaries for linux !

---

### Post by oooh on 2009-11-11
I had my 64bits matlab linux running

Just make sure your version has got the 64bits folder in the binaries

Without them, it is a mess to make matlab work, so for 64bits users, I d recommend the 64bits binaries

---

### Post by diehardyouth on 2009-11-30
> **oooh said:**
> I had my 64bits matlab linux running

Just make sure your version has got the 64bits folder in the binaries

Without them, it is a mess to make matlab work, so for 64bits users, I d recommend the 64bits binaries

If our student version doesn't have the 64-bit binaries, is there a way to get them?

Thanks

---

### Post by emigrant on 2009-11-30
is there a way to get matlab full version for free?

---

### Post by lite1979 on 2010-08-31
No, but the student version is only $100 and now lasts forever, as opposed to being a one-year subscription...

I did the same as above, used /home/lite as the root directory for the program, and got through most of the licensing stuff then it told me that activation had failed because it could not determine a machine ID.

I re-booted my computer, activated my on-board ethernet adapter, and it must have gotten the MAC address off of that because now I'm up and running!  Many thanks to the OP!

---

### Post by Vulcanasm on 2010-09-27
The reason Matlab could not determine a machine ID is that Matlab is that Matlab is hard coded to only work when your active network card is identified as   eth0. This is confirmed by their tech support, who coincidentally suggested I was some kind of idiot for having two network cards and ever using eth1. You will have to manually change the identifiers associated with your various network cards if you start getting that error. Furthermore, each time  Matlab is started, you have to ensure that you are using eth0 to connect to the internet, and you may even need the card associated with eth0 to have  the same MAC address as the one used to register Matlab. Otherwise, particularly if you don't meet the first condition, you will certainly get "cannot determine machine ID", and the subsequent call to their technical "support" may cause you to start drinking heavily at 2:00 PM.

Incidentally, for impatient people like me, here are my commands, step by step, that got Matlab R2007A Student working with 64 bit Ubuntu 10.4 this afternoon:
```
apt-get install ia32-libs
/media/MATHWORKS_R2007A/install_unix.sh -glnx86
ln -s /opt/matlab/sys/java/jre/glnx86/ /opt/matlab/sys/java/jre/glnxa64
matlab -glnx86 -nojvm
```That's it. I filled out my installer information on step 4 and it transferred the license to my new machine. It did give these miscellaneous errors on the 4th step, which have no apparent effect on Matlab functionality:

```
Severe:
The program '[3946] : Native' has exited with code 1 (0x1).
/usr/share/themes/New Wave/gtk-2.0/gtkrc:83: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuBar::shadow-type'
/usr/share/themes/New Wave/gtk-2.0/gtkrc:94: Failed to parse property value " GTK_SHADOW_NONE " for `GtkToolbar::shadow-type'
/usr/share/themes/New Wave/gtk-2.0/gtkrc:102: Failed to parse property value " GTK_SHADOW_NONE " for `GtkStatusbar::shadow-type'
/usr/share/themes/New Wave/gtk-2.0/gtkrc:104: Failed to parse property value " GTK_SHADOW_NONE " for `GtkProgressBar::shadow-type'
/usr/share/themes/New Wave/gtk-2.0/gtkrc:133: error: lexical error or unexpected token, expected valid token
```These errors do not reappear once you've finished  registration, so I conclude they're only associated with the display for the registration script. 

I have now tested Matlab now with most of a custom GUI written for my dissertation, and it's more functional in an hour than a certain Linux competitor was in a year.

---

### Post by ofloveandhate on 2010-11-22
To reply to Vulcanasm, his tips worked great for 32bit Student Matlab 2009a on a fresh 64bit install of Maverick.

the relevant commands for me, in order, were:

sudo apt-get install ia32-libs
sudo /media/MATHWORKS_R2009A/install_unix.sh -glnx86
sudo ln -s /containingdirectory/matlab/sys/java/jre/glnx86/ /containingdirectory/matlab/sys/java/jre/glnxa64
sudo chmod 777 -R /containingdirectory/matlab
matlab -glnx86

thanks to everyone in this thread, esp. Vulcanasm!

now to get hardware rendering to work...

---

