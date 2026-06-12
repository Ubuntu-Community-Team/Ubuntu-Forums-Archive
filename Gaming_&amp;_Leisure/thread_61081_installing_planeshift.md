---
title: "installing planeshift"
date: 2005-08-30
forum: Gaming &amp; Leisure
---

### Post by bobmaster on 2005-08-30
I'm tring to install planeshift but when I run it it says this.

ben@ubuntu:~$ sh /home/ben/PlaneShift_CBV0.3.011.linux.x86-2.run
Creating directory ps.cb.03.011.linux.x86-2
Verifying archive integrity... All good.
Uncompressing Planeshift Crystal Blue Version 3.011 relase 2.....Extraction failed.
Terminated
Am I doing something wrong?

---

### Post by arnieboy on 2005-08-30
[QUOTE=bobmaster]I'm tring to install planeshift but when I run it it says this.

ben@ubuntu:~$ sh /home/ben/PlaneShift_CBV0.3.011.linux.x86-2.run
Creating directory ps.cb.03.011.linux.x86-2
Verifying archive integrity... All good.
Uncompressing Planeshift Crystal Blue Version 3.011 relase 2.....Extraction failed.
Terminated
Am I doing something wrong?[/QUOTE]
Try doing a 
```
sudo sh /home/ben/PlaneShift_CBV0.3.011.linux.x86-2.run
```

---

### Post by bobmaster on 2005-08-30
It came up with the same message. Why would the extraction fail?

---

### Post by arnieboy on 2005-08-30
[QUOTE=bobmaster]It came up with the same message. Why would the extraction fail?[/QUOTE]
can be one or both reasons:
1) the file is corrupt.
2) the file paths hardcoded in the setup script do not exist on ur box and the script does not have a way to create them in case they are not there. u might want to look into the script and see what paths it installs the files into. create them manually and run the script again.
do a 
```
gedit /home/ben/PlaneShift_CBV0.3.011.linux.x86-2.run
```
to find out.

---

### Post by bobmaster on 2005-08-30
When I do that it gives me this error message.

gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.

---

### Post by arnieboy on 2005-08-30
[QUOTE=bobmaster]When I do that it gives me this error message.

gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.[/QUOTE]
ok then its a binary file. no use opening it in gedit. if it had been a shell script, we could have learnt something from it. what I would suggest you do is look for the howto on this shell script and find out the instructions. there should be something on where the files are getting installed. look on the website where u donwloaded it from. arent there any "readme" or instructions files along with the executable?

---

### Post by bobmaster on 2005-08-30
I found a howto it took awhile though. I'll post again when I'm finished.

---

