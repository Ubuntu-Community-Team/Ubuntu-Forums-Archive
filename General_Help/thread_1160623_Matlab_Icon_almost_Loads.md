---
title: "Matlab Icon almost Loads"
date: 2009-05-15
forum: General Help
---

### Post by Swamprat2010 on 2009-05-15
Hi All,

I just installed Matlab onto Kubuntu and I am having some trouble making an icon for it. I have managed to make the icon by putting a file into  /usr/share/applications/Matlab.desktop. See Code section.

The icon shows up fine and when I click it it will run the initial Matlab startup screen but then it closes mid way though the load and then nothing, its been killed. I can launch matlab fine from the Konsole  by just typing matlab, everything will run fine. 

What do i need to add/change to allow matlab to run as i would loading it from the konsole.

Many Thanks,
Richard

```
[Desktop Entry]
Version=2008b
Name=Matlab
Comment=Matlab and Simulink 2008b
GenericName=Matlab and Simulink 2008b

Exec=matlab
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/swamprat/Pictures/matlab-icon.png
Categories=Application;Network;
MimeType=
StartupWMClass=matlab
```

---

### Post by Swamprat2010 on 2009-06-01
Simple solution when you find it. Under command input for the ICON i had 'matlab' this should be changed to 'matlab -desktop'

---

