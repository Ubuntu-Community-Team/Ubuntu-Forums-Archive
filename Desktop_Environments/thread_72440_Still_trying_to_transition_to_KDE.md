---
title: "Still trying to transition to KDE"
date: 2005-10-06
forum: Desktop Environments
---

### Post by twoseids on 2005-10-06
Two things at least:

1, When I was using Gnome, I could click on "Log Out" from my main menu and it would give me the dialogue "Shut Down, Reboot," etc. Now that I'm using KDE, it only brings me back to the login screen and then I say shut down and have to answer "Shut Down or Restart". And when it's shutting down and showing all the text stuff of what it's doing, it says something like "Turning off Gnome Display Manager" and then "Gnome Display Manager not running." Anyway, just thought I'd see if anyone has a clue on this - I just wanna be able to shut down straight from my main menu without all the hassle!

2. Is there a KDE equivalent for "System Monitor"?  While I'm on that, is there a site or post that tells you all the KDE equivalents for Gnome stuff?

3. When Breezy is released, will there be a separate Kubuntu release? Or will I just have to download the KDE stuff after getting Breezy?

Thanks!

---

### Post by Knome_fan on 2005-10-06
1. Make sure to use kdm, not gdm and you will have the options on log out.
(sudo dpkg-reconfigure kdm and then choose kdm)

2. Yes, simply press Ctrl+Esc

3. There will be a kubuntu release:
[www.kubuntu.org](www.kubuntu.org)

---

### Post by twoseids on 2005-10-06
[QUOTE=Knome_fan]1. Make sure to use kdm, not gdm and you will have the options on log out.
(sudo dpkg-reconfigure kdm and then choose kdm)
2. Yes, simply press Ctrl+Esc
3. There will be a kubuntu release:
[www.kubuntu.org](www.kubuntu.org)[/QUOTE]
Thanks, that helps a lot with questions #2 and #3.
But with the first question:  I AM using KDM. Even when I do Ctrl + Esc I can see KDM. But I still have to go through a bunch of rigamarole to shut down my computer.  Hmm...

---

### Post by Knome_fan on 2005-10-06
[QUOTE=twoseids]Thanks, that helps a lot with questions #2 and #3.
But with the first question:  I AM using KDM. Even when I do Ctrl + Esc I can see KDM. But I still have to go through a bunch of rigamarole to shut down my computer.  Hmm...[/QUOTE]

Sorry for not reading your first point thoroughly.
That you don't get a logout dialog is really strange, as you should normally get it automatically when you are using kdm (are you really sure it is kdm?).

I really don't know what's wrong exactly, but did you take a look at the control center?
Under system administration you can set up your login manager. Could you check under the shutdown tab if you have the permission to shutdown your computer?

---

### Post by twoseids on 2005-10-07
[QUOTE=Knome_fan]Sorry for not reading your first point thoroughly.
That you don't get a logout dialog is really strange, as you should normally get it automatically when you are using kdm (are you really sure it is kdm?).

I really don't know what's wrong exactly, but did you take a look at the control center?
Under system administration you can set up your login manager. Could you check under the shutdown tab if you have the permission to shutdown your computer?[/QUOTE]
Well, when I do Ctrl + Esc I see kdm running, and no gdm.

And yeah, under the Shutdown tab, it says everybody can shut down.

Maybe this isn't really a big problem, since I'll be installing Kubuntu Breezy next week, and hopefully everything will be installed right from the start?

---

### Post by Seth on 2005-10-07
Yes, definitely.

---

### Post by stimpack on 2005-10-07
Make sure both 'Confirm Logout' and 'Offer shutdown options' are checked in Session Manager.

KMenu -> System Settings -> User Account -> Session Manager

or

System Menu -> Settings -> KDE Components -> Session Manager

---

### Post by twoseids on 2005-10-07
[QUOTE=stimpack]Make sure both 'Confirm Logout' and 'Offer shutdown options' are checked in Session Manager.

KMenu -> System Settings -> User Account -> Session Manager

or

System Menu -> Settings -> KDE Components -> Session Manager[/QUOTE]
Bingo! That was it - neither one was checked.

Thanks stimpack!

---

