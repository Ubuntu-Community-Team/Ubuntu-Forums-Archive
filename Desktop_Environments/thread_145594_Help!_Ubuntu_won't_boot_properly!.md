---
title: "Help! Ubuntu won't boot properly?!"
date: 2006-03-16
forum: Desktop Environments
---

### Post by user1397 on 2006-03-16
I turned off my computer, took out my graphics card and when i turned the pc on again, the ubuntu sign appeared and then it goes to that blue/gray scrren and when i get out of that it's just the black screen and it prompts me:
Ubuntu 5.10 "Breezy Badger" <my computer name> tty1

<my computer name> login: <my account>
Password:

What happened just because I took my graphics card??

---

### Post by Ramses de Norre on 2006-03-16
You use another video card now?
You will need to change the driver in /etc/X11/xorg.conf then.

---

### Post by user1397 on 2006-03-16
Thanks for the reply,
I actually have no graphics card installed now.
So what could I do???

---

### Post by Ramses de Norre on 2006-03-16
?? you mean you're using your onboard? That needs the right drivers too:) vesa will work for all graphic cards normally. You can then log in and go search which one is the best for you type.

---

### Post by Lord Illidan on 2006-03-16
Giving us some motherboard details would help too.

---

### Post by user1397 on 2006-03-16
Sorry but I'm kind of a noob so...
What is vesa and how do I go about getting to it?

---

### Post by Ramses de Norre on 2006-03-16
Vesa is a graphic card driver.
[http://www.ubuntuforums.org/showpost.php?p=783606&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=783606&postcount=2")

---

### Post by user1397 on 2006-03-16
Would reinstalling the graphics card make it boot normally?

---

### Post by Ramses de Norre on 2006-03-16
Yes, if you didn't allready changed drivers.

EDIT: didn't think of it yet: run sudo dpkg-reconfigure xserver-xorg with your onboard.

---

### Post by user1397 on 2006-03-16
ok thank you for the support
i'm just going to reinstall it:)

---

### Post by Ramses de Norre on 2006-03-16
Running the command I gave should make you're other one configured correctely. Do startx after it (if you want to try it.)

---

