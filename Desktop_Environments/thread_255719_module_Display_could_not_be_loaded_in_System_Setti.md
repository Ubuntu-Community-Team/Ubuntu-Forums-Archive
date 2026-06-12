---
title: "module Display could not be loaded in System Settings &gt; Display in Kubuntu"
date: 2006-09-11
forum: Desktop Environments
---

### Post by rordog on 2006-09-11
When I go to System Settings and click on Display, I get the error "The module Display could not be loaded"

This is the output from "kcmshell displayconfig"

Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 1677, in create_displayconfig

return DisplayApp(parent, name)
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 443, in __init__

self.xsetup = XSetup(self.xconfigpath)
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 156, in __init__

xorg_unused_device_sections.remove(device_section)
ValueError
:
list.remove(x): x not in list

error: *** runFunction failure


Any ideas? I've googled this to death. I suspect it might be a problem with my xorg.conf settings, but other people have suggested that its broken packages and I need to re-install a bunch of stuff. I'm at a loss.

---

### Post by gerdt on 2006-09-26
Hi,
I have the (exact?) same problem.
When I go to System Settings > Display, this message shows up:
```
The module Display could not be loaded

The diagnostics is:

Possible reasons:

An error occured during your last KDE upgrade, leaving an orphaned module.
You have old third party modules laying around.

Check these points carefully and try to remove the module mentioned in the error message. If this fails, consider contacting your distributor or packager.
```

When I log in as administrator, the window stays empty.
I've been googling around some time, but I can't find the answer.
I found an older thread on this forum, which is closed btw: [http://ubuntuforums.org/showthread.php?t=166753]("http://ubuntuforums.org/showthread.php?t=166753")
But no answer to the problem can be found. 
I would really like to have an answer, as I cannot modify anything now and my screen is running below 60Hz, which is very irritating to my eyes :-? 

I believe this problem started when I was playing around with a second monitor. Somewhere along the way I achieved that, but I left the Display section within the System Settings a little bit mixed up as you can see... My laptop, which has the exact same distribution, version, etc. and almost the same programs installed, does not have this problem.
I believe it is just removing/reinstalling/loading this or another module, but I don't know which module it is.
Could someone please help me out?!? I'd really apreciate it. 
Thanx in advance,
Gerard

---

### Post by gerdt on 2006-09-26
BTW, this is the only problem I have with my desktopcomputer. Everythink else works perfectly.

This is the output of "sudo kcmshell displayconfig":
```

user@COMPUTER:~$ sudo kcmshell displayconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.


Pythonize constructor -- pid = 1845
Python interpreter initialized!



Pythonize constructor -- pid = 1845
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 1677, in create_displayconfig
    return DisplayApp(parent, name)
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 439, in __init__
    self.xf86server = xf86misc.XF86Server()
  File "/usr/lib/python2.4/site-packages/xf86misc.py", line 97, in __init__
    raise XF86Error, "Couldn't connect to X server."
xf86misc.XF86Error: Couldn't connect to X server.
error: *** runFunction failure
;

```

---

### Post by tonyr on 2006-10-20
Try re-installing package **kde-guidance**.  It worked for me.

```
sudo apt-get install --reinstall kde-guidance
```
or
```
sudo aptitude reinstall kde-guidance
```

---

### Post by mexlinux on 2006-10-21
Aren't you using XGL?

---

### Post by ulriks on 2006-11-04
I encountered the same problem (as well as another one, see [http://ubuntuforums.org/showthread.php?t=285223]("http://ubuntuforums.org/showthread.php?t=285223")) after upgrading the nvidia-glx.

Running
```

sudo apt-get install --reinstall kde-guidance

```

Did the trick

Ofcourse everythinbg crashed when my screen saver ([Electric Sheep]("http://electricsheep.org/")) started ](*,)

---

### Post by michaelphipps on 2006-11-22
[QUOTE=tonyr;1642388]Try re-installing package **kde-guidance**.  

```
sudo apt-get install --reinstall kde-guidance
```

I can also confirm it worked for me as well.

Just as a side note:

This is the longest I've been able to keep running ubuntu / kubuntu without resorting to rebooting my windows drive.  So I'm very happy.  It'd be nice if these little things didn't keep popping up - I know it is definately causing more casual computer users to shy away from adopting a linux platform as their main OS.

---

### Post by gerdt on 2006-11-22
I finally got to solve my problem:
After a lot of trying, I figured out that my monitor was running on the wrong frequencies. Apparantly that's why the module couldn't be loaded.
So I changed the resolution and the frequency manually in xorg.conf and when I changed it back to a lower frequency the module Display suddenly worked again.
So, if you think you have the same problem as I had, figure out the real specs about your monitor, and change the xorg.conf file.

---

### Post by esaym on 2006-12-17
I got the same problem too, just happened today for no reason



```

user@user-desktop:~$ displayconfig
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/bin/displayconfig", line 1699, in ?
    displayapp = DisplayApp()
  File "/usr/bin/displayconfig", line 443, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 73, in __init__
    self.xorg_config = xorgconfig.readConfig(xorg_config_filename)
  File "/usr/lib/python2.4/site-packages/xorgconfig.py", line 657, in readConfig
    raise ParseException,"Unknown line type '%s' on line %i" % (first,line)
xorgconfig.ParseException: Unknown line type 'section' on line 97
user@user-desktop:~$

```

reinstalling guidance  does nothing :(

---

### Post by viz_e on 2007-03-30
Same problem here.

---

### Post by esaym on 2007-03-30
That sucks, I had to do a reinstall

---

