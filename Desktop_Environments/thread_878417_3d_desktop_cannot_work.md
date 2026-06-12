---
title: "3d desktop cannot work"
date: 2008-08-02
forum: Desktop Environments
---

### Post by duge0413 on 2008-08-02
Does anyone know how to install 3d desktop.when I install it ,the following is the messages of the terminal :
sudo apt-get install 3ddesktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3ddesktop

---

### Post by bas1 on 2008-08-02
> **duge0413 said:**
> Does anyone know how to install 3d desktop.when I install it ,the following is the messages of the terminal :
sudo apt-get install 3ddesktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3ddesktop

What exactly do you want to install? If you mean compiz-fusion (see youtube), it is installed by default from Ubuntu 7.04 and on, and activated by default from Ubuntu 7.10 and on. If it's not activated already, you may need to install the proper drivers for your video card (eg nvidia, ati).

---

### Post by arubislander on 2008-08-02
> **bas1 said:**
> What exactly do you want to install? If you mean compiz-fusion (see youtube), it is installed by default from Ubuntu 7.04 and on, and activated by default from Ubuntu 7.10 and on. If it's not activated already, you may need to install the proper drivers for your video card (eg nvidia, ati).

Yep, the 3ddesktop package seems not to be included in the hardy repositories anymore.

And while compiz-fusion is installed and enabled by default as bas1 says, the 3d desktop cube effect is not. To enable that you need to install the compizconfig-settings-manager package.

---

### Post by sayakb on 2008-08-03
As indicated, install the compizconfig-settings-manager package. Then goto System->Preferences->Advanced desktop effects settings and **check** the *Desktop cube*, *rotate cube* and *cube caps* plugins. Also, goto System->Preferences->Appearance->Visual Effects and click on Extra to enable compiz (or type in **compiz --replace &** at a terminal)

---

### Post by jeepers on 2008-08-03
> **LinuxIsInnovation said:**
> As indicated, install the compizconfig-settings-manager package. Then goto System->Preferences->Advanced desktop effects settings and **check** the *Desktop cube*, *rotate cube* and *cube caps* plugins. Also, goto System->Preferences->Appearance->Visual Effects and click on Extra to enable compiz (or type in **compiz --replace &** at a terminal)

I get this when i run the replace command:

john@john-ubuntu:~$ compiz --replace &
[1] 6521
Checking for Xgl: john@john-ubuntu:~$ not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

what does "an unsupported value" mean ?. I have the Cube desktop enabled, and can rotate it with the "Ctrl+alt+right click" but will not rotate by itself although i have that option ticked in the advanced desktop.

and when i go to System>>Appearance>>Visual Effects and select extra, it will not stay selected.

cheers

---

### Post by sayakb on 2008-08-03
Open CCSM and disable the **Scale** plugin. 
Also to rotate the cube, you need to press **Ctrl+Alt+Left mouse button** to initiate free rotation.

---

### Post by jeepers on 2008-08-03
> **LinuxIsInnovation said:**
> Open CCSM and disable the **Scale** plugin. 
Also to rotate the cube, you need to press **Ctrl+Alt+Left mouse button** to initiate free rotation.

Thank you for the reply...I disabled the "Utility..scale add-ons, but when i press "Ctrl + Alt + left mouse button" it gets the cube effect, but only while i have the "Ctrl + Alt + left mouse button" pressed, as soon as i release them it goes back to my normal desktop.

cheers

---

### Post by sayakb on 2008-08-03
I don't quite know how to keep the desktop zoomed out while not rotating.
1. In the rotate cube plugin, set zoom level to 0.4
2. In the desktop cube plugin, click on **Transparent Cube** tab and adjust the transparency levels to reveal other desktops while not rotating.

---

### Post by jeepers on 2008-08-03
O.K. i have spent a whole day on this..and still cannot get the desktop to rotate . I can rotate the desktop manually by moving my mouse of the screen either left or right.

But i must be missing something, as i cannot get the cube to spin without using the mouse.

It is set up O.K. with a skydome background set to animate. and have searched and followed the tutorials, but no joy.:(

cheers

---

### Post by |{urse on 2009-05-02
okay i think the OP was referring to the package 3ddesktop not compiz-fusion. 3ddesktop is no longer in the repos. Anyone know where i can get a deb for it?

---

