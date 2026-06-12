---
title: "Whats the terminl expression for..."
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by JaK0121 on 2007-07-22
i have my computer partioned  with ubuntu and windows xp... 



whats the terminal expression for moving windos above ubuntu on the start up screen?

im pretty sure theres an expression to enter into the terminal.. then it takes u to a list..  then you can cut and copy the windows code and paste it above the ubuntu code so that windows is above ubuntu on the start up screen.  


any help is appreciated.. thank you

---

### Post by scxtt on 2007-07-22
sudo nano /boot/grub/menu.lst

---

### Post by pardesi on 2007-07-22
and change the expression before windows from 1to 0 and before ubuntu from 0 to 1

---

### Post by JaK0121 on 2007-07-22
How do i save the changes?      *begginner sorry*

---

### Post by Nythain on 2007-07-22
in nano i believe its control+o

---

### Post by scxtt on 2007-07-22
nano tells you how to do pretty much everything you'd need to do at the bottom of the screen (which is why i suggested using it instead of vi) ... WriteOut = save, which is control+o ... use control+x to exit ...

---

### Post by pjones0404 on 2007-07-22
you could also use sudo gedit /boot/grub/menu.lst

it is a little more user friendly in my opinion. nothing wrong w/ nano at all but some new people find gedit easier to use.

there is also an application called startup manager (SUM) that allows you to make these types of changes using a gui.

---

