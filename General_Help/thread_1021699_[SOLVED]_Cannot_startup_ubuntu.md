---
title: "[SOLVED] Cannot startup ubuntu"
date: 2008-12-25
forum: General Help
---

### Post by angrez on 2008-12-25
I'm using Ubuntu 8.10. I was messing around with compiz settings and I think I switched on 3D desktop setting. Now I can't boot up. It actually shows up to the point where my wallpaper appears and then it goes back to the login screen. I tried the fail safe gnome but it doesn't work. Can anyone show if there's a way to remove compiz through fail safe terminal or if there's a better way. I'm using a Dell 640M by the way.

---

### Post by pytheas22 on 2008-12-25
You could uninstall compiz by typing in the failsafe terminal:
```

sudo apt-get remove compiz
```

That would hopefully allow you to log in, and afterwards you could experiment with getting compiz working normally again.

If the command above doesn't help, we can try some other things; let me know.

---

### Post by angrez on 2008-12-25
Thanks for the reply pytheas22 but it didn't work. Also isn't fail safe similar to safe mode in windows? But why are the drivers attemptng to load?

---

### Post by pytheas22 on 2008-12-25
Sorry that didn't work.  Please try this:

In the failsafe terminal, type:
```

sudo adduser testuser
```

Follow the instructions on the screen for creating a new user account.

When you're done, end the failsafe session and try logging into Gnome again with username 'testuser' and the password that you just set for the new user.  Can you log in now?  If you can, it should be relatively easy to fix your problem.

I'm not sure why failsafe Gnome won't work, but this will help to pinpoint the problem and hopefully lead to a solution.

---

### Post by angrez on 2008-12-25
Ok I'm in testuser account. :)

---

### Post by pytheas22 on 2008-12-25
Alright, good.  Now try this: log back into the failsafe terminal as your normal user.  Then run these commands:
```

mv ~/.gnome ~/.gnome-OLD
mv ~/.gnome2 ~/.gnome2-OLD
```

Then try logging into Gnome as the normal user again.  Does this work?

---

### Post by angrez on 2008-12-25
I tried but it didn't work. It says No such file or directory when I keyed in mv ~/.gnome ~/.gnome-OLD
and when typed in mv ~/.gnome2 ~/.gnome2-OLD, But it didn't do anything.

---

### Post by pytheas22 on 2008-12-25
That's weird.  Are you using something other than Gnome--for example Kubuntu or Xubuntu?  What is the output of:
```

ls -a /home | grep -e gnome -e xfce -e kde
```

---

### Post by angrez on 2008-12-25
No I'm on Gnome. Pretty much everything I use is default. Right now 'm in testuser and I typed in ls -a /home | grep -e gnome -e xfce -e kde in terminal and it didn't do anything. I will have to log back into fail-safe terminal to key in to the admin account. I was wondering if I add a user who has admin priviledges, just like you showed me the testuser account and forget about the broken account or remove it somehow. I don't have any important data there so it doesn't matter.

---

### Post by abn91c on 2008-12-25
> **angrez said:**
> Thanks for the reply pytheas22 but it didn't work. Also isn't fail safe similar to safe mode in windows? But why are the drivers attemptng to load?
you also need to do sudo apt-get remove compiz-core

---

### Post by angrez on 2008-12-25
It works now! All I did was go into the testuser account, hit on the 'ON' button on the right top hand corner (the one for shutdown or restart) and choose my admin account and I got in. Then I chose to switch off compiz settings. And logged back in. Thanks pytheas22 for all the help.

---

### Post by pytheas22 on 2008-12-25
Strange that it works when you use the user-switch applet, but in any case I'm glad the problem is solved.

For security purposes, you may want to delete the testuser account if you're not going to use it anymore.

---

### Post by angrez on 2008-12-26
I think I'll leave the test account as it is. Anyway only I use the laptop so it's alright. Thanks

---

