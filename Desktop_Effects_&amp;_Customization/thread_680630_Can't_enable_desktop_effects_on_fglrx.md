---
title: "Can't enable desktop effects on fglrx"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by ASPCartman on 2008-01-28
Hi. I have ATI x1800. I installed 8.1 fglrx driver. My outputs r

```
$ glxinfo | grep direct
direct rendering: Yes

```

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.1.7276 Release


```

As i see everything must be ok but when i try to enable desktop effects i got message "Cannot enable desk effects"

When i exec "compiz --replace" somethings happens but still no effects.
```

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:7109 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 373: /usr/local/bin/compiz: not found


```

---

### Post by frodon on 2008-01-28
I'm not an ATI expert but i believe that for most versions of ati drivers you need xserver-xgl package installed to get it working. The drawback being that there's no direct rendering with XGL.

However i've heard that latest driver version don't require XGL anymore.

---

### Post by ASPCartman on 2008-01-28
Yeah ur right - last one doesn't need it.:(

---

### Post by CUC_Byron on 2008-01-28
I have the same problem with my on board X1250, and I've solved it.

As far as I know, the problem is related to these two things:

aiglx, xgl

aiglx is a fundamental thing needed for running compiz, I think.

At the time Ubuntu 7.10 released, the old ati driver can't use aiglx directly, so as a bridge xgl is needed.

And when the compiz is running, it'll first check if xgl is enabled. If not, the message "Cannot enable desk effects" will appear.so we have to install xgl.

But we don't have to do that now. I just want to explain the problem clearly for you.

The new driver 8.1 supports aiglx directly. So we do not need to install xgl (maybe there'll be troubles if we install it now).

But there's is a bug(I think it's a bug), though we installed the new driver, the old compiz will still check if the xgl is enabled. So the message "Cannot enable desk effects" appears again.You can see the bug if you type "compiz" and press enter in the terminal.

 So after the long explaination, the only thing we have to do is to bypass the checking progress.

Now let's open the terminal and begin.

1. type these and press enter:

[COLOR="SeaGreen"]sudo gedit /usr/bin/compiz [/COLOR]

to open gedit and edit a file of compiz

2. find this

[COLOR="seagreen"]# Driver whitelist 
WHITELIST="nvidia intel ati radeon i810" [/COLOR]

and add fglrx into it. Like this:

[COLOR="seagreen"]# Driver whitelist 
WHITELIST="fglrx nvidia intel ati radeon i810" [/COLOR]

You can see, you added the fglrx driver to the compiz driver whitelist.

3. find this:

[COLOR="seagreen"]# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details 
T=" 1002:5954 1002:5854 1002:5955" # ati rs480 
T="$T 1002:4153" # ATI Rv350 
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965 
T="$T 8086:2972" # i965 (x3000) 
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T" [/COLOR]

and change all these lines into:

[COLOR="seagreen"]# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T" 
BLACKLIST_PCIIDS="" [/COLOR]

you can see, this step cleared the compiz driver blacklist.

4. then change the lines 30-35 into these lines:

[COLOR="seagreen"]COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz 
PLUGIN_PATH="/usr/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo" 
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity" 
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real) [/COLOR]

this step solved the "not found" problem you listed at the last of your code frame.

5. restart your computer and enable the desktop affects.

May be you'll have to do something more to enable your compiz--- to enable aiglx
 
type "sudo gedit /etc/X11/xorg.conf " in the terminal to edit the configuration file of the GUI.

And, add these lines into the file, anywhere is OK, but I think it's the safest to add them to the last of it:

Section "Extensions" 
        Option  "Composite" "1" 
EndSection 

Section "ServerFlags" 
        Option  "AIGLX" "on" 
EndSection 

these are the everything I did to run compiz.

PS:

I learned this solution from [http://forum.ubuntu.org.cn](http://forum.ubuntu.org.cn)

the new 8.1 driver is still a bit slow, but better than any one before.It's said that the next driver would be much more faster.

someone said the new driver solved the problem on playing video, but I think installing the newest compiz is the right way if it flashes when you play video.

I'm a Chinese and not very good at English. I hope my explaination is clear.

At last, hope you enjoy your life with Ubuntu~~~

---

