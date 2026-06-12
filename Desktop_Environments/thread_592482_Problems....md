---
title: "Problems..."
date: 2007-10-26
forum: Desktop Environments
---

### Post by Veevose on 2007-10-26
hello, i have some problems with installing the login image.
I tryed to install gdmsetup but it says that i have to be a root user to do that...thats the error i get when i try to install a login with gdmsetup, lil' help please i am a beginner.

---

### Post by taurus on 2007-10-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jfordwashere on 2007-10-26
Did you try sudo gdmsetup? Or, alternativly goto System->Administration->Login Window

---

### Post by divague on 2007-10-26
Have you tryed going to the system menu->Administration->Login window
write your password, and in the local tab, you can change the login image

---

### Post by Veevose on 2007-10-26
yes i can change the login image but i cant install the one i have on desktop.. i press install and open the bluswirl file witch is the login image and nothing appears its blank...

---

### Post by Veevose on 2007-10-26
> **jfordwashere said:**
> Did you try sudo gdmsetup? Or, alternativly goto System->Administration->Login Window

sudo gmdsetup >>command not found ??!!

---

### Post by jfordwashere on 2007-10-26
The "which" command tells you where things are on the system

which gdmsetup

replys:
/usr/sbin/gdmsetup

So:
sudo /usr/sbin/gdmsetup

---

### Post by Veevose on 2007-10-26
hmm...ok that comand opens the main window with the optins for login image.. i click add  then it redirects to to select the image then i select the folder with the image then i press install and nothing happens\

---

### Post by jfordwashere on 2007-10-26
Unless I'm mistaken, you can't just add any image as a login screen... they have to be in a special format.

If you open the synaptic package manager and add the "gnome-art" package this will add a icon called "Art Manager" under System->Preferences. That app will have a bunch of login screens that you can choose from, and download in the proper format

---

