---
title: "Read raw data from USB port"
date: 2009-05-18
forum: General Help
---

### Post by Vined Adobo on 2009-05-18
Hi all,

Background:  I have a CMS 50e pulse oximeter which I need to use for sleep studies to tell, while sleeping, when my  percent of oxygen gets too low,  how low it gets, and how many events below 87% saturation occur.  I desperately wish to discontinue my nighttime oxygen use through dieting and exercizing.  To do this, I must do periodic sleep studies.

Obstacle: the pulse oximeter will record up to 24 hours of data which uploads to my laptop through a USB connection.  The software is poorly engineered, almost impossible to install (drivers try to install over other devices in use,) and contains sorely deficient documentation.  The data is still uploading when the software generates its report, so report suddenly stops at random amounts of data.  Searching on the internet, I have discovered that this is a common (universal?) problem

Hopeful workaround:  The data is stored in CSV format.  If I could capture data stream for entire upload, I could import it into Open Office and create my own accurate report.  The longest report my software generates has been 5 hours of sleep.


Question (finally!):  Does anyone know how to capture a raw USB stream?  Here is what I have so far:

rumrunner@FUSION-UBUNTU:/dev$ lsusb
Bus 001 Device 002: ID 5986:0100 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rumrunner@FUSION-UBUNTU:/dev$ 

The Cygnal Integrated Products port is what I want to capture

rumrunner@FUSION-UBUNTU:/etc$ sudo mount /dev/sda1 /mnt/USB
rumrunner@FUSION-UBUNTU:/etc$ cd /mnt/USB

# At this point, I uploaded the data from the SPO2#

rumrunner@FUSION-UBUNTU:/mnt/USB$ ls -la
drwxrwxrwx 1 root root   8192 2008-10-05 01:48 .
drwxr-xr-x 3 root root   4096 2009-05-18 13:44 ..
-rwxrwxrwx 1 root root    490 2005-09-29 02:35 ACERBP.P2
-rwxrwxrwx 1 root root     29 2007-09-27 14:36 aimdrs.dat
drwxrwxrwx 1 root root      0 2007-06-04 00:13 AUTORUN
-rwxrwxrwx 1 root root    356 2005-07-14 23:25 BACKUP.NAP
drwxrwxrwx 1 root root      0 2007-06-04 00:13 BitLocker
-rwxrwxrwx 1 root root  37376 2005-07-29 18:13 BOOT.DAT
drwxrwxrwx 1 root root      0 2007-06-04 00:13 D2D
-rwxrwxrwx 1 root root 888832 2006-12-22 01:42 D2D32.EXE
-rwxrwxrwx 2 root root     78 2007-06-04 15:34 DrAssign2C.ini
drwxrwxrwx 1 root root      0 2007-06-04 15:34 FACTORY
-rwxrwxrwx 1 root root   6656 2005-06-27 10:28 FATBOOT.BIN
-rwxrwxrwx 1 root root    153 2005-12-15 03:12 FmtFAT32.INI
-rwxrwxrwx 1 root root  69632 2003-09-30 23:29 int15.sys
-rwxrwxrwx 1 root root    512 2005-06-25 20:49 MBR.BIN
drwxrwxrwx 1 root root   4096 2007-06-04 00:12 Minint
-rwxrwxrwx 1 root root   1359 2006-11-12 02:57 model.dat
-rwxrwxrwx 1 root root     67 2006-09-16 02:18 NAPP.DAT
-rwxrwxrwx 2 root root    302 2007-06-04 15:23 NewPartDisk.ini
-rwxrwxrwx 1 root root  47772 2005-03-25 05:00 ntdetect.com
-rwxrwxrwx 1 root root 298096 2005-03-25 05:00 ntldr
-rwxrwxrwx 1 root root    230 2007-06-04 15:58 OBR3.acr
-rwxrwxrwx 1 root root     70 2005-09-12 09:20 OBR3.ini
-rwxrwxrwx 1 root root     11 2005-07-07 20:31 P1.DAT
-rwxrwxrwx 2 root root    125 2005-12-28 20:12 PARTITION.ALL
drwxrwxrwx 1 root root      0 2006-11-02 03:22 ProgramData
drwxrwxrwx 1 root root      0 2006-11-02 03:23 Program Files
-rwxrwxrwx 1 root root    207 2007-04-10 04:58 RCD.DAT
-rwxrwxrwx 2 root root    382 2005-12-19 06:54 RestoreFAT32.INI
drwxrwxrwx 1 root root  12288 2007-06-04 00:13 RYTOOLS
-rwxrwxrwx 1 root root    116 2007-04-27 08:37 SCD.DAT
drwxrwxrwx 1 root root      0 2006-11-11 03:50 sources
-rwxrwxrwx 1 root root     80 2007-04-27 03:10 SWCD.DAT
drwxrwxrwx 1 root root   4096 2007-06-04 15:41 System Volume Information
-rwxrwxrwx 1 root root 131072 2005-08-23 20:02 UNICODE.BIN
drwxrwxrwx 1 root root      0 2006-11-02 03:22 Users
drwxrwxrwx 1 root root   8192 2008-08-31 03:30 Windows
rumrunner@FUSION-UBUNTU:/mnt/USB$ 


Can anyone help me out from here?

Thank you,
David Boone

---

### Post by sambaig on 2009-07-09
> **Vined Adobo said:**
> Hi all,

Background:  I have a CMS 50e pulse oximeter which I need to use for sleep studies to tell, while sleeping, when my  percent of oxygen gets too low,  how low it gets, and how many events below 87% saturation occur.  I desperately wish to discontinue my nighttime oxygen use through dieting and exercizing.  To do this, I must do periodic sleep studies.

Obstacle: the pulse oximeter will record up to 24 hours of data which uploads to my laptop through a USB connection.  The software is poorly engineered, almost impossible to install (drivers try to install over other devices in use,) and contains sorely deficient documentation.  The data is still uploading when the software generates its report, so report suddenly stops at random amounts of data.  Searching on the internet, I have discovered that this is a common (universal?) problem

Hopeful workaround:  The data is stored in CSV format.  If I could capture data stream for entire upload, I could import it into Open Office and create my own accurate report.  The longest report my software generates has been 5 hours of sleep.


Question (finally!):  Does anyone know how to capture a raw USB stream?  Here is what I have so far:

rumrunner@FUSION-UBUNTU:/dev$ lsusb
Bus 001 Device 002: ID 5986:0100 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rumrunner@FUSION-UBUNTU:/dev$ 

The Cygnal Integrated Products port is what I want to capture

rumrunner@FUSION-UBUNTU:/etc$ sudo mount /dev/sda1 /mnt/USB
rumrunner@FUSION-UBUNTU:/etc$ cd /mnt/USB

# At this point, I uploaded the data from the SPO2#

rumrunner@FUSION-UBUNTU:/mnt/USB$ ls -la
drwxrwxrwx 1 root root   8192 2008-10-05 01:48 .
drwxr-xr-x 3 root root   4096 2009-05-18 13:44 ..
-rwxrwxrwx 1 root root    490 2005-09-29 02:35 ACERBP.P2
-rwxrwxrwx 1 root root     29 2007-09-27 14:36 aimdrs.dat
drwxrwxrwx 1 root root      0 2007-06-04 00:13 AUTORUN
-rwxrwxrwx 1 root root    356 2005-07-14 23:25 BACKUP.NAP
drwxrwxrwx 1 root root      0 2007-06-04 00:13 BitLocker
-rwxrwxrwx 1 root root  37376 2005-07-29 18:13 BOOT.DAT
drwxrwxrwx 1 root root      0 2007-06-04 00:13 D2D
-rwxrwxrwx 1 root root 888832 2006-12-22 01:42 D2D32.EXE
-rwxrwxrwx 2 root root     78 2007-06-04 15:34 DrAssign2C.ini
drwxrwxrwx 1 root root      0 2007-06-04 15:34 FACTORY
-rwxrwxrwx 1 root root   6656 2005-06-27 10:28 FATBOOT.BIN
-rwxrwxrwx 1 root root    153 2005-12-15 03:12 FmtFAT32.INI
-rwxrwxrwx 1 root root  69632 2003-09-30 23:29 int15.sys
-rwxrwxrwx 1 root root    512 2005-06-25 20:49 MBR.BIN
drwxrwxrwx 1 root root   4096 2007-06-04 00:12 Minint
-rwxrwxrwx 1 root root   1359 2006-11-12 02:57 model.dat
-rwxrwxrwx 1 root root     67 2006-09-16 02:18 NAPP.DAT
-rwxrwxrwx 2 root root    302 2007-06-04 15:23 NewPartDisk.ini
-rwxrwxrwx 1 root root  47772 2005-03-25 05:00 ntdetect.com
-rwxrwxrwx 1 root root 298096 2005-03-25 05:00 ntldr
-rwxrwxrwx 1 root root    230 2007-06-04 15:58 OBR3.acr
-rwxrwxrwx 1 root root     70 2005-09-12 09:20 OBR3.ini
-rwxrwxrwx 1 root root     11 2005-07-07 20:31 P1.DAT
-rwxrwxrwx 2 root root    125 2005-12-28 20:12 PARTITION.ALL
drwxrwxrwx 1 root root      0 2006-11-02 03:22 ProgramData
drwxrwxrwx 1 root root      0 2006-11-02 03:23 Program Files
-rwxrwxrwx 1 root root    207 2007-04-10 04:58 RCD.DAT
-rwxrwxrwx 2 root root    382 2005-12-19 06:54 RestoreFAT32.INI
drwxrwxrwx 1 root root  12288 2007-06-04 00:13 RYTOOLS
-rwxrwxrwx 1 root root    116 2007-04-27 08:37 SCD.DAT
drwxrwxrwx 1 root root      0 2006-11-11 03:50 sources
-rwxrwxrwx 1 root root     80 2007-04-27 03:10 SWCD.DAT
drwxrwxrwx 1 root root   4096 2007-06-04 15:41 System Volume Information
-rwxrwxrwx 1 root root 131072 2005-08-23 20:02 UNICODE.BIN
drwxrwxrwx 1 root root      0 2006-11-02 03:22 Users
drwxrwxrwx 1 root root   8192 2008-08-31 03:30 Windows
rumrunner@FUSION-UBUNTU:/mnt/USB$ 


Can anyone help me out from here?

Thank you,
David Boone


I am trying to same. Were you able to load data?

Sam Baig
1-281-935-3171
[email]sbaig04@yahoo.com[/email]

---

### Post by HermanAB on 2009-07-09
Howdy,

I would plug the device in and see with 'dmesg' whether it is recognized as a device.  If so, confirm the device name in /dev then simply use 'cat' to dump data from the device to a file and then look at it with 'hexeditor'.

# dmesg
... device xxx ...
# ls /dev/xxx*
...
xxx1
...
# cat /dev/xxx1 > filename
...long wait...
ctrl-d
# hexedit filename

Hope that helps!

---

### Post by Vined Adobo on 2009-08-07
> **sambaig said:**
> I am trying to same. Were you able to load data?

Sam Baig
1-281-935-3171
[EMAIL="sbaig04@yahoo.com"]sbaig04@yahoo.com[/EMAIL]


I was able to see it with the dmesg command These were the extra lines added at the bottom when the device was plugged in:

[ 1262.676089] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 1262.838749] usb 5-1: configuration #1 chosen from 1 choice
[ 1263.149567] usbcore: registered new interface driver usbserial
[ 1263.149602] USB Serial support registered for generic
[ 1263.149665] usbcore: registered new interface driver usbserial_generic
[ 1263.149671] usbserial: USB Serial Driver core
[ 1263.601896] USB Serial support registered for cp2101
[ 1263.601951] cp2101 5-1:1.0: cp2101 converter detected
[ 1263.712081] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[ 1263.862265] usb 5-1: cp2101 converter now attached to ttyUSB0
[ 1263.862302] usbcore: registered new interface driver cp2101
[ 1263.862309] cp2101: v0.07:Silicon Labs CP2101/CP2102 RS232 serial adaptor driver

The only thing that changed in /dev was ttyUSB0 being added.
I typed cat ttyUSB0 > /home/dave/spo2.  The cursor went into wait just as advertised.  After the upload was completed,  I unplugged the device and the cursor came back.  A file titled spo was made in my home directory, but the file was empty. :confused:   I never got it working on Vista, and it doesn't work in WINE installed as an XP either.  I guess I was lucky to get it running in windows XP.
Back to the drawing board.

---

### Post by Vined Adobo on 2009-11-13
bump

---

### Post by t4thfavor on 2010-01-28
Any news on this, if you have a device, and the file was created, then it is possible. Maybe post the file so that others can analyze the format, maybe you got yourself a new FOSS project.

---

### Post by HermanAB on 2010-01-28
Howdy,

It looks like you need to install the USB Serial driver and then dump /dev/usb/ttyUSB0 or some such to a file using cat.

---

### Post by rnerwein on 2010-01-28
hi 
the cat command coudn't work because cat is reading from stdion. ( it's possible to use cat but cat is not designed to
handle raw data.
1. figure out your mount point of the usb: mout command will show you the stuff.
2. if your usb is mounted on /dev/sdX (X is your divice) use dd this works !
--> dd if=/dev/sdX of=/your_path/your_file bs=4k
in your file you will have now a exact copy of your usb data
ciao

---

### Post by iphands on 2010-02-07
Vined Adobo, sambaig,

My father has one of these devices. I hooked it up to his laptop yesterday, and found that the provided software did not work under wine.

I hacked together my own Java + SWT over the past couple of days (it is really poorly written at this point.. will clean up and add features soon).

I have attached a pic.

Also the code should be attainable, buildable, and runnable by following this procedure:
```
$ git clone [http://github.com/iphands/PulseOx.git](http://github.com/iphands/PulseOx.git)
$ cd PulseOx/workspace/PulseOx/
$ mkdir -p jars ; cp /path_to_your_swt.jar ./jars
$ ant
$ java -jar pulseox.jar
```


Please let me know if this does or does not work for you. I am not running ubuntu, but java is java :-) (though SWT is platform specific).

Oh and for the moment the /dev/ttyUSB0 path is hard coded.

Thanks,
-Ian Page Hands

edit:
See my website for up to date information [http://ian.ahands.org/progs/pulseox/](http://ian.ahands.org/progs/pulseox/)

---

### Post by Vined Adobo on 2010-04-21
> **iphands said:**
> Vined Adobo, sambaig,

My father has one of these devices. I hooked it up to his laptop yesterday, and found that the provided software did not work under wine.

I hacked together my own Java + SWT over the past couple of days (it is really poorly written at this point.. will clean up and add features soon).

I have attached a pic.

Also the code should be attainable, buildable, and runnable by following this procedure:
```
$ git clone [http://github.com/iphands/PulseOx.git](http://github.com/iphands/PulseOx.git)
$ cd PulseOx/workspace/PulseOx/
$ mkdir -p jars ; cp /path_to_your_swt.jar ./jars
$ ant
$ java -jar pulseox.jar
```
Please let me know if this does or does not work for you. I am not running ubuntu, but java is java :-) (though SWT is platform specific).

Oh and for the moment the /dev/ttyUSB0 path is hard coded.

Thanks,
-Ian Page Hands

edit:
See my website for up to date information [http://ian.ahands.org/progs/pulseox/](http://ian.ahands.org/progs/pulseox/)


It went well for me until I got to: 
$ mkdir -p jars ; cp /path_to_your_swt.jar ./jars

I did it in two steps instead of both on the same command line.  The directory was made, but when I used cp /path_to_your_swt.jar ./jars, I got the following:

 [:~/PulseOx/workspace/PulseOx] $ cp /usr/share/jni ./jars
cp: omitting directory `/usr/share/jni'

Now I have to admit I am not proficient at Linux systems, so I don't even really know if I got the path right (although the library liibswt-gtk-3452.so  is in the directory listed.  Also, I can't find where any link was created. When I typed ant, I got 100 errors.  I hope you can help.  I'm getting closer anyway!


thank you,
Dave

---

### Post by iphands on 2010-04-21
> **Vined Adobo said:**
> It went well for me until I got to: 
$ mkdir -p jars ; cp /path_to_your_swt.jar ./jars

I did it in two steps instead of both on the same command line.  The directory was made, but when I used cp /path_to_your_swt.jar ./jars, I got the following:

 [:~/PulseOx/workspace/PulseOx] $ cp /usr/share/jni ./jars
cp: omitting directory `/usr/share/jni'

Now I have to admit I am not proficient at Linux systems, so I don't even really know if I got the path right (although the library liibswt-gtk-3452.so  is in the directory listed.  Also, I can't find where any link was created. When I typed ant, I got 100 errors.  I hope you can help.  I'm getting closer anyway!


thank you,
Dave

Dave,

Yeah the instructions are kind of vague on purpose... I am not actually a ubuntu user atm.

Basically you have to simply copy (or symlink) two java Jars (they will have a .jar extension... not .so) to the workspace/PulseOx/jars/ directory.

I do:
$ cd workspace/PulseOx/jars/
$ ln -s /usr/share/java/log4j.jar .
$ ln -s /usr/share/java/swt.jar .

But you could copy them:
$ cd workspace/PulseOx/jars/
$ cp /usr/share/java/log4j.jar .
$ cp /usr/share/java/swt.jar .



The path to the .jar files might be different on ubuntu. You can try to find them by running:
$ locate -r log4j*jar
$ locate -r swt*jar

Or:
$ find / -name 'swt*jar'
$ find / -name 'log4j*jar'

Let me know if you have any trouble with it after these files are in place... I think I had to set the character device in 19200 baud manually sometimes (I dont actually have the pulseOx hardware).

I think you can set the buad rate like:
# stty -F /dev/ttyUSB0 19200
(replace /dev/ttyUSB0 with the device name of the pulseOx char device)

Also the user might need read/write permissions (maybe read only??) to the usb device.

Like:
# chmod 777 /dev/ttyUSB0
(replace /dev/ttyUSB0 with the device name of the pulseOx char device)

Peace,
-Ian Page Hands

---

### Post by Vined Adobo on 2010-04-22
> **iphands said:**
> Vined Adobo, sambaig,

My father has one of these devices. I hooked it up to his laptop yesterday, and found that the provided software did not work under wine.

I hacked together my own Java + SWT over the past couple of days (it is really poorly written at this point.. will clean up and add features soon).

I have attached a pic.

Also the code should be attainable, buildable, and runnable by following this procedure:
```
$ git clone [http://github.com/iphands/PulseOx.git](http://github.com/iphands/PulseOx.git)
$ cd PulseOx/workspace/PulseOx/
$ mkdir -p jars ; cp /path_to_your_swt.jar ./jars
$ ant
$ java -jar pulseox.jar
```
Please let me know if this does or does not work for you. I am not running ubuntu, but java is java :-) (though SWT is platform specific).

Oh and for the moment the /dev/ttyUSB0 path is hard coded.

Thanks,
-Ian Page Hands

edit:
See my website for up to date information [http://ian.ahands.org/progs/pulseox/](http://ian.ahands.org/progs/pulseox/)


Ah, I went to your website and found

$ git clone [http://github.com/iphands/PulseOx.git](http://github.com/iphands/PulseOx.git)
		$ cd PulseOx/workspace/PulseOx/
		$ mkdir -p jars
		$ ln -s /path_to_your_swt.jar ./jars/
		$ ln -s /path_to_your_log4j.jar ./jars/
		$ ant
		$ java -jar pulseox.jar

So now the links do appear in the jars directory.  Now when I build, I get 42 errors.  At least now I know I didn't have the one link I thought I did.  Do I have to install apache or something?

dave@METROPOLIS:~/PulseOx/workspace/PulseOx$ ant
Buildfile: build.xml

compile:
    [javac] Compiling 9 source files to /home/dave/PulseOx/workspace/PulseOx/bin
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:11: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:26: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.FileListener
    [javac]     Logger logger = Logger.getLogger(FileListener.class);
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:8: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.ConsoleAppender;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:9: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.FileAppender;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:10: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Layout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:11: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Level;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:12: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:13: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.PatternLayout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:14: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.SimpleLayout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:41: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Logger logger = Logger.getLogger(LoggingListener.class);
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:46: cannot find symbol
    [javac] symbol  : class Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level fileLevel = Level.INFO;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:47: cannot find symbol
    [javac] symbol  : class FileAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     FileAppender fileAppender = null;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:50: cannot find symbol
    [javac] symbol  : class Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level consoleLevel = Level.DEBUG;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:51: cannot find symbol
    [javac] symbol  : class ConsoleAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     final ConsoleAppender consoleAppender = new ConsoleAppender(
    [javac]           ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:4: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Level;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:5: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:31: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]     static Logger logger = Logger.getLogger(TestGUI.class);
    [javac]            ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:26: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.FileListener
    [javac]     Logger logger = Logger.getLogger(FileListener.class);
    [javac]                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:41: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Logger logger = Logger.getLogger(LoggingListener.class);
    [javac]                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:46: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level fileLevel = Level.INFO;
    [javac]                       ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:50: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level consoleLevel = Level.DEBUG;
    [javac]                          ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:51: cannot find symbol
    [javac] symbol  : class ConsoleAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     final ConsoleAppender consoleAppender = new ConsoleAppender(
    [javac]                                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:52: cannot find symbol
    [javac] symbol  : class SimpleLayout
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]             new SimpleLayout());
    [javac]                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:148: cannot find symbol
    [javac] symbol: class Logger
    [javac]                 Logger rootLogger = Logger.getRootLogger();
    [javac]                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:148: cannot find symbol
    [javac] symbol: variable Logger
    [javac]                 Logger rootLogger = Logger.getRootLogger();
    [javac]                                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:164: cannot find symbol
    [javac] symbol: class Layout
    [javac]                         Layout fileLayout = new PatternLayout("%m\n");
    [javac]                         ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:164: cannot find symbol
    [javac] symbol: class PatternLayout
    [javac]                         Layout fileLayout = new PatternLayout("%m\n");
    [javac]                                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:167: cannot find symbol
    [javac] symbol: class FileAppender
    [javac]                             fileAppender = new FileAppender(fileLayout,
    [javac]                                                ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:294: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.DEBUG;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:296: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.INFO;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:298: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.WARN;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:300: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.ERROR;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:302: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.FATAL;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:376: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.DEBUG;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:378: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.INFO;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:380: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.WARN;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:382: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.ERROR;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:384: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.FATAL;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:31: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]     static Logger logger = Logger.getLogger(TestGUI.class);
    [javac]                            ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:285: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         final Logger rootLogger = Logger.getRootLogger();
    [javac]               ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:285: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         final Logger rootLogger = Logger.getRootLogger();
    [javac]                                   ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:286: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         rootLogger.setLevel(Level.DEBUG);
    [javac]                             ^
    [javac] 42 errors

BUILD FAILED
/home/dave/PulseOx/workspace/PulseOx/build.xml:12: Compile failed; see the compiler error output for details.

Total time: 1 second

Thank you for your help.
Dave

---

### Post by iphands on 2010-04-22
> **Vined Adobo said:**
> Ah, I went to your website and found

$ git clone [http://github.com/iphands/PulseOx.git](http://github.com/iphands/PulseOx.git)
		$ cd PulseOx/workspace/PulseOx/
		$ mkdir -p jars
		$ ln -s /path_to_your_swt.jar ./jars/
		$ ln -s /path_to_your_log4j.jar ./jars/
		$ ant
		$ java -jar pulseox.jar

So now the links do appear in the jars directory.  Now when I build, I get 42 errors.  At least now I know I didn't have the one link I thought I did.  Do I have to install apache or something?

dave@METROPOLIS:~/PulseOx/workspace/PulseOx$ ant
Buildfile: build.xml

compile:
    [javac] Compiling 9 source files to /home/dave/PulseOx/workspace/PulseOx/bin
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:11: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:26: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.FileListener
    [javac]     Logger logger = Logger.getLogger(FileListener.class);

...

BUILD FAILED
/home/dave/PulseOx/workspace/PulseOx/build.xml:12: Compile failed; see the compiler error output for details.

Total time: 1 second

Thank you for your help.
Dave



Yeah it looks like you got the swt.jar in the right place, but not the log4j.jar. You don't have to install "apache" the web server. But the group/entity Apache does write/maintain the log4j package, and you likely have to install that package.

Can you show me what the libs/ dir looks like?
$ ls -lh libs/

You can probably find the log4j package in your distro by doing:
# apt-cache search log4j

or something... it has been a while since I last used apt*.

---

### Post by Vined Adobo on 2010-04-22
> **iphands said:**
> Yeah it looks like you got the swt.jar in the right place, but not the log4j.jar. You don't have to install "apache" the web server. But the group/entity Apache does write/maintain the log4j package, and you likely have to install that package.

Can you show me what the libs/ dir looks like?
$ ls -lh libs/

You can probably find the log4j package in your distro by doing:
# apt-cache search log4j

or something... it has been a while since I last used apt*.

This is what I got:

dave@METROPOLIS:~/PulseOx/workspace/PulseOx/jars$ ls -lh
total 0
lrwxrwxrwx 1 dave dave 13 2010-04-21 21:35 java -> /usr/lib/java
lrwxrwxrwx 1 dave dave 18 2010-04-22 15:21 lib -> /usr/share/ant/lib

When I run gnome-search-tool, I get 
    ant-apache-log4j.jar /usr/share/ant/lib 3.0 KB link to Java archive
    ant-apache-log4j.jar /usr/share/java 3.0 KB link to Java archive
The first link in turn points to a link to: Link target  ../../java/ant-apache-log4j-1.7.1.jar
The second link points to: Link target ant-apache-log4j-1.7.1.jar (I can't use second link because the link to /usr/lib/java already uses java as its name to link to swt, so if i make a link to /usr/share/java, I get a complaint that the link already exists, even though it points to a different place.)

dave@METROPOLIS:~$ apt-cache search log4j
libexcalibur-logkit-java - Lightweight and fast designed logging toolkit for Java
liblog4j1.2-java - Logging library for java
liblog4j1.2-java-doc - Documentation for liblog4j1.2-java
liblog4j1.2-java-gcj - Logging library for java (native code)
liblog4net1.2-cil - highly configurable logging API for the CLI
liblogkit-java - Lightweight and fast designed logging toolkit for Java
libslf4j-java - Simple Logging Facade for Java
cl-arnesi - small Common Lisp utilities
libjboss-common-java - The JBoss Common Project
liblog-log4perl-perl - A Perl port of the widely popular log4j logging package.
liblog4cpp-doc - A C++ library for flexible logging (documentation)
liblog4cpp5 - C++ library for flexible logging (runtime)
liblog4cpp5-dev - C++ library for flexible logging (development)
liblog4cxx10 - A logging library for C++
liblog4cxx10-dev - A logging library for C++ (development files)
liblog4cxx10-doc - Documentation for log4cxx
liblogback-java - flexible logging library for Java
liblogback-java-doc - flexible logging library for Java - documentation
dave@METROPOLIS:~$ 

I hope this is what you needed to see.

---

### Post by iphands on 2010-04-22
> **Vined Adobo said:**
> This is what I got:

dave@METROPOLIS:~/PulseOx/workspace/PulseOx/jars$ ls -lh
total 0
lrwxrwxrwx 1 dave dave 13 2010-04-21 21:35 java -> /usr/lib/java
lrwxrwxrwx 1 dave dave 18 2010-04-22 15:21 lib -> /usr/share/ant/lib

Yeah, this is not right. 

> **Vined Adobo said:**
> dave@METROPOLIS:~$ apt-cache search log4j
libexcalibur-logkit-java - Lightweight and fast designed logging toolkit for Java
liblog4j1.2-java - Logging library for java
liblog4j1.2-java-doc - Documentation for liblog4j1.2-java
liblog4j1.2-java-gcj - Logging library for java (native code)
liblog4net1.2-cil - highly configurable logging API for the CLI
liblogkit-java - Lightweight and fast designed logging toolkit for Java
libslf4j-java - Simple Logging Facade for Java
cl-arnesi - small Common Lisp utilities
libjboss-common-java - The JBoss Common Project
liblog-log4perl-perl - A Perl port of the widely popular log4j logging package.
liblog4cpp-doc - A C++ library for flexible logging (documentation)
liblog4cpp5 - C++ library for flexible logging (runtime)
liblog4cpp5-dev - C++ library for flexible logging (development)
liblog4cxx10 - A logging library for C++
liblog4cxx10-dev - A logging library for C++ (development files)
liblog4cxx10-doc - Documentation for log4cxx
liblogback-java - flexible logging library for Java
liblogback-java-doc - flexible logging library for Java - documentation
dave@METROPOLIS:~$ 

I hope this is what you needed to see.

You might have to install the liblog4j1.2-java package (and an swt package).

Then run:
# updatedb
# locate swt.jar
# locate log4j.jar

find the two jars.

On my system they are:
/usr/lib64/java/swt.jar
/usr/lib64/java/log4j.jar

I don't mind looking at you output though.
Regards,
-Ian Page Hands

---

### Post by Vined Adobo on 2010-04-23
> **iphands said:**
> Yeah, this is not right. 



You might have to install the liblog4j1.2-java package (and an swt package).

Then run:
# updatedb
# locate swt.jar
# locate log4j.jar

find the two jars.

On my system they are:
/usr/lib64/java/swt.jar
/usr/lib64/java/log4j.jar

I don't mind looking at you output though.
Regards,
-Ian Page Hands


I changed the links.  Here is my jars directory:
dave@METROPOLIS:~/PulseOx/workspace/PulseOx/jars$ ls -lh
total 0
lrwxrwxrwx 1 dave dave 36 2010-04-22 20:53 ant-apache-log4j.jar -> /usr/share/java/ant-apache-log4j.jar
lrwxrwxrwx 1 dave dave 23 2010-04-22 20:50 swt.jar -> /usr/share/java/swt.jar
dave@FUSION:~/PulseOx/workspace/PulseOx/jars$ 

Still doesn't compile.  Here is the output of the commands you asked me to type in:

updatedb returned nothing

dave@METROPOLIS:~$ locate swt.jar
/etc/alternatives/swt.jar
/home/dave/PulseOx/workspace/PulseOx/jars/swt.jar
/usr/share/java/swt.jar
/var/lib/dpkg/alternatives/swt.jar
dave@METROPOLIS:~$ locate log4j.jar
/home/dave/PulseOx/workspace/PulseOx/jars/ant-apache-log4j.jar
/usr/share/ant/lib/ant-apache-log4j.jar
/usr/share/java/ant-apache-log4j.jar

I did an apt-get install for log4j.jar, but file couldn't be found.

Alas, poor me.

Thanks for all the help.
Dave

---

### Post by iphands on 2010-04-23
> **Vined Adobo said:**
> I changed the links.  Here is my jars directory:
dave@METROPOLIS:~/PulseOx/workspace/PulseOx/jars$ ls -lh
total 0
lrwxrwxrwx 1 dave dave 36 2010-04-22 20:53 ant-apache-log4j.jar -> /usr/share/java/ant-apache-log4j.jar
lrwxrwxrwx 1 dave dave 23 2010-04-22 20:50 swt.jar -> /usr/share/java/swt.jar
dave@FUSION:~/PulseOx/workspace/PulseOx/jars$ 


Hey, that looks better :-D.


> **Vined Adobo said:**
> Still doesn't compile.  Here is the output of the commands you asked me to type in:

Hmm, I wonder why... Wanna paste the output from ant?

---

### Post by Vined Adobo on 2010-04-23
> **iphands said:**
> Hey, that looks better :-D.




Hmm, I wonder why... Wanna paste the output from ant?


Buildfile: build.xml

compile:
    [javac] Compiling 9 source files to /home/dave/PulseOx/workspace/PulseOx/bin
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:11: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:26: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.FileListener
    [javac]     Logger logger = Logger.getLogger(FileListener.class);
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:8: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.ConsoleAppender;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:9: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.FileAppender;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:10: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Layout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:11: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Level;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:12: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:13: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.PatternLayout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:14: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.SimpleLayout;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:41: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Logger logger = Logger.getLogger(LoggingListener.class);
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:46: cannot find symbol
    [javac] symbol  : class Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level fileLevel = Level.INFO;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:47: cannot find symbol
    [javac] symbol  : class FileAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     FileAppender fileAppender = null;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:50: cannot find symbol
    [javac] symbol  : class Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level consoleLevel = Level.DEBUG;
    [javac]     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:51: cannot find symbol
    [javac] symbol  : class ConsoleAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     final ConsoleAppender consoleAppender = new ConsoleAppender(
    [javac]           ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:4: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Level;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:5: package org.apache.log4j does not exist
    [javac] import org.apache.log4j.Logger;
    [javac]                        ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:31: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]     static Logger logger = Logger.getLogger(TestGUI.class);
    [javac]            ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/FileListener.java:26: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.FileListener
    [javac]     Logger logger = Logger.getLogger(FileListener.class);
    [javac]                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:41: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Logger logger = Logger.getLogger(LoggingListener.class);
    [javac]                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:46: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level fileLevel = Level.INFO;
    [javac]                       ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:50: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     Level consoleLevel = Level.DEBUG;
    [javac]                          ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:51: cannot find symbol
    [javac] symbol  : class ConsoleAppender
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]     final ConsoleAppender consoleAppender = new ConsoleAppender(
    [javac]                                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:52: cannot find symbol
    [javac] symbol  : class SimpleLayout
    [javac] location: class org.ahands.ian.pulseox.LoggingListener
    [javac]             new SimpleLayout());
    [javac]                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:148: cannot find symbol
    [javac] symbol: class Logger
    [javac]                 Logger rootLogger = Logger.getRootLogger();
    [javac]                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:148: cannot find symbol
    [javac] symbol: variable Logger
    [javac]                 Logger rootLogger = Logger.getRootLogger();
    [javac]                                     ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:164: cannot find symbol
    [javac] symbol: class Layout
    [javac]                         Layout fileLayout = new PatternLayout("%m\n");
    [javac]                         ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:164: cannot find symbol
    [javac] symbol: class PatternLayout
    [javac]                         Layout fileLayout = new PatternLayout("%m\n");
    [javac]                                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:167: cannot find symbol
    [javac] symbol: class FileAppender
    [javac]                             fileAppender = new FileAppender(fileLayout,
    [javac]                                                ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:294: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.DEBUG;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:296: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.INFO;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:298: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.WARN;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:300: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.ERROR;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:302: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     fileLevel = Level.FATAL;
    [javac]                                 ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:376: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.DEBUG;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:378: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.INFO;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:380: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.WARN;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:382: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.ERROR;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/LoggingListener.java:384: cannot find symbol
    [javac] symbol: variable Level
    [javac]                     consoleLevel = Level.FATAL;
    [javac]                                    ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:31: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]     static Logger logger = Logger.getLogger(TestGUI.class);
    [javac]                            ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:285: cannot find symbol
    [javac] symbol  : class Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         final Logger rootLogger = Logger.getRootLogger();
    [javac]               ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:285: cannot find symbol
    [javac] symbol  : variable Logger
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         final Logger rootLogger = Logger.getRootLogger();
    [javac]                                   ^
    [javac] /home/dave/PulseOx/workspace/PulseOx/src/org/ahands/ian/pulseox/TestGUI.java:286: cannot find symbol
    [javac] symbol  : variable Level
    [javac] location: class org.ahands.ian.pulseox.TestGUI
    [javac]         rootLogger.setLevel(Level.DEBUG);
    [javac]                             ^
    [javac] 42 errors

BUILD FAILED
/home/dave/PulseOx/workspace/PulseOx/build.xml:12: Compile failed; see the compiler error output for details.

Total time: 1 second

(carets changed places when I pasted output)

I even tried changing the name (only) of the link to "log4j.jar" but same errors.

Thank you so much for the time you have spent on my problem
Dave

---

### Post by Vined Adobo on 2010-04-25
I installed gtkterm and configured port for /dev/ttyUSBO 19200 N81.  I don't get any data from oximeter in monitor mode, but when I upload data from oximeter to laptop, I do see data coming across (this is the data I want to see so I can make a sleep study graph in a spreadsheet) but it is all garbled.  I tried setting my speed, parity, data bits, stop bits, DTR and CTS to all possible settings (at least I think I tried all permutations) but couldn't find any setting that would give me clear data.

Can anyone help me from this new direction I'm trying?

Thank you.
Dave

---

### Post by ubusarah on 2010-10-24
Hi Dave (And All...)

I just got my own CMS50F pulse oximeter (the one with the wrist display) so I will likely join in trying to make it work decently on Linux... the Windows software is kind of rough. However, it will probably have to wait until I've been on CPAP a little while because at the moment I don't really have the energy... :)

Has anybody else done any additional work on this recently?

Sarah

---

### Post by vaideheep on 2011-08-10
Hello,

I have a pulse oximeter CMS50E model too and downloaded all the files that Ian posted. When I run "java -jar pulseox.jar" (in ubuntu 10.10) the gui comes up, and although my pulse oximeter is plugged into the usb port and showing readings, those readings are not showing up on the gui. The gui stays blank as if it is not registering any readings.

I used dmesg and it appears that the pulse ox is mapped to dev/ttyUSB0. So I did not change anything in the code. The pulse oximeter "USB mode" and "Recording" is on. 

Can anyone think of something I am doing wrong?

Thanks,
Vaidehee

---

