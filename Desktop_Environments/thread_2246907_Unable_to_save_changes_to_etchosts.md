---
title: "Unable to save changes to /etc/hosts"
date: 2014-10-04
forum: Desktop Environments
---

### Post by Shimbou on 2014-10-04
Salutations, I'm trying to make a change to the /etc/hosts file to see if it fixes a problem i am having with league of legends but, when I try to edit it either through the text file directly or the terminal it wouldn't allow me to save changes to the file. Google search didn't turn up anything So, I'm wondering if anyone knows how to make it to where I have write privileges to the /etc/hosts file? Any help would be appericated and thank you in advance.
~Shimbou

---

### Post by kc1di on 2014-10-04
did you open the Text file editor as root? 
only root can make changes in the /etc/host file. 
you can open a text editor in a terminal with ```
sudo gedit
``` * replace gedit with your favorite editor. 
it will ask for your password.
then you should be able to edit the file and save it. 
good Luck.

---

### Post by Shimbou on 2014-10-04
I used nano tho, I'm not really sure how to save changes under that perticular editor.

---

### Post by steeldriver on 2014-10-04
In nano,you can use Ctrl-o to write **o**ut your changes and then Ctrl-x to e**x**it (there should be a summary of the special keys at the bottom of the nano screen)

---

### Post by Iowan on 2014-10-04
Saving w/ **nano** is a CTRL-o, but the key is having opened it 
```
 sudo nano /etc/hosts 
```

---

### Post by Shimbou on 2014-10-04
Thanks steeldriver, all it gave me at the bottom was ^0 I didn't know the ^ represented the shift key. ](*,).

Thanks as well, Iowan.

---

