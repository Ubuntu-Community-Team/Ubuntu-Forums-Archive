---
title: "Desktop in wrong directory"
date: 2009-08-06
forum: Desktop Environments
---

### Post by Da CalebMan on 2009-08-06
Hey guys,:( 

I've really messed up my Desktop, and I want to revert all Desktop settings back to factory. U see, I've accidentally clicked and dragged my Desktop folder into my 'Animation' folder. Not where it should be. And now, it won't drag back. The only place it can go, is a lower subfolder. For instance, Desktop directory used to be here: 

"/home/*user*/Desktop" ...right?... Now it's here:

 "/home/*user*/Media/Animation/Animations/Desktop"

What do I do!?:confused: I was thinking, well at least hoping, there was a configuration file that controls which folder the Desktop synchronizes with, so I could possibly move it up again, or that there could be some way to set my Desktop setting (Desktop only) back to factory, with out losing my apps and data. 

Pleeeeeeeeeeeeeeeeeeeeeeease help!!!

Sincerely, ~Caleb:(

---

### Post by sailthesea on 2009-08-06
If you open Places and right click Desktop and look in Properties it should show your full ownership so you can work out how to move it 
I know I have a problem shifting stuff around because the filing system is a bit confusing as long as are working in the Home directory you shouldn't have too much trouble

Edit : In the Nautilus window open a second window for Home and then drag the desktop from its wrong location Should have mentioned that first!

---

### Post by Hobgoblin on 2009-08-06
Do you have a /home/*user*/Desktop directory?

If not then simply creating an empty one will have that back to default, there is nothing stored in there other than desktop shortcuts.

What settings do you want to reset?

---

### Post by warp99 on 2009-08-06
Open a terminal and issue the following command:

```
sudo mv ~/Media/Animation/Animations/Desktop ~/
```

That will put the Desktop directory back in your /home/$user directory. If the ownership of the directory in incorrect then do the following:

```
sudo chown $user:$user ~/Desktop
```

Of course replace $user with your user name.

---

