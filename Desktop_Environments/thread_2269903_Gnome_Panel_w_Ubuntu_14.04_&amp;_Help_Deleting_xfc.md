---
title: "Gnome Panel w/ Ubuntu 14.04 &amp; Help Deleting xfce"
date: 2015-03-18
forum: Desktop Environments
---

### Post by bonzo2 on 2015-03-18
Hello,

I have 2 desktop environment issues.

I am a Linux/Ubuntu newby who is running 14.04 LTS.  If it is correct that 14.04 includes the Unity desktop environment by default, then that is what I'm running. I'm confused about what constitutes a desktop environment and how I'm supposed to know which components are necessary to run one.  

**ISSUE 1**: I was looking for more desktop customizability and installed "xfce4" via the Synaptic Package Manager, but then decided I should acquaint myself more with the standard issue 14.04 before customizing. Besides the "xfce4" component (package?) that I installed, I saw approximately 28 other items that included "xfce" in their names or descriptors.  

Should I also delete those other "xfce" items and why are they there if I did not install them?


**ISSUE 2**: An awesome forum member named pdc assisted me with installing a scanner launcher for my desktop using "sudo apt-get install gnome-panel." (Launchers seem complicated in Ubuntu or at least Ubuntu 14.04.)

We got the launcher installed. May I continue to run gnome panel in the absence of gnome desktop or is there a similar launcher for Unity that I should try?

Thanks for reading,
Bonzo2

---

### Post by pmi2 on 2015-03-19
In general, you will be best off, if you uninstall a package or an app the same way you installed it.  So, if you installed XFCE4 in the Synaptic Project Manager, then you should uninstall it the same way.  Search for what you installed (probably Xfce4), click the green box and mark it for "complete removal", then click "Apply", and you should be done.

I am not sure if I understand the second question, you will have to ask pdc... :D

---

### Post by CantankRus on 2015-03-20
> **bonzo2 said:**
> Hello,

I have 2 desktop environment issues.

I am a Linux/Ubuntu newby who is running 14.04 LTS.  If it is correct that 14.04 includes the Unity desktop environment by default, then that is what I'm running. I'm confused about what constitutes a desktop environment and how I'm supposed to know which components are necessary to run one.  

**ISSUE 1:** I was looking for more desktop customizability and installed "xfce4" via the Synaptic Package Manager, but then decided I should acquaint myself more with the standard issue 14.04 before customizing. Besides the "xfce4" component (package?) that I installed, I saw approximately 28 other items that included "xfce" in their names or descriptors.  

Should I also delete those other "xfce" items and why are they there if I did not install them?


**ISSUE 2:** An awesome forum member named pdc assisted me with installing a scanner launcher for my desktop using "sudo apt-get install gnome-panel." (Launchers seem complicated in Ubuntu or at least Ubuntu 14.04.)

We got the launcher installed. May I continue to run gnome panel in the absence of gnome desktop or is there a similar launcher for Unity that I should try?

Thanks for reading,
Bonzo2
**ISSUE 1:** The xfce4 package is a metapackage which means it contains no real application itself 
but a list of applications needed for the Xfce desktop environment.  [**_[COLOR="#B22222"]MetaPackages[/COLOR]_**]("https://help.ubuntu.com/community/MetaPackages")
A desktop environment is defined by the window manager and set of applications used.
eg
_Ubuntu_
[LIST]
[*]Window manager: compiz
[*]Panel: Unity interface
[*]File browser: nautilus
[/LIST]
_Xfce_
[LIST]
[*]Window manager: xfwm4
[*]Panel: xfce4-panel
[*]File browser: thunar
[/LIST]

After installing a new desktop environment a new desktop session using that environment 
is created for you to choose from at the greeter.
[ATTACH=CONFIG]260760[/ATTACH]
When you uninstall the xfce4 package, it removes nothing except the metapackage which, as I said, is just a list of dependencies for the Xfce desktop environment.
Your Xfce session will function as normal.
In most cases  the different desktop environments shouldn't interfere with one another.
Lately, though there have been occasions where they do.


**ISSUE 2**:Most applications with a GUI, install a launcher (.desktop file) to **/usr/share/applications** which are then shown in the dash under Applications.
These can be dragged and dropped on the unity launcher but cannot be dragged and dropped from the dash to your desktop. 

Occasionally you may have to create your own custom launcher which is what pdc helped you with.
 
Before the unity interface, ubuntu used the gnome-panel which as part of it's package includes a command
to create a custom launcher.
In default unity, the only way to create a custom launcher is to manually create a .desktop file in your text editor 
which requires a bit of knowledge about .desktop files.
So for new users after installing gnome-panel you can use the command ```
gnome-desktop-item-edit --create-new **~/Desktop**
``` to place launcher icons on the desktop.


You could also use ```
gnome-desktop-item-edit --create-new **~/.local/share/applications**
``` to place the launcher in ~/.local/share/applications which is a location
searched by the dash to be listed under Applications.
You can then drag and drop the Dash Application icon to the launcher.

The gnome-panel doesn't startup when logging into the default Ubuntu session.... it's just installed so you can use the **gnome-desktop-item-edit** command.

---

