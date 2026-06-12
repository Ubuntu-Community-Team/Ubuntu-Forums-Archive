---
title: "KDM errors - Should it be concerned?"
date: 2005-05-09
forum: Desktop Environments
---

### Post by Vizariel on 2005-05-09
Ello.. everytime I logged in to KDE, there will be a quick pop out window appearing then disappearing immediately. I thought it was kinda weird since my last installation hasnt got that. I checked my logs and here is the error.

May  9 18:46:56 localhost kdm[6632]: X server for display :0 terminated unexpectedly
May  9 18:47:06 localhost kdm_greet[7796]: Can't open default user face

Is there any way to fix it or it could just let it be?

---

### Post by johnprgr on 2005-05-10
You could let it be, it doesn't hurt anything.

However if your inclined to fix it you can add pictures to your login in the Control Center (kcontrol).  It is under "System Adminstration" and "Login Manager".  There is a button at the bottom "Adminstrator Mode", you must be in admin mode to change the picture initially.  On the "Users" tab on the far right side is "User Image Source" and "User Images".  Changing "User Image Source" to "Admin,user" or "User, admin" will make it so you can change images without being the administrator.  Under "User Images" you select your user id and click the square under that to select a picture.

Hope this helps.

---

### Post by ltmon on 2005-05-10
I used to see a pop up on login to KDE when using a slow computer.  The popup was something to do with scanning the trash bin.  Upgrading the computer caused this to either dissapear completely or be fast enough that I just don't see it. 

Either way I don't think it's a bug or a problem, I think it's just that kde is set up to show a file transfer dialog for file operations that take greater than a certain predefined amount of time.

---

