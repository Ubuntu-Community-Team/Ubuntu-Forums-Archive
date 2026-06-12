---
title: "openoffice"
date: 2005-04-15
forum: Desktop Environments
---

### Post by jhands on 2005-04-15
i want to install openoffice.org 2.0 beta. but when i try to uninstall openoffice 1.1.3 from ubuntu, it also wants to uninstall gnome-desktop with it. is there any way i can uninstall 1.1.3 and install 2 beta in its place?

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=jhands]i want to install openoffice.org 2.0 beta. but when i try to uninstall openoffice 1.1.3 from ubuntu, it also wants to uninstall gnome-desktop with it. is there any way i can uninstall 1.1.3 and install 2 beta in its place?[/QUOTE]

You could make a note of all the packages apt wants to remove along with openoffice 1.1.3 and then reinstall them after you've removed openoffice 1.1.3. Or, you could just leave openoffice 1.1.3 installed, in case openoffice.org 2 beta proves flaky. Just remember to do **sudo apt-get install openoffice.org2 openoffice.org2-gnome** if you want the full integration.

---

### Post by jhands on 2005-04-15
it wants to uninstall ubuntu-desktop. i think if that gets uninstalled i wont be able to use ubuntu without reinstalling it. and i also dont want openoffice 1.1.3 left behind. thats y i want to install 2.0 beta.

---

### Post by denzilla on 2005-04-15
When Ooo 2.0 gets released, will it update like other packages or will it be somewhat complicated like it is now?

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=jhands]it wants to uninstall ubuntu-desktop. i think if that gets uninstalled i wont be able to use ubuntu without reinstalling it. and i also dont want openoffice 1.1.3 left behind. thats y i want to install 2.0 beta.[/QUOTE]

Try the following steps:

1. Hit CTRL+ALT+F1 to get to a console.
2. Login.
3. Do **sudo /etc/init.d/gdm stop** to disable X
4. Do **sudo apt-get install openoffice.org2 openoffice.org2-gnome**
5. Do **sudo apt-get --purge remove openoffice.org**
6. Do **sudo apt-get install ubuntu-desktop**
7. Do **sudo /etc/init.d/gdm start && exit**. (Restart X)

You should have your new OpenOffice.org 2 beta, ubuntu desktop, and have gotten rid of the old openoffice with these seven steps.

---

### Post by danip on 2005-04-16
you can uninstall gnome-desktop and everything will still work.  I was told this is just a superflous package.  I uninstalled it when i removed evolution i believe.

---

### Post by jhands on 2005-04-16
Stormy Eyes, i did just as you told me but i skipped the 6th step just to see if ubuntu would run without the ubuntu-desktop package and it does. so thats well. the only problem is that when i got to Applications>Office, there are noe icons for openoffice2 and when i went to synaptic, it doesnt show openoffice 2 as installed. its either an error with synaptic or really  openoffice2 did not install even though i saw the install process running.  maybe it is installed but isnt show in the Office menu. if that is the case then can u please tell me how to add all the shortcuts in that menu.

---

### Post by denzilla on 2005-04-16
I know that sometimes after installing a program, it either showed a white box in place of the icon or didn't list the item at all till I rebooted, then all was fine.

---

### Post by Stormy Eyes on 2005-04-16
[QUOTE=jhands]Stormy Eyes, i did just as you told me but i skipped the 6th step just to see if ubuntu would run without the ubuntu-desktop package and it does. so thats well. the only problem is that when i got to Applications>Office, there are noe icons for openoffice2 and when i went to synaptic, it doesnt show openoffice 2 as installed. its either an error with synaptic or really  openoffice2 did not install even though i saw the install process running.  maybe it is installed but isnt show in the Office menu. if that is the case then can u please tell me how to add all the shortcuts in that menu.[/QUOTE]

Try reinstalling ubuntu-desktop and then do "killall gnome-panel".

---

### Post by jhands on 2005-04-16
well i just installed openoffice 2 from synaptic and now everthing works real good. :razz:

---

### Post by Simian on 2005-04-16
[QUOTE=jhands]well i just installed openoffice 2 from synaptic and now everthing works real good. :razz:[/QUOTE]

I installed OpenOffice 2 with synaptic and removed the old one, but i had no language support. No spellchecker etc. I tried everything to get working but had no luck. Then I reinstalled the old OpenOffice along side OpenOffice 2 and now then spell checker works. I was wondering if you had this problem?

---

### Post by jhands on 2005-04-16
spellchecker works fine 4 me

---

### Post by oli on 2005-05-05
Could someone tell me how to uninstall ubuntu linux from my laptop so as to install windows 2000 instead.

Thanks


Oli

---

### Post by jiro on 2005-05-05
[QUOTE=oli]Could someone tell me how to uninstall ubuntu linux from my laptop so as to install windows 2000 instead.[/QUOTE]

Just install Win2K. Part of its install process is to reformat your hard drive - bye bye, linux! (but make sure you back up any files you might want to save onto a CD or something...

---

