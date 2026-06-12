---
title: "Fast User Switcher user list."
date: 2009-09-08
forum: Desktop Environments
---

### Post by gfxguy on 2009-09-08
So the "Fast User Switcher" app allows you to list users to switch to, which is really great since my desktop is essentially just me with a couple of accounts.

One of my accounts has a low user ID because that's the ID that I use at work, so when I vpn into work and map drives... you can see how that works.

But because it's a low user ID, it won't show up on the user list, so I have to have another button the desktop bar (the logout button, which let's you "switch user" also).

The problem is that when it's a user with a "normal" ID, you can go right to that user and switch back and forth without any problems.  With this low number user, because you have to run the other switch user, doesn't always register correctly.

Now, I don't lose anything... I don't get lockups or anything, but sometimes I have to keep typing in the username and password to switch back and forth.  Sometimes it shows up on the list, sometimes it doesn't... nothing gets lost, even when I have to type in username and password, the session is still there.

It's just annoying.

So the question is if there's a way to configure the fast user switcher to include the lower number (still higher than all the system services) user.

Thanks.

---

### Post by SoftwareExplorer on 2009-09-08
What if you go to System->Administration->Login Window and then go to the users tab and add the user in the include box?

---

### Post by gfxguy on 2009-09-08
I get the error: 

The "username" user UID is lower than allowed MinimalUID.

Replace username with actual username.

The userID is over 500... well over the highest system user ID.  So the question, then, if I can't add it that way, is if there's a way to configure the MinimalUID to be lower.

EDIT: D'OH!  Thanks for your help... found it!  Thanks.

---

### Post by SoftwareExplorer on 2009-09-08
> **gfxguy said:**
> I get the error: 

The "username" user UID is lower than allowed MinimalUID.

Replace username with actual username.

The userID is over 500... well over the highest system user ID.  So the question, then, if I can't add it that way, is if there's a way to configure the MinimalUID to be lower.

EDIT: D'OH!  Thanks for your help... found it!  Thanks.

Your welcome. :)

---

