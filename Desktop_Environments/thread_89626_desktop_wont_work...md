---
title: "desktop wont work.."
date: 2005-11-13
forum: Desktop Environments
---

### Post by sunrex on 2005-11-13
i dont know wtf i did, but now im just going into console mode when i bootup. what do i type to get back control of my KDE, GNOME, and such?

i mean omg.....all i did was restart!

---

### Post by Remmelas on 2005-11-13
after loging into the console, try ```
sudo /etc/init.d/gdm start
``` and see if that gets you back to X or an error message.

---

### Post by sunrex on 2005-11-13
..

im in console only mode...as in no gui..

---

### Post by aysiu on 2005-11-13
[QUOTE=sunrex]..

im in console only mode...as in no gui..[/QUOTE] Yes. And in that mode, log in. Then type the command suggested. You can also try the command ```
startx
``` or just pressing control-alt-F7.

---

### Post by sunrex on 2005-11-13
sudo /etc/init.d/gdm start

not defult..wouldent work

sudo /etc/init.d/kdm start

alredy running

startx

invailid comand

control alt f7

nothing happened...


any other ideas?

---

### Post by aysiu on 2005-11-13
If KDM is already running, control-alt-F7 should work. Maybe another control-alt-F#? I believe they run F1 to F7 and all the ones in between...

---

### Post by sunrex on 2005-11-13
ctrl alt f1-f12 nothing happened.

f2 - some words disapeared..thats it..

it feels like im in server only mode....could it be the bootup paramiters..what sould they be?

i really dont want to reinstall linux.

*edit*

there has to be somone here who can tell me wtf to do..i mean i got my dvds to play, my sound to work, and mpg's, alot of other crap..im not about to reinstall....

---

### Post by sunrex on 2005-11-13
hmm..i think the problem is in kde...

how do i make gdm my defult bootup?

---

### Post by sunrex on 2005-11-13
nvm ill just reinstall linux...but i was under the impression that linux wouldent be like windows in reinstalls like this.

---

### Post by IBLPNZIT on 2005-11-13
I feel Sunrex's pain...

I would also like some help getting the computer to book with the KDE GUI... I followed the /kdm and /gdm commands, and it tried to start it. But then it failed... So if anyone has any help, I'd love to hear from you.

---

### Post by SickTwist on 2005-11-13
If there is a problem with X, more information about the error might be contained in the log which is stored in /var/log/Xorg.0.log. In order to vew the last 20 entries of the log, run this command:

cat /var/log/Xorg.0.log | tail -20

Also, if you may wish to try restarting gdm with this command:

sudo /etc/init.d/gdm restart

Or if you are running Kubuntu, restart kdm with this command:

sudo /etc/init.d/kdm restart

Please post the contents of the X.org log here if you need help deciphering it.

---

### Post by sunrex on 2005-11-13
i just reinstalled...kde was getting old..i wanted to go back to gnome anyway for awhile at least..

well i was just a little pissed couse on windows i just happened to get rootkit...for those who DONT know what that means..its like the worst kind of spyware/virus you can get..its called root for a very good reson...

so i was just a little pissed off when linux failed on me....

but meh.

---

### Post by IBLPNZIT on 2005-11-13
Hey everyone,

GOOD NEWS!

The GUI does work...

I was trying to log in remotely, aka from another computer on the LAN.

Does anyone know why the VNC Viewer would not work?

(Remote Desktop is enabled)

Thanks for any help,

Joshua M. Goodwin

---

