---
title: "KDE 4.2 on 8.04 broken after intalling updates"
date: 2009-04-06
forum: General Help
---

### Post by Azazel on 2009-04-06
I had been keeping up with updates and then all of a sudden there were nearly 200 updates. After installing and rebooting there is no desktop. The login screen seems fine, but after logging in there is nothing but black. I can press alt+f2 to run programs like firefox etc... I tried reinstalling some packages like kde, kubuntu desktop and some other related packages. I dont know whats wrong or what to do! Thanks in advance for any help.

---

### Post by kuja on 2009-04-06
Try creating a new user and logging in with it.

---

### Post by Azazel on 2009-04-06
the new user works just fine. so its just my user data thats messed up? how do i fix this?

---

### Post by Azazel on 2009-04-06
would it be easier to start with a new user rather than trying to fix the old one?

---

### Post by kuja on 2009-04-06
> **Azazel said:**
> would it be easier to start with a new user rather than trying to fix the old one?

Probably not really. What I would do would be back up or otherwise move your files that you need out of your home folder (taking care not to take the config files along for the ride, seeing as we don't know which one it is). 
Next, delete your home folder.
Re-create your home folder.
Copy your files back.

---

### Post by 3Miro on 2009-04-06
There is a .kde folder in your old user's folder. Unless you saved something in it (and should not have done that), it should be safe to delete it. Then trying to log in again. At most you will loose your plasma settings, all the files/installed programs and program specific settings should be fine.

---

### Post by Azazel on 2009-04-07
I figured the problem was in the kde folder but I didnt know a new folder would be generated if it was deleted. Deleting the folder and logging back in solved the problem, I now have a desktop. I did loose a ton of settings but at least it works. Thanks for you help!

---

