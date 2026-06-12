---
title: "Launching Matlab"
date: 2009-04-29
forum: General Help
---

### Post by dsmilo on 2009-04-29
After installing MATLAB on my computer, I encountered a few problems:

First, with Compiz running, the toolbars do not display.  I found a solution for that here: [http://ubuntuforums.org/showthread.php?t=579281](http://ubuntuforums.org/showthread.php?t=579281)
Second, once the script was written, I could not launch MATLAB with a simple terminal command or create a simple terminal.  Combining the above with this advice [http://ubuntuforums.org/showthread.php?t=1050291](http://ubuntuforums.org/showthread.php?t=1050291) my problems are solved.  Here's the summary for those also struggling:

1. You are going to need to create a script in order to do this easily.  In order to find where to put this script so that it is globally executable, type "echo $PATH" (no quotes) into a terminal.  Pick one of the paths displayed (I used /usr/local/bin) and change to this directory.

2. Now to create the script.  Create a file called "matlab" by typing "sudo gedit matlab" and enter the following code
```
#!/bin/bash
unset LANG
export AWT_TOOLKIT=MToolkit
/home/dsmilo/MATLAB/bin/matlab -desktop
```
adjusting the last line to fit the location of your MATLAB directory

3. After saving the file, you must make it accessible in all directories.  To do this, type "sudo chmod 755 matlab."

You should now be able to access MATLAB (and Simulink) from anywhere by typing "matlab" into a terminal.

If you want to create a launcher (in the panel or the Applications menu), create the custom launcher, set the type to Application and the command to matlab.  For an icon, you can just place a .png file of the logo (wikipedia has one) in your MATLAB folder and browse to it.


Hope this helps someone out, I just wanted to make life a bit easier for anyone else stuck.

---

### Post by KRTW on 2009-06-19
I get this error:

```
Unable to initialize com.mathworks.mwswing.MJStartup
Fatal Error on startup: Failure loading desktop class

```

My matlab script looks like this:

```
#!/bin/bash
unset LANG
export AWT_TOOLKIT=MToolkit
/usr/local/matlab/bin/matlab -desktop
```

Any thoughts?

---

