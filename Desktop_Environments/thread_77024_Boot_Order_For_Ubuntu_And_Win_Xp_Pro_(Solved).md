---
title: "Boot Order For Ubuntu And Win Xp Pro (Solved)"
date: 2005-10-16
forum: Desktop Environments
---

### Post by nit407 on 2005-10-16
i have installed ubuntu and win xp pro on my dell 700m. everything is working perfectly fine. the only thing i would like to know is that is it possible to change the default boot order from ubuntu to windows xp pro with a 3-5 sec time-out option which would give me the option of booting onto ubuntu when i want to? I tried going onto 'msconfig' in xp but nothing was there and I am not too familier with ubuntu/linux, so would appreciate any help i can get. thanks for your help in advance.:D 
-nit407

---

### Post by drummer on 2005-10-16
If you're using grub as your boot loader, I assume you are, do this:
In a terminal, ```
sudo gedit /boot/grub/menu.lst
```then find and edit these lines:

default   0
[change the 0 to the number in the list of OSs that WinXP is, starting counting from 0. To check which one it is, have a look at the end of the file and there are the OS entries, in separate blocks/paragraphs each starting with 'title', just count them, including the 'other OSs' entry. If you just did a standard Ubuntu install, Windows should be 5th in the list, so put a 4 in place of the 0.]

timeout   10
[change the 10 to the time in seconds you want for the timeout before Windows loads]

#hiddenmenu
[make sure there's a '#' at the start of this line to display the boot loader menu, otherwise you press ESC to show the menu at boot]

Save the file and you're done.
Hope that was clear enough..

---

### Post by nit407 on 2005-10-16
[QUOTE=drummer]If you're using grub as your boot loader, I assume you are, do this:
In a terminal, ```
sudo gedit /boot/grub/menu.lst
```then find and edit these lines:

default   0
[change the 0 to the number in the list of OSs that WinXP is, starting counting from 0. To check which one it is, have a look at the end of the file and there are the OS entries, in separate blocks/paragraphs each starting with 'title', just count them, including the 'other OSs' entry. If you just did a standard Ubuntu install, Windows should be 5th in the list, so put a 4 in place of the 0.]

timeout   10
[change the 10 to the time in seconds you want for the timeout before Windows loads]

#hiddenmenu
[make sure there's a '#' at the start of this line to display the boot loader menu, otherwise you press ESC to show the menu at boot]

Save the file and you're done.
Hope that was clear enough..[/QUOTE]


thx ... ill try it and let you know how it goes...:razz:

---

### Post by nit407 on 2005-10-16
It worked...thanks for your help.. i was able to change the boot order as well as the boot preference.
0nit407:p

---

### Post by drummer on 2005-10-17
No problem, glad I could help.

---

### Post by malaprohibita on 2005-10-30
big thumbs up for this post!

---

### Post by drummer on 2005-10-30
:grin:

---

### Post by Sumint620 on 2006-11-28
real sorry to bring up a dead topic but i didn't want to start another one. i am too looking at changing the boot order however i don't have the Default or Timeout lines in my menu.lst . anybody have ideas on what i should do?

---

### Post by Sumint620 on 2006-11-28
alright i got it. disregard this thread now

---

### Post by Jamppa-90 on 2006-12-16
bumb

i just installed ubuntu 6.10, and i have no idea what is a "terminal", how to access it, and how to modify it... pls help...
sudo gedit /boot/grub/menu.lst -> do i have to type this somewhere? or what? step-by-step instuctions would be nice, i am in a hurry, please help.

---

