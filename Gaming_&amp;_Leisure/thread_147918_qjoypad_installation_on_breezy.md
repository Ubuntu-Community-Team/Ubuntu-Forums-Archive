---
title: "qjoypad installation on breezy"
date: 2006-03-21
forum: Gaming &amp; Leisure
---

### Post by trent dillman on 2006-03-21
After ripping my hair out trying to install qjoypad, I finally succeeded, so I figured I would share how I did it.

First, I downloaded the .rpm from [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

NOTE: the .deb doesn't work, because it suffers from the wretched libqt3-mt dependency hell. The source wouldn't compile for me, first throwing qmake errors and then (after a simple symlink) complaining about a type declaration in layout.h.

Then, I converted it with alien:

fakeroot alien qjoypad-3.4-1.i586.rpm

I installed using dpkg:

sudo dpkg -i qjoypad_3.4-2_i386.deb

I then linked the icons so they actually worked:

cd /usr/local/share/pixmaps/qjoypad/
sudo ln -s gamepad2-24x24.png icon24.png
sudo ln -s gamepad2-64x64.png icon64.png

NOTE: try `eog /usr/local/share/pixmaps/qjoypad/ &` first if you want a choice of icons! 

Finally, I hope someone fixes this stupid libqt3-mt dependency crap.

Regards,
td

---

### Post by CornMaster on 2006-04-10
I'd like to add a note that you have to disconnect and reconnect your device before it will be recognized.

Also...if you get lazy and skip the icon part....you won't realize it is running in the taskbar. ;)

---

### Post by chammi on 2006-04-17
After some digging around in synaptic ("*Conflicts With:libqt3c102-mt, Replaces:libqt3c102-mt*") I, too figured out that the deb package doesn't work. 

But looking over your walk-thru, I was wondering why you use** fakeroot** instead of **sudo **or **su**?  I'm pretty new to Linux, so I know there's a good reason. I just don't understand it yet.

---

### Post by trent dillman on 2006-04-17
Eh, just so the resulting .deb isn't owned by root.

---

### Post by zi99y on 2006-04-26
Trent, thank you so very much for this, I have struggled in the past to get the deb or the source working - the deb tended to work but give you horrid dependency errors every time you use apt-get.

I never have meddled with the alien command, maybe in future I will experiment.

Thanks again, really happy to have this working - with tray icons too.

---

### Post by trent dillman on 2006-05-03
This method also works on Dapper, with the following amendment: you cannot as a user go into /usr/local/share/pixmaps/qjoypad, so the icon fix is as follows:

```
sudo chmod 755 -R /usr/local/share/pixmaps
cd /usr/local/share/pixmaps/qjoypad/
sudo ln -s gamepad2-24x24.png icon24.png
sudo ln -s gamepad2-64x64.png icon64.png

```

---

### Post by crazygerad on 2006-06-04
I am having problems, I first used the joypad and joystick calibration programs and it reads the buttons. I did a cat of the dev and it reads the buttons. I followed your instructions and I get this error when using Qjoypad:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I am using a Saitek  P880 Dual Analog Controller. Any help is aprecciated.

---

### Post by chrism66 on 2006-06-17
Ok, I am a toatal 'Newbie' I can not follow the first instructions. i.e it just doesn't work on 6.06. Are there other commands to get it to work?

---

### Post by chrism66 on 2006-06-17
Ok, da' 'Newbie' figured it out!! i had to install the Alien package and it worked like a dream!! I am so HAPPY now I have joystick support for Quake IV. Life is so great!!!! Thanks all for your previous postings to get me up and running!!

By the way crazygerad, I am getting the same message when I open Qjoypad. Howver it is working just fine.

Chris

---

### Post by dk5151 on 2006-12-02
The program doesn't run automatically for me, when I run it from the terminal it works fine but as soon as I close the terminal qjoystick also closes. I tried adding it to my startup programs also, but then it doesn't start in my tray. Any ideas?

---

### Post by zi99y on 2006-12-02
when you run it in a terminal leave a & on the end of the line and when you exit the terminal it will remain loaded:

qjoypad &

as for the startup it may be loading before the tray gets loaded depending on your WM

---

### Post by Moe-loves-ayumi on 2006-12-27
This how-to worked for me on Edgy Eft with a Playstation Dual Shock controller and a generic convertor. Don't forget to install fakeroot and alien before starting. Thanks.

---

### Post by BobDolesUncle on 2007-02-01
> **CornMaster said:**
> I'd like to add a note that you have to disconnect and reconnect your device before it will be recognized.

Also...if you get lazy and skip the icon part....you won't realize it is running in the taskbar. ;)

Any idea how one might script something to get around this problem so you don't have to manually unplug and replug the device?  I am using Logitech Rumblepad 2 and the analog axis' won't work until you replug the usb transceiver in.

---

### Post by Saubazi on 2007-02-02
I'd like to try this one but I have a problem - my system is 64bit so I get:

$ fakeroot alien qjoypad-3.4-1.i586.rpm 
Warning: Skipping conversion of scripts in package qjoypad: postinst
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/qjoypad
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libqt-mt.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libqt-mt (soname 3, path libqt-mt.so.3, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: qjoypad-3.4: No such file or directory


if someone could upload the i386.deb file I could try a force-architecture... 

I also tried compiling from source. Otherwise ok, except 

$ qjoypad 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by chrism66 on 2007-02-02
Here is the 64 bit version I got from on the net works for my 64bit system

---

### Post by Saubazi on 2007-02-02
Hallelujah, you are the man - it truly worx

---

### Post by TechSupportNoob on 2007-03-25
Okay it seems like everyone else can get this going, so I'm not sure why I'm having so much trouble.

I followed all the instructions, seems to have gone okay.  No where do I find anything to click on to start qjoypad...when I try to run it in terminal under sudo...I get the library error mentioned in the first post, then nothing else.  No icons in the tray [I did that little trick], no window, nothing...ever.

When i try to run from terminal::

tommyboy@Tommy:~$ qjoypad
qjoypad: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

This sucks.

  Why is this so difficult?  Do I have to install that library, and how would I go about doing that?  Wasn't the point of converting the rpm to bypass the library error or am I understanding wrong?

-Tom

---

### Post by TechSupportNoob on 2007-03-25
BUMP!

I'm getting this solved!!!!

---

### Post by matemargo on 2007-07-15
I've follow the instructions and everything is fine. Except that Qjoypad doesn't keep the configuration.

Every time I add a layout it creates a new **.lyt** file in **~/.qjoypad3** but is always empty.
In fact, the only text inside is:
```

# QJoyPad 3.4 Layout File

```

Has anyone this problem?

---

### Post by LJarvis on 2007-07-19
I get this whenever i try to convert the file with alien:
> Warning: Skipping conversion of scripts in package qjoypad: postinst
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `qjoypad-3.4': File exists
mkdir: cannot create directory `qjoypad-3.4/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/qjoypad
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libqt-mt.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libqt-mt (soname 3, path libqt-mt.so.3, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: qjoypad-3.4: No such file or directory

Can anyone help?

---

### Post by JumpmanXXIII on 2007-07-31
proz for this I been looking everywhere to find out how to install the qjoy package

I even tried to unpack, change the control dependency to libqt3 then repack and install it but it didn't work

Thanks

---

### Post by matemargo on 2007-07-31
**LJarvis**: You don't need qjoypad to use ePSXe. You can use padjoy plugin that works very well. 
Get it from here:
[http://www.ngemu.com/psx/plugins.php?cat=1&os=linux](http://www.ngemu.com/psx/plugins.php?cat=1&os=linux)

---

### Post by gaiterin on 2007-08-15
Hi.
I can run it!!! :)
I do, as the first entrie:
sudo apt-get install alien fakeroot
fakeroot alien qjoypad-3.4-1.i586.rpm
sudo dpkg -i qjoypad_3.4-2_i386.deb
cd /usr/local/share/pixmaps/qjoypad/
sudo ln -s gamepad2-24x24.png icon24.png
sudo ln -s gamepad2-64x64.png icon64.png

but the program not works! :(
The solution is (I use Kubuntu 7.04), Alt+F2, and type qjoypad.

---

### Post by fatalfurry on 2007-09-24
> **crazygerad said:**
> I am having problems, I first used the joypad and joystick calibration programs and it reads the buttons. I did a cat of the dev and it reads the buttons. I followed your instructions and I get this error when using Qjoypad:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I am using a Saitek  P880 Dual Analog Controller. Any help is aprecciated.

I also get this error. When I use qjoypad it registers which buttons I press but does not save the configuration.

---

### Post by AaronSells on 2007-11-12
I was also getting the qjoypad behavior where gamepad key presses were being registered, but mapped keys would not save.  I worked around this by tabbing over such that the "update" button was in focus.  I was able to save my key mappings after I did this.

---

### Post by Ferrat on 2007-11-12
Well got qjoypad to work but WTF! 55-75% usage of CPU even in idle mode?

---

### Post by Ferrat on 2007-11-12
Well got it working but still looks like alot of CPU

---

### Post by radu_radu on 2007-11-17
There's a fix for that CPU problem: go to a file called loop.cpp that can be found in src/, and search for some lines that says:
```

        //sleep for a moment. This is just to keep us from throwing all the
        //available processer power into madly checking for new events.
        usleep(1);

```
it's around the middle of the file.
Modify usleep(1) into usleep(10000), save and recompile.
The solution was take from [[COLOR="Blue"]_here_[/COLOR]]("http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100") (it's in French, and the patch failed on me, so I had to modify by hand).
It works for me, that's all i can say. Before it would take between 75 - 85% of my CPU, now it takes less than 1%.

---

### Post by tuesday20102001 on 2007-11-26
to everyone who was as frustrated as me i hope this helps:
The source code is available here: [http://sourceforge.net/project/showfiles.php?group_id=98952](http://sourceforge.net/project/showfiles.php?group_id=98952)
(contrary to what the site says, sent maintainer of qjoypad a email about the broken link).
Also noted I reduce the processor speed in the setup (posted previously in this post). To all others finding that their configuration is not saving, you can modify the file and change it accordingly (mine was located in /home/username/.qjoypad3)Notice the dot in front of the file name which means it's hidden (can find it with ls -a command). I previously had my controller configuration saved from earlier on joystick 2 so i opened the file and copied it to joystick one: (filename:wolfenstein.lyt)

 # QJoyPad 3.4 Layout File

Joystick 1 {
        Axis 1: gradient, maxSpeed 30, mouse+h
        Axis 2: gradient, maxSpeed 10, mouse+v
        Axis 3: gradient, maxSpeed 10, mouse+h
        Axis 4: gradient, maxSpeed 10, mouse+v
        Button 5: mouse 4
        Button 6: key 27
        Button 7: mouse 5
        Button 8: rapidfire, key 41
        Button 13: key 25
        Button 14: key 40
        Button 15: key 39
        Button 16: key 38
}

#end of file

I was hoping someone would post a standard 101 keyboard number layout in the futre to cut the extra step out and just edit the file (.lyt).

---

### Post by skychris on 2007-12-17
Hi all,

I've managed to install Qjoypad on Gutsy using the different tips in this post but when I want to configure it, it only allows me to link one keyboard key to one button. 
But I would like to assign a combination of key, like "Ctrl + T", to a button, is it possible or am I missing something here ?:)

Chris

---

### Post by tuesday20102001 on 2008-01-12
I have seen this done previously with other key to joystick programs (joytokey). I am sure this would be possible with this program. Might need to alter the program. Might want to send this suggestion to the developer located on this site: [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

Even though the program isn't updated often, I still think its a start for us. Much appreciative Nathan Gaylinn, Thanks.

---

### Post by Maxiom on 2008-03-13
As far as I know Nathan is not developing this program anymore though I think he will answer the odd polite question via E-Mail

I have not bothered him yet. What I would like to know is....

Okay this program can produce physical KEY code output as default. This is great in a lot of cases however, what about the modifier keys?

Is there a command line switch to allow or force system code outputs?
 as in (Shift+1) = ! not as it stands right now as (Shift+1) = (Shift)

---

### Post by Maulwuff on 2008-06-01
I managed to compile the sources from:
[http://sourceforge.net/project/showfiles.php?group_id=98952&package_id=106031&release_id=460265](http://sourceforge.net/project/showfiles.php?group_id=98952&package_id=106031&release_id=460265)

modify the loop.cpp on line 34 first! 
change 
usleep(1) to
usleep(100).
10000, like mentioned earlier, was far too much for me.

to get rid from error: /usr/bin/ld: cannot find -lXtst
install libxtst-dev

i am on gutsy.

---

### Post by BryanFRitt on 2008-07-09
about line 34 in /joypad-3.4.1/src/loop,cpp
usleep(XXXX), where XXXX is in microseconds(10^-6)
[http://linux.die.net/man/3/usleep](http://linux.die.net/man/3/usleep)
[http://en.wikipedia.org/wiki/Microsecond](http://en.wikipedia.org/wiki/Microsecond)

most monitors are 60-120Hz. Doubling it, just because of some analog to digital rule I heard of (not that it really applies here(or does it?))  and then doubling it again for the heck of it, followed by dividing by ((10^-6)_s).  Mines 60Hz so 240Hz, (1_s/240) divide that by ((10^-6)_s) and get 4166+2/3 take the integer part of that number and get 4166.  That's the number I'm trying first.

p.s. I'm on 8.04_64_KUbuntu (not that it matters)
-
Tried it out(4166), according to KDE System Guard, afterwards for qjoypad CPU usage went down to about 0% most of the time, maxing out at around 1.00% User and 1.00% System.
-
2.2GHz Intel Dual Core 2, 64 bit, 8.04 KUbuntu

-

The default USB data rate is 125Hz(but some overclock to 1000Hz), (1_s/125)/((10^-6)_s)=8000, so maybe the ideal setting (for USB joysticks) would be 8000-X, where X is the maximum time in microseconds it takes for this program to do its thing.  Anybody know how to find X?

---

### Post by crazyfuturamanoob on 2008-11-03
```
arho@ohra-laptop:~$ qjoypad
bash: qjoypad: command not found
arho@ohra-laptop:~$ 

```
How can I make it so when I type qjoypad it runs qjoypad?

I downloaded and installed the source rpm with your instructions.
Also, I had no idea where to get the icons to link, so I made some.
And I didn't have that pixmaps or qjoypad folder in my /usr/local/share.

---

### Post by Siggma on 2009-05-08
Ya know yall don't need to do anything fancy to compile this program. The dependencies were just renamed.

See: [http://ubuntuforums.org/showthread.php?t=1147506](http://ubuntuforums.org/showthread.php?t=1147506)

This works for jaunty and probably Interepid and Hardy.

```
sudo apt-get install build-essential qt3-dev-tools libxtst-dev joystick jscalibrator
```

Then compile it normally.

Thanks for the loop.cp mod. If I can figure out the correct checkinstall syntax I'll make a working x64 deb and post it, along with the syntax for making a working x32 deb so one of you kind folks can post one of them.

-Tom

---

### Post by Perfect Storm on 2009-05-08
Can you start a new thread about this? Then I can close this really old thread. (with staff blessing ofcause).


regards
A.I. Dude
Ubuntu Forum Staff

---

