---
title: "Uninstalling OpenOffice 2"
date: 2006-03-07
forum: Desktop Environments
---

### Post by avantgardaclue on 2006-03-07
I want to re-install open office (to try and stop it crashing) but this option in synaptic is not offered. 

I decided to delete and re-install from afresh but when i tried this it says that it would also remove my KDE desktop and ubuntu desktop... eeek... so didn't do that! (i have gnome, kde and xfce desktops in my boot options - love em all!)

The guys at openoffice forum said this was an ubuntu problem not an openoffice one - well they would say that wouldn't they!

Something about dependencies?

Any ideas?

---

### Post by Hallavej on 2006-03-07
Just remove (k)(x)ubuntu-desktop. There are no files in them at all.

---

### Post by adamkane on 2006-03-07
[FONT=Arial]You should disable Java if you haven't already.

Tools -> Options -> OpenOffice.org -> Java -> Java Options -> [ ] Use a Java runtime environment[/FONT]

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=avantgardaclue](to try and stop it crashing)[/QUOTE]
you have the 1.9.129 version right (openoffice>help>about)? you could update it to 2.0.1 using a custom repository. just search forum for howto update openoffice. that should fix things, hopefully...

---

### Post by avantgardaclue on 2006-03-07
[QUOTE=adamkane][FONT=Arial]You should disable Java if you haven't already.

Tools -> Options -> OpenOffice.org -> Java -> Java Options -> [ ] Use a Java runtime environment[/FONT][/QUOTE]

Not sure where i find this ;-) I can't get to anything in openoffice as it crashes  as soon as it opens!

---

### Post by avantgardaclue on 2006-03-07
[QUOTE=towsonu2003]you have the 1.9.129 version right (openoffice>help>about)? you could update it to 2.0.1 using a custom repository. just search forum for howto update openoffice. that should fix things, hopefully...[/QUOTE]

Nope, have OOo 2 

OOo2 was working ok but was annoyingly slow to boot up so i decided for run of the mill stuff to download Koffice.. this worked great until i needed to open a complex XLS file and kspread couldn't cope... open in OOo thought I, but no it keeps crashing! Hey ho, lets see if a re-installation works!

---

### Post by avantgardaclue on 2006-03-07
Well i tried uninstalling OOo 2, evidently it didn't still got old prob, opens then immediatly shuts! So installed OOo 1 which appears to work perfectly, so i guess that's what i'll be sticking with, what are the benefits of OOo2 over OOo1? 

Not to worry too much, i installed gnumeric spread sheet which appears to do EXACTLY what i needed in the first place!!!

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=avantgardaclue]Well i tried uninstalling OOo 2, evidently it didn't still got old prob, opens then immediatly shuts![/QUOTE]
try locating the user configuration files for openoffice in your home directory (something like ~/.openoffice2??) and delete the folder, launch openoffice2 again. I don't know where it is, "locate" could help? I don't have my ubuntu around, so I don't know where that folder is.

---

