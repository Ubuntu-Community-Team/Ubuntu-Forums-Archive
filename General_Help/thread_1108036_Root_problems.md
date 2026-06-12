---
title: "Root problems"
date: 2009-03-27
forum: General Help
---

### Post by sanjeevpunj on 2009-03-27
[SOLVED]I have an admin account which allows me to install programs. When I click the "Users and Groups" under System/Administration, I can see another user (root) which I cannot selct or modify even as admin. Is this normal? Also, when I select my admin account, and click unlock, I am unable to unlock, I get a message "unable to authenticate. an unexpected error has occured" what does this mean? What do I need to do, to be able to modify "users and groups" Also, under Privileges tab (for admin) the box for function "Administer the System" is not checked. The entire tab is greyed out, I cannot check the required boxes.

---

### Post by coffeecat on 2009-03-27
> **sanjeevpunj said:**
> Also, when I select my admin account, and click unlock, I am unable to unlock, I get a message "unable to authenticate. an unexpected error has occured" what does this mean?

That shouldn't be happening if your 'admin' account is the first created account.

Question: is the admin account a first created account or a secondary one? If it is a secondary one it may be that insufficient privileges have been assigned to it. Although, I would have thought that if you can install programs you should be able to do other admin type things with it.

If this is a secondary account, log in with the first created account (which has full admin privileges). Then go to Users and Groups, unlock and modify your so-called admin account.

But if your admin account is your first created account, I have no idea what has gone wrong.

---

### Post by sanjeevpunj on 2009-03-27
You are right! The admin account I created was an afterthought, and the first created account had all the privileges. Sorted it out now, I have enabled/unlocked and checked the required boxes. Wow thanks, good thinking on your side.Cheers.

---

### Post by coffeecat on 2009-03-27
Glad it's sorted. One thing though. Don't unprivilege your first account (if you were thinking of doing so) until you have made sure that your admin account is fully privileged. I seem to remember a few threads where people had managed to unprivilege their first account without creating an administrator account. Goodness knows how, or why. You can imagine the consequences. OOps! :oops:

That was a couple of years ago, so I don't know whether the devs have put in a failsafe now to stop you being able to do that. And I'm not going to try it out to see either. :p

---

### Post by sanjeevpunj on 2009-03-28
You dont need to try that out. Last time when I installed ubuntu, I had done that mistake, and I do remember it. I am glad you reminded me too. Cheers.

---

