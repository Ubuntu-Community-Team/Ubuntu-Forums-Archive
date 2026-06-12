---
title: "Kubuntu Edgy menu locked?"
date: 2006-11-29
forum: Desktop Environments
---

### Post by x64Jimbo on 2006-11-29
I have been trying to figure this out but nothing is coming to me. I have sole ownership over my home directory, but if I try to change a menu item (change its command, alter it in some way) i can save the menu and it appears to take, but then it just reverts as soon as I close the editor. Is there a setting somewhere that I don't know about?

---

### Post by aysiu on 2006-11-29
Do you have ownership of all the subdirectories as well? Particularly ~/.config and ~/.kde? You may want to have a look.

---

### Post by x64Jimbo on 2006-11-29
Yeah. I did a recursive chown just to be sure.

---

### Post by aysiu on 2006-11-29
Have you tried creating a new test user (one you can delete later, of course) and seeing if that test user is also unable to edit the menu?

---

### Post by x64Jimbo on 2006-11-29
Trying that now...

---

### Post by x64Jimbo on 2006-11-29
OK so test user can edit menu items, but I still cannot. Weird.

---

### Post by aysiu on 2006-11-29
I know you've done a recursive ownership change already, but what happens if you move those folders? ```
mv ~/.config ~/.config.old
mv ~/.kde ~/.kde.old
``` Are you afterwards able to edit your KMenu?

---

### Post by x64Jimbo on 2006-11-29
I'll give that a try...

---

### Post by x64Jimbo on 2006-11-29
No difference.

---

### Post by aysiu on 2006-11-29
Can you try logging out and then logging back in again after the *mv* commands? Maybe that'll make a difference?

---

### Post by x64Jimbo on 2006-11-29
I copied them while logged out.

---

### Post by aysiu on 2006-11-29
Copied? You mean moved, right?

Well, if moving them didn't help... 

How about this? ```
mv ~/.local/share/applications ~/.local/share/applications.old
mkdir ~/.local/share/applications
```

---

