---
title: "com port help please (bitpim)"
date: 2005-12-22
forum: Desktop Environments
---

### Post by fletch331360 on 2005-12-22
i have installed bitpim a software designed to manipulate my lg phone. the program installed just fine and runs great except i am unable to connect to my phone because bitpim says no phone detected. 

when running in windows i would have to install the lg modem drivers to get this to work but i dont know if that is needed for linux.

bitpim show 1 available port when i have the phone plugged in that is " USB modem (/dev/ttyACM0) " . however when i choose this port to connect thru i get " no phone detected or recognized " . i have been searching for weeks to fix this. please help.

does anyone have anysuggestions on how i might get this to work?

this is the only thing keeping me from getting rid of windows all together.

thanks

---

### Post by briancurtin on 2005-12-22
i dont really see how this is a problem with ubuntu. i understand you are missing some drivers possibly, but BitPim forums would probably be the place to look on problems with BitPim.

---

### Post by Kratos on 2006-03-31
[QUOTE=briancurtin]i dont really see how this is a problem with ubuntu. i understand you are missing some drivers possibly, but BitPim forums would probably be the place to look on problems with BitPim.[/QUOTE]
Last I checked, bitpim didn't have a forum.

---

### Post by r3v3rs3pa on 2006-04-09
link-deleted see below:
the problem isnt 100% bitpim, it is just usb recognition, i believe, but then, i am just beginning to follow the page myself, so i could be wrong.
anyways, it should solve your problems. i will likely post again if it seems necessary.

EDIT:
um, i posted more info here, just cuz topic seemed mroe specific...
[http://ubuntuforums.org/showthread.php?t=145946](http://ubuntuforums.org/showthread.php?t=145946)

---

### Post by hbj on 2006-06-27
BitPim 0.9.03 official is working just fine for me in Dapper with an LG-PM225.  dmesg shows 

cdc_acm 3-2:1.0: ttyACM0: USB ACM device

I used alien to convert the .rpm to a .deb and installed it.  In Edit/Settings I set the Phone Type to LG-PM225 and Com to auto.  Everything works perfectly except that I had to launch bitpim with kdesu which I suspect just indicates a permission issue, probably with the USB device.  I didn't need to do any other configuration.

---

### Post by lorddaddy84 on 2006-10-24
I can access my file system on my E816 but when I try to read the phone book off the phone, I get this error.
> BitPim version: 0.9.07-official
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "src/gui.py", line 1770, in OnCallback
  File "src/gui.py", line 177, in __call__
  File "src/gui.py", line 134, in __call__
  File "src/gui.py", line 1614, in OnProgressMinor
  File "src/guiwidgets.py", line 1277, in progressminor
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 928, in SetValue
PyAssertionError: C++ assertion "wxAssertFailure" failed in ../src/gtk/gauge.cpp(95): invalid value in wxGauge::SetValue()

Variables by last 8 frames, innermost last

Frame MainLoop in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py at line 7720
           self =  <gui.MainApp; proxy of C++ wxPyApp instance at _d0654f08_p_wxPyApp>

Frame MainLoop in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py at line 7153
           args =  (<gui.MainApp; proxy of C++ wxPyApp instance at _d0654f08_p_wxPyApp>,)
         kwargs =  Keys []
                   {}

Frame OnCallback in src/gui.py at line 1770
           self =  <gui.MainWindow; proxy of C++ wxFrame instance at _680f6408_p_wxFrame>
          event =  <gui.HelperReturnEvent; proxy of C++ wxPyEvent instance at _488e0209_p_wxPyEvent

Frame __call__ in src/gui.py at line 177
           self =  <gui.HelperReturnEvent; proxy of C++ wxPyEvent instance at _488e0209_p_wxPyEvent

Frame __call__ in src/gui.py at line 134
           self =  <gui.Callback instance at 0xb5568e8c>
           args =  (500, 10, 'Reading conatct entry 1 to 10')
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame OnProgressMinor in src/gui.py at line 1614
            max =  10
           self =  <gui.MainWindow; proxy of C++ wxFrame instance at _680f6408_p_wxFrame>
            pos =  500
           desc =  'Reading conatct entry 1 to 10'

Frame progressminor in src/guiwidgets.py at line 1277
            max =  10
           self =  <guiwidgets.MyStatusBar; proxy of C++ wxStatusBar instance at _90256408_p_wxStat
            pos =  500
           desc =  'Reading conatct entry 1 to 10'

Frame SetValue in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py at line 928
           args =  (<wx._controls.Gauge; proxy of C++ wxGauge instance at _e0726e08_p_wxGauge>, 500
         kwargs =  Keys []
                   {}

Any Ideas, I would like to be able to sync my phone book.

---

### Post by 13east on 2007-05-14
> **fletch331360 said:**
> i have installed bitpim a software designed to manipulate my lg phone. the program installed just fine and runs great except i am unable to connect to my phone because bitpim says no phone detected. 

when running in windows i would have to install the lg modem drivers to get this to work but i dont know if that is needed for linux.

bitpim show 1 available port when i have the phone plugged in that is " USB modem (/dev/ttyACM0) " . however when i choose this port to connect thru i get " no phone detected or recognized " . i have been searching for weeks to fix this. please help.

does anyone have anysuggestions on how i might get this to work?

this is the only thing keeping me from getting rid of windows all together.

thanks

i'm been having the same problem w/ my lg cu500 (cingular) phone for the longest while now... i'm really getting tired to switching to Windows XP everytime i need to access my phones filesystem... if anyone knows how to get bitpim to work w/ my phone i would every much appreciate it... thx

**[COLOR="Red"]edit:  Finally got bitpim to recognize my phone... [/COLOR]**
1) ```
sudo aptitude install bitpim
```
2)```
cd /usr/lib
```
3)create a symlink : ```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```
4)launch program: ```
sudo bitpim
```
5)setup your phone... in my case(lg cu500) i had to set bitpim to other cdma and auto detect the phone on startup

full credit to the solution goes to pooslinger [http://ubuntuforums.org/showthread.php?t=145946&page=5](http://ubuntuforums.org/showthread.php?t=145946&page=5)

the only problem i've seen so far is that i the program hangs every time i try to close it because it's always under a busy status... but hopefully that too should be soon solved... hopefully...

---

