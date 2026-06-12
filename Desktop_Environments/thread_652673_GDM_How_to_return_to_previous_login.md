---
title: "GDM How to return to previous login"
date: 2007-12-29
forum: Desktop Environments
---

### Post by akwatve on 2007-12-29
I have GDM with KDE (Yeah I know its a weird combo but I have it). I was using GDM for quite a few months before needing to have multiple accounts and multiple sessions. I recently faced a peculiar problem in GDM.

Suppose I have two accounts A1 and A2. If I do "switch user" from A1 and come back at the login screen, How do I log back in to A1. I dont see any option which lets me do that.
KDM has that option on the main login screen. But I didnt see it on GDM's login screen (the "options" menu does not have it). This is kinda weird...

Further, when I login in to A1 (to create multiple sessions) My screen just goes "Ubuntu Red" (or brown whatever shade it is) and nothing happens. In fact I have to kill Xserver to do anything useful after that.. :-(

Can anyone help me... Am I doing anything wrong ? I don't want to switch back to KDM....

Thanks,

---

### Post by x1a4 on 2007-12-30
Ctrl+Alt+F7 should do the trick.  To switch back to the second one it'll be Ctrl+Alt+F8 or F9 etc.  Also running switch user again will give you a list of logged-in users you can switch to.

---

### Post by akwatve on 2008-01-08
That worked ....

Thanks a lot.
But I find it quite strange that there is no option in the login manager to do it....Isn't that weird ?

---

### Post by x1a4 on 2008-01-08
> **akwatve said:**
> But I find it quite strange that there is no option in the login manager to do it....Isn't that weird ?

It is possible if you use a theme with a face browser (both standard and plain)

---

### Post by akwatve on 2008-01-13
Even with a face browser it is not possible. But I found something interesting.... 
If we have only one locked session and we want to go back to it , we can just click "OPTIONS"-->"QUIT" 
But if we have multiple users logged in, this too becomes crappy as we dont get to choose which session we want to resume (we have to go to the sessions which comes up and again choose "switch user" to select desired session).

The more serious issue though is when u "switch user" from a "root" login, It is not locked... so if any other user selects to go back to original sessions he is allowed to do so without having to type the password. May be this is because root is by default disabled in ubuntu. Is there any way to fix this ? Or is it that the ubuntu developers have ignored this  assuming no-one will ever enable root login...

---

