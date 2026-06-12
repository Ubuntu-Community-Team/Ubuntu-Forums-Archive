---
title: "3D games wont open"
date: 2008-10-09
forum: Gaming &amp; Leisure
---

### Post by Jepperen on 2008-10-09
Hey

I cant open the 3d games i downloaded and installed. I have open all ohter games and applications.

Whats more strange is that i had no problem opening the 3D games yesterday. But yesterday the games was very laggy so i installed the newest graphic drivers today.

Anyone who can help me here?

---

### Post by Liviu-Theodor on 2008-10-09
This is from the advice even the video card manufacturers give: when this is happening, try not the latest driver, but one that is a little bit older. The reason is sometimes the newest is alpha or beta, while the other has been tested more thoroughfully.

---

### Post by neilengineer on 2008-10-09
> **Jepperen said:**
> Hey
But yesterday the games was very laggy so i installed the newest graphic drivers today.


Are you sure your graphical card support 3D?

What's the output of the following command:
$glxinfo|grep "direct rendering"

---

### Post by Liviu-Theodor on 2008-10-09
> **neilengineer said:**
> Are you sure your graphical card support 3D?
> **Jepperen said:**
> Whats more strange is that i had no problem opening the 3D games yesterday.

I will guess the videocard support 3D.

---

### Post by Jepperen on 2008-10-09
Yes it supports 3D. Its a ATI X1600 and i have played alot of diffent games in windows with it and as Liviu mentioned, it worked yesterday.

Liviu-Theodor your suggention didnt work, so i reinstalled Ubuntu, try the games without driver update, it worked! Then i installed the drivers, it worked! Now im installing the Ubuntu auto updates, which i think caused the problem last time, if so, i'll be back ;)

And thanks for your interest and answers.

---

