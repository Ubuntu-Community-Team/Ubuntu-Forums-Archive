---
title: "Corrupt F-Prot Installation"
date: 2006-01-29
forum: Desktop Environments
---

### Post by browndog on 2006-01-29
Hoping someone can help me with an error I got after installing F-Prot.  I got the directions for installing F-Prot from a post in the Ubuntu Breezy Tips and Customization forum...please take a look at the attached screenshot.  The directions in the screenshot also call for downloading and installing xfprot as a gui front end for F-Prot.  I followed all instructions to the letter, and everything worked out fine until I reached the line that says "make".  My first question is, what does the instruction "make" mean?  After that line the other code didn't work.  I put an F-Prot icon in the System Tools tool bar using smeg, and when I went to run it I got the following error message:

Cannot launch entry

Details: Failed to execute child process "xfprot" (No such file or directory)

I know this means something failed to install correctly.  Please take a look at the code in the attachment and see if you can help.  Thanks!!

BD

---

### Post by Perfect Storm on 2006-01-29
If the make command failed you can't go further. The make command means it uses all the information it gathered (usually from ./configure) about your system + your own preferences you desire and build the program.

I havn't figure out what the problem is yet, as other have the problems too and other don't, but I'm investigating it. 

Try see if this help:

```
sudo apt-get install build-essential
```
and run the howto again.

---

### Post by Perfect Storm on 2006-01-29
The howto have been corrected: You may try again. [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by browndog on 2006-01-30
[QUOTE=Artificial Intelligence]The howto have been corrected: You may try again. [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)[/QUOTE]
Thanks so much AI...I'll try your directions and the HowTo and let you know how it turned out.

---

### Post by browndog on 2006-01-30
[QUOTE=Artificial Intelligence]The howto have been corrected: You may try again. [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)[/QUOTE]

AI,

I followed your directions and the install went perfectly.  Thanks again.

BD

---

