---
title: "i locked myself out"
date: 2009-02-13
forum: General Help
---

### Post by finmanrushfan on 2009-02-13
in setting up permissions for the users on my computer, i enabled the root account, and took away my user account's admin privilages.  what i did not realize is that i cannot login as root to access the user configuration again.  how do i give myself configuration privilages through the shell?

---

### Post by Alterax on 2009-02-13
That's like opening a crate with the crowbar that was shipped inside.  Difficult, but not impossible.

Log in as yourself.  Once you have logged in, bring up a terminal.  Use the su command to change to root (hopefully you do have Root's password)

```
su
```

Then load up the users-admin applet with the following command:
```
users-admin
```

You'll be in the applet as root, where you can fix your permissions.

---

### Post by finmanrushfan on 2009-02-13
thanks, that worked perfectly.  i have very little linux experience, but i had previously been using fedora, where i believe using separate accounts was the best way to make sure you don't accidentally change things by mistake. from what i have gathered, this uses the sudo command to do that instead. is that about right?

---

### Post by Verd-Ear on 2009-03-18
> **finmanrushfan said:**
> in setting up permissions for the users on my computer, i enabled the root account, and took away my user account's admin privilages.  what i did not realize is that i cannot login as root to access the user configuration again.  how do i give myself configuration privilages through the shell?



  I was wondering if it only happened to me, luckily for me you guys solved this already.

  Thanks for posting, thanks for solving the issue, it helped me!

good job, keep it up!

---

