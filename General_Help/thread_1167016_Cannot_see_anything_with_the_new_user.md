---
title: "Cannot see anything with the new user"
date: 2009-05-22
forum: General Help
---

### Post by oxhaksi on 2009-05-22
Hi,

i create a new user in ubuntu using command line and when i log in using that user i can only see the background picture and nothing else. can someone please help me? thank you

---

### Post by hexanol on 2009-05-22
You mean you can't see, for example, the top and bottom panels ?

---

### Post by oxhaksi on 2009-05-22
yes i cannot see them. just the mouse

---

### Post by hexanol on 2009-05-22
Hum... I don't think I'll be able to help you, but could you post the output of "grep '*USER*' /etc/passwd" where *USER* is the username of the new user.

---

### Post by oxhaksi on 2009-05-22
i cannot get to the command line. as i said nothing is available.

---

### Post by hexanol on 2009-05-22
Well, there's no other user who can log correctly into your system ? To run this command, you don't need to do it as the "problematic" user.

Alternatively, when on the login screen, hit "Alt+Ctrl+F1" and log from here. I guess that, even for the problematic user, you should be able to get a shell session... (To return to the graphical login screen, hit "Alt+Ctrl+F7").

---

