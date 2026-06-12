---
title: "Problem Opening office/pdf files *directly* on Windows Shares via Nautilus, xffm, etc"
date: 2005-03-02
forum: Desktop Environments
---

### Post by Mike Eberhart on 2005-03-02
Using UBUNTU distro, I noticed that if I browse to a Windows Share (via smb) using Nautilus or XFCE's xffm, konquerer etc., that, although I can see the files I want, and can COPY them to my Ubuntu system, I cannot *directly* open the file by double-clicking it in the file-explorer(s).  Such action always errors with something like this:

"Error Loading Document    file:///home/mike/smb://administrator@winservernamehere/sharename/directoryname/file.swx"  (for example of opening an OpenOffice.org file)

By contrast, under Knoppix, I can browse to the same files on network using konquerer, etc, and simply double-click on the file, and voila!, it opens as expected in xpdf, openoffice, etc.

I have tried under Ubuntu Warty, and latest Hoary builds.  I am comparing to Knoppix 3.7.    I have even tried same versions of Konqueror under both Ubuntu and Knoppix, and I only have issues under Ubuntu.

Is this a GNOME issue, or an Ubuntu implementation issue?  And, is it a known bug/issue?  If so, is there a "quick fix"?

---

### Post by bladedog on 2005-04-18
I just noticed this with Hoary. Has this been addressed or fixed?

---

### Post by LeoTheLion on 2005-04-25
I'm having this problem with two current Hoary installations. txt files work and Gnumeric can open Open Office spreadsheet files but OpenOffice won't open any files and neither xpdf or evince will open pdf files.

I have tried opening files on network drives running Mac os X and Ubuntu. Same results for either server os.

If anyone has any ideas it would be great to here them.

---

### Post by Michael Kofler on 2005-05-03
openoffice can't open network files because it has no gnome vfs support

the package openoffice.org-gnomevfs (universe) should solve this, but unfortunately even after the installation it is impossible to open network files (I have no idea, why)

---

### Post by Mujaheiden on 2007-03-30
Also doesnt work in edgy, where the openoffice.org-gnome is defaultly installed with OO. A fix was suggested [here]("http://ubuntuforums.org/showthread.php?p=2370836") but i dont know how to implement.

---

