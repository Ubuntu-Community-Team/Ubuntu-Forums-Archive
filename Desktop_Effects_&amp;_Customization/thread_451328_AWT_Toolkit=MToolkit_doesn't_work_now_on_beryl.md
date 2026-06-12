---
title: "AWT_Toolkit=MToolkit doesn't work now on beryl"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by jaywhy13 on 2007-05-22
This fix doesn't work on Beryl now. I'm using Feisty Fawn. Netbeans comes up blank.

Is there anything I'm not loading possibly in Xorg.conf?
Here's the device section

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "UseInternalAGPGART" "no"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "MonitorLayout" "LVDS, AUTO"
        BusID       "PCI:1:0:0"
EndSection

And the module section

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
#       Load  "extmod"
        SubSection  "extmod"
          Option  "omit xfree86-dga"
        EndSubSection
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "vbe"
EndSection

---

### Post by Circus-Killer on 2007-06-29
*bump*
having the same problem, any solutions?

---

### Post by shanaka36 on 2007-07-02
I have the same problem with netbeans as well as blender........:(

---

### Post by glok_twen on 2007-07-05
same problem here. :( 

searched all over the web and every solution calls for adding the export AWT_TOOLKIT env var. however when i do that, my netbeans core dumps.

i am running 64bit fiesty.

anyone know of a solution?

---

### Post by leinuz.basher on 2007-07-28
I finally find a useful link to fix my problem... Just A simple Edit....

[http://www.mepis.org/docs/en/index.php/Fix_Java_Applications_in_Beryl](http://www.mepis.org/docs/en/index.php/Fix_Java_Applications_in_Beryl)


Just Used Root User to run NB so It will run smoothly

---

### Post by hoogland on 2008-03-24
I had the same problem running Matlab with Compiz on Hardy Beta. The solution to this problem is to create a soft link as follows:



> ln -s [matlabroot]/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif21
[matlabroot]/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif12


where [matlabroot] is the root directory of matlab.

Of course you also need a shell script to launch your program. Mine contains the following lines:


> 
unset LANG
export LIBXCB_ALLOW_SLOPPY_LOCK=true
export AWT_TOOLKIT=MToolkit

matlab


EDIT update: I edited out 'export HOSTNAME=localhost' as this caused some problems

---

