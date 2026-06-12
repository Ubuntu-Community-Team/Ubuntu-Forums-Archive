---
title: "[SOLVED] switching user"
date: 2007-12-02
forum: Desktop Environments
---

### Post by discoade on 2007-12-02
Hi Guys

my problem is... When i switch user by clicking in my name in the top panel it switches to my wifes logon screen. Perfect!  But when we try to switch back using the same method ie:clicking on her name by the clock we just get a white screen and nothing happens resulting in a system restart!

if we use the "switch user log out shutdown" button and log out first it works a treat!

any ideas?:(

---

### Post by ItsManaged on 2007-12-03
Have you tried using <Ctrl> <Alt> <Fn>  (Fn = F7, F8, F9 etc.) to switch between users?

The first logged in user is at F7, the second in my experience is F9, so if you <Ctrl> <Alt> <Fn> you should be able to switch between your user and your wifes without needing the panel button. 

If this works ok, then I suggest your user config files are corrupt somewhere. Try creating another user and see if logging into this test user produces the same results.

---

### Post by discoade on 2007-12-04
sorry for the delay in replying been away!:popcorn:

The ctrl / alt/  fn thing works but i still have the same problem when when using the user names in the top panel. it only happens when switching from my wifes account back to mine! unless im logged out! then its fine!! :confused:

Any thaughts?

---

### Post by discoade on 2007-12-04
Any one care to comment before i abandon this thread?

---

### Post by mannheim on 2007-12-05
This is a workaround that works for me:

Right-click on your name in the panel, and select "Preferences ..." from the menu there. You will get a "User Switcher Preferences" dialog. **Un**check the item "Lock screen after switching users". Do the same from your wife's account.

This may not be appropriate in an environment where you really want to lock your screen; but for a home computer it may not matter to you. Anyway, this gets rid of the white-screen problem on my machine.

(I think another workaround is to turn off Desktop Effects. I've also read that this is a problem with nvidia graphics cards and the non-free driver, but I'm not sure.)

---

### Post by discoade on 2007-12-05
Your right it does work!   thanks for the advice  ill see how i get on like that for now!:guitar:

Many thanks

---

