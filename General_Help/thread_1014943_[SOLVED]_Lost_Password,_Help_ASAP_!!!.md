---
title: "[SOLVED] Lost Password, Help ASAP !!!"
date: 2008-12-18
forum: General Help
---

### Post by 4-PackDad on 2008-12-18
Help...!

Short & Simple...!

Can't Find or Remember Password.....!

Do remember Username...

How can I Log-In...

Wife out of state, Need to talk her thru this...

Thnx,
Bill

---

### Post by taurus on 2008-12-18
Boot into recovery mode from GRUB menu and at the prompt, change your password.  Assuming your login name is bill, run

```
passwd bill
```

Then reboot and see if you can log in with your username and the new password.

```
shutdown -r now
```

---

### Post by 4-PackDad on 2008-12-18
Hey;

I'm not good at Ubuntu my self much less trying to talk my wife thru this log distance.

She can get to the options screen in the bottom left.

Now what...

Thnx,
Bill

---

### Post by taurus on 2008-12-18
> **4-PackDad said:**
> Hey;

I'm not good at Ubuntu my self much less trying to talk my wife thru this log distance.

She can get to the options screen in the bottom left.

Now what...

Thnx,
Bill

Options screen in the bottom left?  Not sure what you mean here?  Are we talking about Ubuntu?

---

### Post by kanikilu on 2008-12-18
> **4-PackDad said:**
> Help...!

Short & Simple...!

Can't Find or Remember Password.....!

Do remember Username...

How can I Log-In...

Wife out of state, Need to talk her thru this...

Thnx,
Bill

Are you talking about the *system* login here, or an *application* (e.g. Skype, Pidgin, etc.)?

---

### Post by 4-PackDad on 2008-12-18
Yes, you are correct, that would be a problem.

I could figure this out if I was in front of the box.

That's why I switch'd to Ubuntu on my Home PC, Security Reasons.

Some times I still need Wind-Blows(log into my router). 
So Vista is on my laptop.

Thnx,
Bill

---

### Post by ajgreeny on 2008-12-18
You need to choose recovery mode at the grub menu, long before the login screen, which is where you probably see the Options, bottom left of the screen.  It is normally the second line of the grub menu, but if no grub menu appears hit the Esc button when you see "Starting grub" on the screen, and it should appear, then choose recovery mode.

This will give you a console root login and from there you can follow the info from taurus in post 2.  Just make sure you get the user name exactly correct, including upper and lower case letters, and similarly with the password, don't forget linux is case sensitive, unlike windows.

---

### Post by albinootje on 2008-12-18
> **4-PackDad said:**
> Hey;

I'm not good at Ubuntu my self much less trying to talk my wife thru this log distance.

She can get to the options screen in the bottom left.

Now what...

0) Forget about the options in this case right now.

1) Reboot the machine
2) choose "recovery mode" in the boot menu options (it is possible that you need to press the escape key to see the boot menu).
3) choose "drop to root shell" when that option is there
4) change the password

assuming that the user is called mary, then type :
passwd mary

type in the new password (it will not show any characters),
press enter,
and again the new password 

5) after that type : init 2
6) try to log in at the graphical login screen

---

### Post by 4-PackDad on 2008-12-18
Ok;

Now that, as Ricky Ricardo would say... Thanks for "splain'n" things for me.

Since I don't mess with this stuff every day, I tend to forget.

My wife will just have to wait till I get back.

Thnx again,
Will let you all know what happens this weekend.

Bill

---

### Post by aysiu on 2008-12-18
> **4-PackDad said:**
> Ok;

Now that, as Ricky Ricardo would say... Thanks for "splain'n" things for me.

Since I don't mess with this stuff every day, I tend to forget.

My wife will just have to wait till I get back.

Thnx again,
Will let you all know what happens this weekend.

Bill
What everyone is telling you is the correct method to reset a password. If you need some screenshots to guide you through, this page may help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

P.S. I've moved some of the off-topic discussion to [another thread](http://ubuntuforums.org/showthread.php?p=6393278#post6393278)

---

### Post by 4-PackDad on 2008-12-20
Thanks Everyone...!!!

Worked like a charm...!:)

A happy wife makes for a happy house.

Thanks again,
Bill

---

