---
title: "help logging in."
date: 2009-04-10
forum: General Help
---

### Post by robnepper on 2009-04-10
Hi.  I have forgotten my password and user name for ubuntu.  How do I retrieve this info?

---

### Post by taurus on 2009-04-10
Boot into recovery mode from GRUB menu.  Then, drop into root shell and look it up to see what is your login name.

```
ls -la /home
```
Assuming your login name is rob, assign a new password for account rob with

```
passwd rob
```
Once you are done, reboot and see if you can log in as rob with the new password.

```
exit
```

---

### Post by Michael.Godawski on 2009-04-10
hi robnepper,


how did that happen, I mean how did you manage to forgot both: the username and the password? :confused:

---

### Post by Ericyzfr1 on 2009-04-10
You forgot both?

---

### Post by robnepper on 2009-04-10
See, my friend installed it for me on a second hard drive.  He is no longer around and we moved shortly after he did it. I had my passwords on a piece of paper and they were lost.  My wife, not being sure of this whole " new OS" thing, wanted the old OS with all of her familiar things on it so I haven't been running Ubuntu for quite awhile.  Now that I think I have figured out how to make the drives talk to one another, I am trying to get back into using Ubuntu, but alas, here I am with no clue, as usual.  What the heck is a GRUB menu and how do I get to it.

---

### Post by Michael.Godawski on 2009-04-10
> See, my friend installed it for me on a second hard drive. He is no longer around and we moved shortly after he did it. I had my passwords on a piece of paper and they were lost. My wife, not being sure of this whole " new OS" thing, wanted the old OS with all of her familiar things on it so I haven't been running Ubuntu for quite awhile. Now that I think I have figured out how to make the drives talk to one another, I am trying to get back into using Ubuntu, but alas, here I am with no clue, as usual. What the heck is a GRUB menu and how do I get to it.

Oh I see, no problem here we go:

We are using the recovery mode in root modus so be cautious and do not make any mistakes.  The root is able to edit everything and destroy the whole system.
 **Recovery Mode**

 
[LIST]
[*]Boot into Recovery Mode: during the start-up press ESC while you see the *GRUB Loading Stage* entry.
[*]From the Boot Menu select *Recovery Mode*
[*]Select *Drop to root shell prompt*
[/LIST]
 **Root Shell**

 
[LIST]
[*]Being in the root shell type
[LIST]
[*]ls /home      to see your username(s), then reset the password with
[*]passwd username       - change username to your username, for instance
[*]passwd john
[/LIST]
 
[*]When prompted for a new password type it in. It will not be displayed. You have to type blindly, as it were.
[*]Retype the password when asked to do so
[*]Leave the root shell with
[LIST]
[*]exit
[/LIST]
 
[/LIST]
 **Recovery Mode again**

 
[LIST]
[*]Select *resume normal boot*
[*]Log in with your username and your new password
[/LIST]

---

### Post by robnepper on 2009-04-11
Hi guys and gals.  When I type ls /home, it shows the word "rob" in blue letters.  I then type passwd and it asks me for me new password.  I type it and re-type it and it tells me that my unix passwd is now changed. I re-boot and try to log into to ubuntu and nothing happens. It's still not happy.

when I type ls /home then passwd username rob, it gives me alist of options that I am unable to do anything with.

What am I missing?

---

### Post by robnepper on 2009-04-12
Sorry to bump this thread, but I'm really stuck. Clearly, the answer would be to not get into this little predicament in the first place.

---

