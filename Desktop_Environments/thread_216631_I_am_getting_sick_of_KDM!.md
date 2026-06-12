---
title: "I am getting sick of KDM!"
date: 2006-07-15
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-07-15
Why is it that every second time I've had to either restart or shut down the computer, for a couple of months now, I run the risk of KDM freezing the shutdown process and causing me to press the button on the front of my computer?!?

I know I can switch to GDM because KDM is obviously doing a poor job of working at the moment. . .but COME ON guys. Two solid months without a fix for this?

I don't want to have to keep on restarting the server before I log out through tty1, and I've run fsck on my hard drive enough already thank you.  

What can I do to stop this?

(PS: Reinstalling KDM hasn't worked.)

---

### Post by aysiu on 2006-07-16
I've had no such problems with KDM.

If you think it's a serious problem, you might want to file a bug report about it.

In the meantime, use GDM--just to have a functioning system.

---

### Post by [S|G] on 2006-07-16
I also had no problems with KDM to date. It might be related to some other program that you're running that is not shutting down gracefully (not accepting the TERM signal linux sends to it) and is holding the system.

Try to open up a konsole window and then type ```
sudo shutdown -h now
``` If it still locks up, then it's not a KDM related problem. You could also try to quit some applications before shuttind down and see if there is any improvement.

---

### Post by siafulinux on 2007-06-24
I have had the same problem since upgrading to Feisty. Actually I think it began after an update after upgrading to Feisty. 

Logging out, restarting or shutting it down will sometimes result in a freeze with a blank screen and a mouse cursor. Then I have to shut down by pressing "the button on the front" and restart. But it doesn't always happen.

Wonder what's up.

Siafu

---

### Post by floke on 2007-06-24
What's wrong with using gdm anyway? 
The login screens are far superior IMO.

---

### Post by siafulinux on 2007-06-24
I'm going to try and get GDM going tonight. Nothing wrong with using it. However, I wanted to point out that there are other people experiencing the same problem. At least two now :-)

---

### Post by lexxonnet on 2007-06-25
Thats odd... upgrading to feisty actually fixed the shutdown problems for me... shuts down like a charm everytime now.

---

### Post by floke on 2007-06-25
I occasionally (eg 1/20) get shutdown issues with GDM at the rc.local scripts stage; 'solution' is to drop to tty1 and 'sudo /etc/init.d/gdm restart'. I can then shutdown happily from the login screen.

---

### Post by bailout on 2007-06-25
This has been a problem for some people for a while now. I have had it in fiesty and edgy. I used to think it was a kubuntu problem but the other reports I have seen for fiesty have gnome people with the same problem so it is a fault with ubuntu itself.

There have been lots of 'solutions' posted which work for some but not others. My solution which is a bit of a pain but has always worked for me is to logout and then shutdown from the kdm screen rather than trying to shutdown directly.

---

