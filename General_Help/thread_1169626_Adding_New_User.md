---
title: "Adding New User"
date: 2009-05-25
forum: General Help
---

### Post by rjpilla on 2009-05-25
Trying to add new user. Upon doing so the new user is added however when i go to login under the new user the screen goes black and I have to reboot, Ctrl - alt -backspace doesn't work.  Why is this happening?

---

### Post by rjpilla on 2009-05-25
Plz anybody.  Need to add users to this computer. After I add a new user, when I try to login under this new user it seems like its going into gnome as usual but screen remains blank, mouse cursor moves, but thats it. I then must reboot.

---

### Post by ceylonerana on 2009-05-25
Try to add users using the root terminal. When you reboot your computer go to Recovery console. Under that there is "Drop to Root Shell Prompt" and select it.
It sends you to the root prompt.
On that point you can add users using adduser or useradd commands.
Giving appropriate details to create those accounts then you can switch to that account using [FONT="Courier New"]su -username[/FONT].

Then you can start the GNOME using [FONT="Courier New"]startx[/FONT]

Hope this will work for you.

---

### Post by ceylonerana on 2009-05-25
Sometimes startx gives some uncomfortable things such as stuck the computer with some error messages.
On that kind of issues you can reboot using Alt+Ctrl+Del.
It will reboot the computer and you can log using normal procedure.

---

### Post by rjpilla on 2009-05-26
rebooting the computer is not my issue.  My problem is i cannot go into the new user, i get nothing but a black screen.

---

