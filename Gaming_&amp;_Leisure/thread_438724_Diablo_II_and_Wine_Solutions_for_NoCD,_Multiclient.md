---
title: "Diablo II and Wine: Solutions for NoCD, Multiclient &amp; Loaders...also new problems"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by murraysw on 2007-05-10
Hello everyone,

I have a vested interest in the game Diablo II and would like to make a contribution to it's deployment on Linux..

Currently there are quite a few guides to get Diablo II running well in Wine - on these forums as well as in the wine application DB.  I won't discuss basics in this thread and will only be discussing multiclient & nocd functionality.

This is the process so far:

1)  Download D2Loader from a trusted site.

2)  Download Onlyer's CD Key Refiller from a trusted site.

3)  Next we need to install D2Loader - follow the instructions provided with file - all you will be doing is replacing the original "Diablo II.exe" with the modified executable.  The only difference you will need to take note of is that the D2 folder is located at /home/*usrname*/.wine/drive_c/Program Files/Diablo II/.  I suggest renaming the original "Diablo II.exe" something like "Diablo II (original).exe" before you replace it in case something goes wrong.

4)  Now we will quickly make a shortcut to the loader - right click the desktop and press "Create Launcher".  The "Command" field should read something like:

```

wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d9 -w

```

Remember that referring to "C:\xxx\xxx\" simply points to Wine's virtual drive C, located in /home/*usrname*/.wine/drive_c/  - where we were modifying the files and placing the loader before.  The -w command makes it run in a window, which I've found to be necessary.  The -d3d9 command tells Wine to use Direct X 9 when launching the game - opengl causes the graphics to be glitchy.


--------------------------------
Stepping toward multiclient
--------------------------------

I have tried many things to successfuly multiclient Diablo II with Wine.  Nothing has been perfect so far, but I am VERY close and have only a minor issue involving window managers and how Wine is interacting with them.

The process here is a tad bit trickier since it involved importing registry keys.  I will outline the process in detail now and later move on to the issues with window managers.

1)  After you have installed D2Loader it becomes possible to run multiple clients of Diablo II - there are issues with this in itself, but we will discuss them later. The point here is that we need to have the game using seperate CD Keys if we wish to have true multiclient functionality.  This was my first objective, and it involves Onlyers - so extract Onlyer's cd key refiller to a folder in your Diablo II directory to start.

2)  There are instructions included with Onlyer's, but they require slight modification.  Here they are with changes:

  2a) Copy the file cdkey.mpq to the Diablo II folder (it comes in the Onlyer zip).


   2b) Open the file auto-cdkey.reg with your favourite text editor and set these two lines to point to the                  cdkey.mpq file which you just moved into your D2 directory. 


"d2cdkeympq"="cdkey.mpq"

"d2xcdkeympq"="cdkey.mpq"

This is the mpq file which will be injected with your second set of keys and which D2Loader will force the client into using in order to achieve battle.net multiclienting.


   2c) In the same file, replace the variables "d2cdkey" and "d2xcdkey" to the cdkey to your second set of keys.  The ones already in the file are EXAMPLES, delete them and insert your second set of keys in the same fashion (HINT: NO DASHES!).



   2d) Next, in a terminal type 

```

wine regedit.exe

```

This should bring up the registry editor.


    2e)  From the "File" menu select "Import Registry Key".  We will now need to find the auto-cdkey.reg file we just modified and import it.  Remember it is located in your virtual drive C.  Once it is imported there isn't really any confirmation, so just close it.


    2f)  Use Wine to run Onlyer's CD Key refiller.  I'm pretty sure you don't need to use any switches like -d3d9 or -w to run it, but if things go wrong, try both out.  Press "refill keys" when the refiller comes up.  Again there will be no confirmation and it will seem as if you never clicked it, but one click does it.  Close after you press refill.


3)  You now have a seperate mpq file that Loader can point to for retrieving cdkeys.  To do this we simply use the -mpq switch when we launch it with Wine.  Here's what the "command" looks like for the second shortcut to Diablo II which uses our alternate set of keys:

```

wine "C:\Program Files\Diablo II\Diablo II (2).exe" -d3d9 -w -mpq cdkey.mpq

```

As you can see the Loader is pointing to our newly modified cdkey.mpq to get our second set of keys!!  **This is fully functional multiclienting!!!  **



[B]-------------------
MULTICLIENT INTERACTION WITH WINDOW MANAGERS (A SOLUTION)
-------------------
[/B]

I'm sure I'm not the only one that experiences Diablo II shrinking to the minimum possible window size when a second client is opened.  There is a solution for this, and it is quite simple although it will take up a large amount of Harddrive space because essentially the only way I've found to do this is to copy the .wine folder and rename it.  Here are the steps:

1)  Make a copy of your .wine folder and rename it something like .wine2.  In your .wine2 folder you only need the directory structure to Diablo II, but make sure it's PROPER .... /home/scott/.wine2/drive_c/Program Files/Diablo II is what your .wine2 path should look something like!  Remember that if your .wine directory is huge you DO NOT need every other folder from your "program files" folder to .wine2, you ONLY NEED THE DIABLO II FOLDER WITH PROPER DIRECTORY STRUCTURE.

2)  Next we simply modify the launcher to launch Diablo II from the second wine folder.  Here is what my third shortcut looks like which takes advantage of a third wine folder and a third cdkeys.mpq which I injected:

```

env WINEPREFIX="/home/scott/.wine3" wine "C:\Program Files\Diablo II\Diablo II (3).exe" -d3d9 -w -skiptobnet -mpq cdkeys3.mpq

```

The env WINEPREFIX points to your newly copied .wine directory.  As you can see, mine points to the third one and uses the cdkeys I stored in cdkeys3.mpq (using the steps above).  Now you can have Diablo II clients on every side of your Beryl cube.  Enjoy!!


-Scott

---

### Post by God Of Atheism on 2007-05-10
One question: are the multiple cd keys absolutely necessary or only necessary for online play?

As to the very small windows, I've noticed that when I accidentally start a second instance, I get two very small windows as well, before both crash with c0000005 or me killing both. This is without trying any of the above instructions.

On a graphics note, in my experience, the 2d mode works better than the 3d mode, there is no opengl mode, there is a glide mode, but there does exist a wrapper from glide to opengl that works for some. (not for me though)

---

### Post by lerchedahl on 2007-05-10
I've had the excact same problem with running d2 in windowed mode and when I switch workspace or tab to the desktop it would shrink to the minimum possible window size. The only fix I could manage was to stop the application from integrating with the window manager in winecfg. Not really a viale solution, but it kinda works. And just to clarify, it has nothing to do with running multiclient.

---

### Post by murraysw on 2007-05-10
***I have solved the problem****

To stop Diablo II from shrinking to the minimum possible window size when a second client is opened, you need to make a copy of your .wine directory and rename it.  If you have other things installed, you really only need to move over the windows directory and the directory structure to the Diablo II folder.  Rename this new wine folder .wine2...

Now, you will launch your SECOND d2 window from the SECOND wine directory using this command:

env WINEPREFIX="/home/scott/.wine2" wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d9 -w


The important thing is the env WINEPREFIX because this sets the Wine directory to the second one we just created.

ENJOY!!

---

### Post by magic_ninja on 2007-06-09
When I start d2 with d2loader I get an error message, I believe the problem lies in the sound, as here is a snippet of some code

Backtrace:
=>1 0x6f9b9878 in d2sound (+0x9878) (0x00000000)
0x6f9b9878: movl        0x0(%edx),%ebx
Modules:

---

### Post by dollarbill082 on 2007-07-29
Similar option that I have found easier is to do is install the second copy under a different user with its own wine directory.

Then you can log into your normal account run 1 copy of D2Loader.  Then open a terminal and run:
*xhost +*
*su - <other_account>*
*export DISPLAY=:0.0*
*wine D2Loader*

What would be nice about this option is if you can do the same if the other copies of Diablo are on a different machine.  Then your Display machine is not bogged down with the actual running of the extra Diablo instances.

Cheers!

---

