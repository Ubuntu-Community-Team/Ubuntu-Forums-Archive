---
title: "ABAQUS: Double click to open CAE *.cae, and database *.odb files in UBUNTU"
date: 2018-09-03
forum: Education &amp; Science
---

### Post by sbnwl on 2018-09-03
While one can easily install ABAQUS by following the instructions at various places on the web such as [here]("https://github.com/Solid-Mechanics/Install-ABAQUS-on-Ubuntu"), this is a huge inconvenience for most of the users to launch the ABAQUS CAE application everytime from terminal. 

One can definately make things more affordable and easy by **associating the CAE model (*.cae) and database (*.odb) files to the ABAQUS binary files**. 

This **feature** can make the **model** and database files to be **directly open**ed **in** the** ABAQUS CAE** interface (a GUI), simply **[B]by **do[/B]**[B]ub**le clicking[/B] on them from within the file manager in Ubuntu and Linux OS in general. 
This is similar to the feature already supported on Windows platform.

Here is how to bring this feature.

[LIST=1]
[*]Open a text editor and create a 'Desktop Entry' file by adding the following contents:
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=AbaqusCAE-Open
Exec=env XLIB_SKIP_ARGB_VISUALS=1 /bin/bash -c 'cd $(dirname $0) && /opt/abaqus/abaqus614/6.14-1/code/bin/abq6141 cae database=$0' %u
Icon=/opt/abaqus/abaqus614/6.14-1/CAEresources/graphic/icons/icoR_application.png
Comment=Open file in Abaqus CAE/Viewer
StartupNotify=true

```
Save the above file with the filename 'AbaqusCAE-Open.desktop' (without quotes). 
[*]Place the file in the ~/.local/share/applications directory:
```

mv AbaqusCAE-Open.desktop ~/.local/share/applications

``` 
[*]Finally, open the Files window (Nautilus/Nemo/Caja/Pantheon) and navigate to any directory containing a CAE model (*.cae). Right click on the *.cae file, choose 'Open with Other application', and choose 'Show other applications'. 
Here you can choose AbaqusCAE-Open from the 'Other applications' list. 
**The next time you ****double click**** on any Abaqus ****cae**** model file, it will automatically open in Abaqus GUI (CAE/Viewer).** 
[*]Repeat the above Step No. 3 once for an Abaqus output database (*.odb) file also. 
[/LIST]
 
Now you can directly open Abaqus *.cae and *.odb files in Abaqus GUI, from within any directory with a double click.

[HR][/HR]***Notes***: [I]
[LIST=1]
[*]You may need to make changes in the lines starting with 'Exec=' and 'Icon=' in the above Desktop Entry file, according to your ABAQUS installation directory and graphics card. 
*For example, the ABAQUS installation directory in the present example is '/opt/abaqus/abaqus614/' and the graphics card is an Intel integrated graphics.* 
[*][I]To make an Abaqus CAE launcher, create a Desktop Entry file (named 'AbaqusCAE.desktop') with the following contents and place it either in /usr/share/applications or in ~/.local/share/applications directory.
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=AbaqusCAE
Exec=env XLIB_SKIP_ARGB_VISUALS=1 /bin/bash -c 'cd $HOME/Documents/ATmp && /opt/abaqus/abaqus614/6.14-1/code/bin/abq6141 cae'
Icon=/opt/abaqus/abaqus614/6.14-1/CAEresources/graphic/icons/icoR_application.png
Comment=Launch the Abaqus CAE graphical user interface

```
In the above, we assume that the scratch directory is located at ~/[/I]*[I]Documents/ATmp/*[/I] 
[/LIST]
[/I]

---

