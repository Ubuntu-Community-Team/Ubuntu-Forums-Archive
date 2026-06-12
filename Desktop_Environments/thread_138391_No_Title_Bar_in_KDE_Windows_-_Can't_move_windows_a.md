---
title: "No Title Bar in KDE Windows - Can't move windows around"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Ether on 2006-03-01
Hi guys.
i recently installed the KDE packages onto my previous Ubuntu 5.10 Install using the Kubuntu 5.10 cd and appeared to have no problems.
however all the program windows appear without the top name bar - the first row is automatically File Edit Etc. and i am unable to move them around the screen.
also i cannot seem to open any program that needs the sudo password filled in, on entering it the password window closes but nothing happens.
i've tried changing the theme and style but it makes no difference.

Does anyone have any ideas on whats happening?

---

### Post by ltmon on 2006-03-01
Sounds like you're missing a package.

Make sure you 'apt-get install kubuntu-desktop', and nothing is missing.  It could be the 'kwin' package that you need.

L.

---

### Post by Jucato on 2006-03-01
You could also try to check your window decoration: KControl > Appearance and Themes > Window Decorations.

Oh btw, with or without borders/window titles, you can always move windows by pressing Alt+Left Mouse button anywhere on the window and dragging it to move.

---

### Post by Sharkscott on 2006-03-01
I had similsr and more problems than you when I tried that some time ago. I was a lot greener behind the ears too. :-)

I would see if you can do an update to the KDE stuff, it might show the packages you need or update the ones you need to update. 

After reading the last sentence, I am not even sure I unterstand it. :-)

---

### Post by Ether on 2006-03-02
Cheers, i thought it was probably a package issue.

and thanks Fenyx for the shortcut :)

---

