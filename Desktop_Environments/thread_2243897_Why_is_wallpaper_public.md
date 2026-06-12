---
title: "Why is wallpaper public?"
date: 2014-09-11
forum: Desktop Environments
---

### Post by marexposed on 2014-09-11
Hello people, I'm using 12.04 and decided to have a desktop background image with a personal reminder to see all the time, but then discovered that background is shown at login screen where anyone logging into this computer can see it (only by clicking on my login name).
That behaviour doesn't sound right to me. How can I avoid my desktop background to be seen by any user of this computer? (or what can I use similar to a desktop background which won't be shown at login).
Thanks.

---

### Post by vasa1 on 2014-09-11
If having a user-specific wallpaper isn't possible, you could use Conky instead.

---

### Post by deadflowr on 2014-09-11
Open [s]Files[/s]Home Folder, go to the wallpaper, right click on it go to properties. then go to permissions tab, change permissions for group and other to none.
(Keep the owner permission as is, which should be create and delete)
Should now not show up in login.

Or at least this is how is worked before...

Hopefully both my directions make sense, and it actually still works this way.

Edit: I forget sometimes, but the file manager is called the Home Folder in 12.04.

---

### Post by grahammechanical on 2014-09-11
People will see your background wallpaper just by looking over your shoulder. Have you thought of that?

---

### Post by kostkon on 2014-09-12
> **deadflowr said:**
> Open [s]Files[/s]Home Folder, go to the wallpaper, right click on it go to properties. then go to permissions tab, change permissions for group and other to none.
(Keep the owner permission as is, which should be create and delete)
Should now not show up in login.

Or at least this is how is worked before...

Hopefully both my directions make sense, and it actually still works this way.

Edit: I forget sometimes, but the file manager is called the Home Folder in 12.04.
If that won't work, do the same for the whole Pictures folder, right click on the folder, click on Properties, then Permissions.

Another way to do it would be to move your wallpaper images in a folder outside the Pictures folder.

Hope that helps.

---

### Post by marexposed on 2014-09-12
Thank you, guys, I've changed "others" access to None on that file and it worked. What a community!
Graham: I've got a machine-gun behind my shoulder so to avoid that possibility, hehe.

---

### Post by deadflowr on 2014-09-12
> **kostkon said:**
> If that won't work, do the same for the whole Pictures folder, right click on the folder, click on Properties, then Permissions.

**Another way to do it would be to move your wallpaper images in a folder outside the Pictures folder**.

Hope that helps.
I forgot about that little nugget.
But then again I try to be organized, moving things around into other folders turns things topsy-turvy for me, Documents in Videos, Video on the Desktop, Chaos abound.:p
> **marexposed said:**
> Thank you, guys, I've changed "others" access to None on that file and it worked. What a community!
Graham: I've got a machine-gun behind my shoulder so to avoid that possibility, hehe.

All jokes aside, if the solution works for you, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). So that others may see if it can help them.

---

