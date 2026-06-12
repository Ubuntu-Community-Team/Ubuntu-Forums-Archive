---
title: "No password user"
date: 2006-06-05
forum: Desktop Environments
---

### Post by TTT_travis on 2006-06-05
I want to create a user that doesn't have a password set, I am setting up a ubuntu computer for my family and they don't want to have to enter passwords. Currently I have GDM login setup so they just click their name and it prompts for a password, I want a way so they can just click their name it will log them it. I tried not setting a password but it doesn't let you. I also have tried editing /etc/shadow and taking out the hash but that also did nothing. I am sure someone has covered this.

---

### Post by johnc4510 on 2006-06-05
System>Addministration>Login Window
Click on Security, Click on Enable Automatic Login
This is for Gnome, are you using it or KDE?

---

### Post by eeclark on 2006-06-05
This is not exactly what you want but:

How to automatic login into GNOME (not secure)?

   1. Read General Notes
   2. System -> Administration -> Login Screen Setup
   3. Login Screen Setup

      General Tab -> Automatic Login ->
      Login a user automatically on first bootup (Checked)
      Automatic login username: Select "system_username"

---

### Post by TTT_travis on 2006-06-05
Yeah, but I don't want it to just automatically login to a user I want the login screen with 6 different users without passwords and when one clicks on his name it logins him in. This is for my family so they don't have to type in passwords when they're using it because it bothers them.

---

### Post by TTT_travis on 2006-06-07
I know linux aims at being secure but I am little surprised there isn't a way (that I know of) to not set a password for a user. I hope there is a way to do this some how.

---

### Post by eeclark on 2006-06-07
Good luck. I am waiting to hear an answer too. I set up 6.06 on my son's computer (he's 4) and trying to get him to enter a password...well you could just imagine.

---

### Post by bbala2020 on 2007-11-26
is there someone to help with this?  Even i need the same (users with no password)

---

