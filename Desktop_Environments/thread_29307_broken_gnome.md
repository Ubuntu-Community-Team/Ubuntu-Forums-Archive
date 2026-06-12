---
title: "broken gnome"
date: 2005-04-23
forum: Desktop Environments
---

### Post by atf487 on 2005-04-23
I installed warty 2 months ago, and in early march decided to switch to hoary, which was then a beta. Anyway, along the line after i installed kubuntu, gnome decided to stop working. Now, I've used kde so I never thought to fix it, but I want gnome working again and I don't know how to reinstall everything.

What happens is that after the Ubuntu splash screen comes up, it tries to load the taskbar and just cant do it, eventually coming up with just an empty error box and i have to ctrl+alt+backspace to get back to kdm.

any suggestions?

---

### Post by sfw5000 on 2005-04-23
Logging in as the same user with both KDE and Gnome can cause problems. Try making a different user for gnome than KDE... You can chmod your /home dir so that both users have access to all the files, but generally things can get ugly switching between those two desktops with the same uer.

---

### Post by atf487 on 2005-04-24
[QUOTE=sfw5000]Logging in as the same user with both KDE and Gnome can cause problems. Try making a different user for gnome than KDE... You can chmod your /home dir so that both users have access to all the files, but generally things can get ugly switching between those two desktops with the same uer.[/QUOTE]

alright, ill try that. thanks.

---

### Post by atf487 on 2005-04-25
[QUOTE=atf487]alright, ill try that. thanks.[/QUOTE]
 didnt work. is there anyway to totally reinstall all of gnome and such easily? the packages arent connected in synaptic, id have to do one by one for the most part.

---

### Post by sfw5000 on 2005-04-25
So you logged in as a totally new user and it didn't work? What kind of error message did you get?

Reinstalling gnome is definitely not in the quick-and-easy category, but you really should not have to reinstall... When you try to log in do you see anything or just a blank screen? You say there is an empty error box -- does it say anything? Is there a "click for details" option?

---

### Post by atf487 on 2005-04-27
[QUOTE=sfw5000]So you logged in as a totally new user and it didn't work? What kind of error message did you get?

Reinstalling gnome is definitely not in the quick-and-easy category, but you really should not have to reinstall... When you try to log in do you see anything or just a blank screen? You say there is an empty error box -- does it say anything? Is there a "click for details" option?[/QUOTE]

no, its totally blank and i cant click anything to make it disappear. i have to ctrl + alt + backspace to get out of it.

when i try to log in, i see the ubuntu screen and it seems to load everything, then i see the taskbar quickly jump and disappear again, after awhile it just gives the error message. 

i tried logging in with a new user, too, but it would just back out to gdm after i tried to do it.

---

### Post by tread on 2005-04-27
Well, you should be able to log in to both gnome and kde .. maybe not at the same time, but if you log out of kde and log in again in gnome that should work!

Try deleting (when I say deleting, I mean move into a temp directory) you gnome config files, and then start gnome. If it works you should then be able to setup stuff as you like it again, or incrementally move your older settings back.

---

### Post by atf487 on 2005-04-27
[QUOTE=tread]Well, you should be able to log in to both gnome and kde .. maybe not at the same time, but if you log out of kde and log in again in gnome that should work!

Try deleting (when I say deleting, I mean move into a temp directory) you gnome config files, and then start gnome. If it works you should then be able to setup stuff as you like it again, or incrementally move your older settings back.[/QUOTE]

ive tried logging from one to another; doesnt work.

how would i clear all my gnome config files? i dont care to keep em.

---

### Post by tread on 2005-04-27
Search in your home directory for .gnome, .gtk types of files .. 
I dont know all the folders involved though, so this may take some searching/trial and error.

---

### Post by atf487 on 2005-04-29
[QUOTE=tread]Search in your home directory for .gnome, .gtk types of files .. 
I dont know all the folders involved though, so this may take some searching/trial and error.[/QUOTE]
 yay! i cleared .gconf and .gnome2 from my home directory and its working, sorta.

thanks.

---

