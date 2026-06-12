---
title: "DVD viewing problems in KDE"
date: 2006-04-16
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-04-16
I am a KDE newbie. 

When I put the DVD into the desktop it doesn't recognize it, it wont play it (of course) but if I goto gnome it would play it without any problems and so would it play on windows. Is it somekinda mounting issue ??

Every help is appreciated.

---

### Post by krypto_wizard on 2006-04-16
Please help with this issue as I am liking KDE and want to stick to it. 

Every help is appreciated.

---

### Post by gingermark on 2006-04-16
Probably need more info to help.
Does any DVD icon appear on the Desktop? If you open 'system:/media' in Konqueror is there a DVD icon there? Can you right click and select "mount"?
Which version of KDE are you using?

---

### Post by krypto_wizard on 2006-04-16
KDE version 3.5.2 ...just upgraded few days back.

As soon as I put CD an icon comes on the screen ans asks me to play CD , open in new windows etc

But When I put DVD nothing happens, niether the icon comes nor would it let me play the DVD using Media player. An error comes that couldnt find DVD and some error message related to /etc/fstab.

I check if it was mounted but it won't show there too.

I tried mounting using

mount -a

also using mount /dev/hdc

I dont know whats the problem, in gnome it works pretty smooth and so in windows, so i am sure its not hardware problem.

Every help is appreciated

[QUOTE=gingermark]Probably need more info to help.
Does any DVD icon appear on the Desktop? If you open 'system:/media' in Konqueror is there a DVD icon there? Can you right click and select "mount"?
Which version of KDE are you using?[/QUOTE]

---

### Post by gingermark on 2006-04-16
[QUOTE=krypto_wizard]KDE version 3.5.2 ...just upgraded few days back.

When I put DVD nothing happens, niether the icon comes nor would it let me play the DVD using Media player. An error comes that couldnt find DVD and some error message related to /etc/fstab.
Every help is appreciated[/QUOTE]

Mounting was a little dodgy sometimes for me in Breezy, but has been great since KDE 3.5, at least in my experience.

I can only suggest posting the contents of /etc/ivman/IvmConfigActions.xml and /etc/fstab, and maybe we can see if there is anything up with either of them,

---

### Post by krypto_wizard on 2006-04-17
I get the following error message when i try to start DVD from Totem or gxine.

Failed to play Audio/Video Disc
Failed to find mountpoint for device /dev/hdc in /etc/fstab

This is the /etc/ivman/IvmConfigActions.xml
```

<?xml version="1.0" encoding="UTF-8"?>
<ivm:ActionsConfig version="0.2" xmlns:ivm="http://www.eikke.com/ivm">

    <!-- syntax of this file:

         <ivm:Match name="matchname" value="matchvalue">
             <ivm:Option name="optionname1" value="optionvalue1" />
             <ivm:Option name="optionname2" value="optionvalue2" />
             ...
         </ivm:Match>

         Matches can be nested.  See the examples.

         If a device matches multiple times and is given conflicting options,
         then the last options (closest to end of file) take precedence.
    -->

    <!-- names for Match:

         ivm.mountable (true/false) - a volume which can be mounted by ivman
         hal.anything (mixed) - the HAL property specified by 'anything'
         * - always match (use with care!)

         The hal.anything match is very powerful; see the examples in this
         file for some things which can be done.  Use the output of 'lshal'
         to come up with properties to match for certain devices.
    -->

    <!-- names for Option:
         mount (true/false) - mount the volume
         exec (string) - execute the given command
         execdvd (string) - execute the given command if device is a video DVD volume
         execun (string) - execute the given command when physical device is removed
                           or when disc is removed from drive.  Note that HAL properties
                           substituted for execun will be those at the time of the _insertion_
                           of the device (or at time of mounting if Ivman mounts the device),
                           since the device no longer exists at time of
                           execution (therefore we cannot get properties of it).

         For autoplaying of CDs etc, it is recommended to put an entry in the
         file ~/.ivman/IvmConfigActions.xml and have that user run their
         own instance of Ivman (e.g. in ~/.kde/Autostart).

         A single device can have multiple exec, execdvd and execun
         options; for all others, only the option closest to the end of the
         file will be used.
    -->
    <!-- commands can have any HAL properties placed within them by surrounding
         the property name with $ symbols, for example, $hal.block.device$.
    -->
    <!-- don't forget that this is XML, so some characters will need to be escaped.
         A summary for those who don't know XML/HTML:
         This           Becomes This
         &              &amp;
         <              &lt;
         >              &gt;
         '              &apos;
         "              &quot;
    -->


    <!-- try to mount any mountable volume at all -->
    <ivm:Match name="ivm.mountable" value="true">
        <ivm:Option name="mount" value="true" />
    </ivm:Match>

    <!-- example - autoplay CDs with audio tracks and no data tracks -->
    <!--
    <ivm:Match name="hal.volume.disc.type" value="cd_rom">
        <ivm:Match name="hal.volume.disc.has_audio" value="true">
            <ivm:Match name="hal.volume.disc.has_data" value="false">
                <ivm:Option name="exec" value="/usr/bin/cdplay -d $hal.block.device$ -c" />
            </ivm:Match>
        </ivm:Match>
    </ivm:Match>
    -->

    <!-- example - autoplay video DVDs -->
    <!-- video DVD detection is an ugly hack at the moment, because it's not
         possible to tell if a DVD contains video without mounting it first.
         That's why we don't use a 'Match' to tell if a volume is a video
         DVD yet. -->
    <!--
    <ivm:Option name="execdvd" value="pumount $hal.block.device$ &amp;&amp; /usr/bin/mplayer dvd://1 -really-quiet -fs" />
    -->

    <!-- example - don't mount /dev/camera -->
    <!--
    <ivm:Match name="hal.block.device" value="/dev/camera">
        <ivm:Option name="mount" value="false" />
    </ivm:Match>
    -->

    <!-- example - log whenever someone attaches or removes a device -->
    <!--
    <ivm:Match name="*">
        <ivm:Option name="exec" value="echo `basename $hal.info.udi$` attached at `date` &gt;&gt; /tmp/devices" />
        <ivm:Option name="execun" value="echo `basename $hal.info.udi$` removed at `date` &gt;&gt; /tmp/devices" />
    </ivm:Match>
    -->

   <!-- open konqueror -->
   <ivm:Match name="hal.info.category" value="volume">
           <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" />
   </ivm:Match>

   <!-- open kscd for audiocds -->
   <ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>

   <!-- kaffeine for videos -->
   <ivm:Match name="hal.volume.disc.type" value="dvd_rom">
       <ivm:Option name="execdvd" value="pumount $hal.block.device$ &amp;&amp; /usr/bin/kaffeine dvd://1" />
   </ivm:Match>

   <!-- popup a message for scanners -->
   <ivm:Match name="hal.info.category" value="scanner">
       <ivm:Match name="hal.storage.bus" value="usb">
           <ivm:Option name="exec" value="kdialog --passivepopup 'USB scanner detected: $hal.info.vendor$ $hal.info.product$' 6" />
       </ivm:Match>
   </ivm:Match>

   <!-- popup a message for printers -->
   <ivm:Match name="hal.info.category" value="printer">
        <ivm:Match name="hal.info.bus" value="usb">
           <ivm:Option name="exec" value="kdialog --passivepopup 'USB printer detected: $hal.info.vendor$ $hal.info.product$' 6" />
        </ivm:Match>
   </ivm:Match>

   <!-- cameras -->
   <ivm:Match name="hal.info.product" value="USB PTP Interface">
           <ivm:Option name="exec" value="kfmclient openURL media:/camera" />
   </ivm:Match>

</ivm:ActionsConfig>

```

And here is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hda1 		/media/windows 	ntfs 	nls=utf8,umask=0222 0 0
#/dev/hda5 		/media/fat 		vfat 	iocharset=utf8,umask=000 0 0

```

[QUOTE=gingermark]Mounting was a little dodgy sometimes for me in Breezy, but has been great since KDE 3.5, at least in my experience.

I can only suggest posting the contents of /etc/ivman/IvmConfigActions.xml and /etc/fstab, and maybe we can see if there is anything up with either of them,[/QUOTE]

---

### Post by gingermark on 2006-04-17
OK, the reason I asked for those was that it was my understanding thay they are responsible for automounting in Breezy. I've recently done a fresh install, and it all works fine on my system, so I thought comparing those files with mine could find the problem. Unfortunately they are identical to those on my system, so my apologies for wasting your time there.

Looking around the forum it seems there are some common reasons for this problem. Hardware problems (which I'm discounting cos your drive works in Windows and Gnome) and Codec problem (which I'm discounting as your drive works in Gnome).

Anyways, I found one thread [here](http://www.ubuntuforums.org/showthread.php?t=89224) that suggested a workaround:
[QUOTE=tseliot]I have the same problem but I have find a workaround:

right click on a free space of the desktop and select

Create new/Link to device/DVD-Rom Device (or Harddisk device, etc.)

write the name of the link in the "General" page (e.g. "pioneer" or "burner", etc.)

click on the Device section:
you will see a text field. Click on the arrow located at its right and select the name of the peripheral according to how it is named in your /etc/fstab (e.g. "/dev/hdc")

Then click ok

Double click on your new link on the desktop

Et voila, your peripheral will mount.[/QUOTE]
So, I'd suggest adding a DVD device to your desktop and seeing if this indeed does the job.

Sorry I couldn't be of more help.

---

### Post by krypto_wizard on 2006-04-18
Can anybody help me with this

---

### Post by krypto_wizard on 2006-04-19
Is it a common problem in KDE because gnome never had such problems >

---

### Post by aha1215 on 2006-04-23
I have installed VLC for DVD player. And I have also installed most of the items shown in Synaptic Package. But when ever I put DVD the programe runs and then quit. 

The message is 

libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000126
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000126)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001e6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000001e6)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000003cd
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000003cd)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c483d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001c483d)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c4e19
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001c4e19)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001c90fa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001c90fa)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[00000252] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 54 error_code 8 request_code 142 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


any one known to this kinda prblm plz advise

---

### Post by ajgreeny on 2006-04-23
I think you need libdvdcss2 from synaptic, which will allow you to play encrypted dvd files.

---

