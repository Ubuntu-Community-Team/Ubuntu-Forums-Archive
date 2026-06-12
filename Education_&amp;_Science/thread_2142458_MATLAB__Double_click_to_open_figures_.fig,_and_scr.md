---
title: "MATLAB : Double click to open figures *.fig, and scripts *.m files in Ubuntu."
date: 2013-05-05
forum: Education &amp; Science
---

### Post by sbnwl on 2013-05-05
While one can easily install MATLAB by following instructions from [Community Ubuntu Documentation for MATLAB]("https://help.ubuntu.com/community/MATLAB"), Still there is a common glitch is the file association of matlab scripts, figures and *.mat files. One cannot directly open them by simply double clicking on them in the file manager in Ubuntu/Linux OS, which is a cool feature on Windows or Mac OS. 

Here is a pretty quick way do solve the above problem.


[LIST=1]
[*]Make a Desktop Entry file, with the following contents:```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=matlab
NoDsiplay=true
Exec=matlab -desktop -r "open %f"
Name[en]=MATLAB-Open
Icon=/usr/share/icons/matlab.png
```
Save the file with a filename MATLAB-Open.desktop 
[*]Place the file in the ~/.local/share/applications directory:```
mv MATLAB-Open.desktop ~/.local/share/applications
``` 
[*]That's all. Open a new nemo/nautilus window, navigate to any directory containing matlab script (*.m) OR figure (*.fig) files. Right click the file, and choose 'Open with Other application', and choose 'Show other applications'. Here you can choose MATLAB-Open from the 'Other applications' list.The next time you double click on any matlab script file, that will automatically open in matlab. 
[*]Repeat step 3 for matlab figure files (*.fig) also. 
[/LIST]
[HR][/HR]TO THOSE WHO USE NEMO FILE MANAGER, THERE IS ADDITIONAL (OPTIONAL) INFORMATION BELOW:

Make a file named 'Open in MATLAB' with the following contents```
#!/bin/sh
matlab -desktop -r "cd %d"
```
Save the file, make the file executable, and place it in ~/.gnome2/nemo-scripts directory.```
mv 'Open in MATLAB' ~/.gnome2/nemo-scripts
```
Now you can launch matlab session from within any directory, and drag and drop the figure files or script files into matlab window to execute them. It is done by right clicking in file manager and selecting 'scripts >> Open in MATLAB' within the context menu.

---

### Post by S1RHC on 2013-05-11
sbnwl,
I followed your guide and generally it works!
Yet, I am facing one, quite annoying, problem: each .m file I open, opens in a new instance of Matlab. Is there any way to solve that?
Thanks in advance,
Chris

---

### Post by sbnwl on 2013-05-17
Yes you are right. I agree that each *.m file opens in a new session of matlab. It could be instead taken as good, because you probably won't want your variables to mix into each other from two different matlab codes:)

---

