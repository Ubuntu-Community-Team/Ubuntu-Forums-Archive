---
title: "Who is triggering the key ring password prompt?"
date: 2011-03-07
forum: Desktop Environments
---

### Post by deepaknet on 2011-03-07
For the past couple of days, after I attempted, KDE shell on my Ubuntu I keep getting a dialog like 'Enter password to unlock keyring'. Not sure if I set something but Ubuntu logon password is not accepted.

Is there a way to find out what causes this dialog to throw open and/or how to reset this KeyRing password?

---

### Post by deepaknet on 2011-03-07
KDE Key-ring started to crop only after KDE attempted.

---

### Post by frank4360 on 2011-06-10
I have a similar annoyance using xubuntu 11.04: I keep getting asked to unlock the keyring. The message occurs twice after bootup, and recently I decided to ignore it to see what happens. Answer - nothing happens! I can get into all programs, wifi, etc - so why is the system asking for a keyring password?

The real annoyance is that it continues to ask for the keyring password (twice) at regular intervals all the time I am logged on.

---

### Post by alienmindtrick on 2011-06-21
I'm getting the password prompt 3 times, every time I log in. And unlike the posts above, if I attempt to ignore them, I can't do some things (like...anything) until I log in...THREE TIMES! I didn't have this problem before upgrading to 11.04. Also, since this may be related, is there a way to get rid of this RIDICULOUS launcher panel and go back to the nice, elegant desktop that 10.10 had without rolling back to 10.10? And why is this supposed to be better? Half the time it doesn't come out when I move my cursor to the edge of the screen. It's not a tool so much as an annoyance, in my opinion.

Not to rant, but it seems to me that the elegance of Ubuntu is ebbing and that a kitschy clutter is starting to obtain. Why?

---

### Post by frank4360 on 2011-06-21
> **alienmindtrick said:**
> Also, since this may be related, is there a way to get rid of this RIDICULOUS launcher panel and go back to the nice, elegant desktop that 10.10 had without rolling back to 10.10? 

I agree the Unity screen is awful!

After much searching I found out how to ditch it and revert to the previous screen - it is supposed to be an option offered while upgrading to 11.04.

Go to Main Menu>>System>>Administration>>Login Screen  You will need to enter your Password to Unlock the screen, then select "Ubuntu Classic" as the Default Session.


By the way I don't get the multiple password prompts on Ubuntu, just on Xubuntu?

Good luck.

---

### Post by alienmindtrick on 2011-06-22
> **frank4360 said:**
> I agree the Unity screen is awful!

After much searching I found out how to ditch it and revert to the previous screen - it is supposed to be an option offered while upgrading to 11.04.

Go to Main Menu>>System>>Administration>>Login Screen  You will need to enter your Password to Unlock the screen, then select "Ubuntu Classic" as the Default Session.


By the way I don't get the multiple password prompts on Ubuntu, just on Xubuntu?

Good luck.

Yeah, I found that too, and ditched the ridiculous Unity desktop.  After spending a week in #ubuntu on Freenode, IRC, I've learned that it is NOT for beginners. It's for advanced users to condescend to those seeking help. Also, for the various problems I've encountered in the almost-1-year I've used Ubuntu, I've never gotten a valid answer there.
So, I'm hoping someone here has a solution, still. Anyone?

---

### Post by wildmanne39 on 2011-06-23
Hi, you can disable key ring in natty if it is malfunctioning like you are seeing. I would not do it if it is working properly.
[http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-)

---

### Post by alienmindtrick on 2011-06-23
> **wildmanne39 said:**
> Hi, you can disable key ring in natty if it is malfunctioning like you are seeing. I would not do it if it is working properly.
[http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-)

Thank you! That is the most cogent answer I've gotten to this issue, and I appreciate your help.

---

### Post by Ginzell on 2011-06-23
Hi,
 I believe there is a place in Passwords & Encryption Keys that you can fix this problem.  I can't recall where I came across this same question but it had to do with there being double entries asking for your key.  There should only be one request for your Keyring, so all that's needed is for you to delete one of the doubles.  Sorry I can't remember the exact details but it seems like an easy fix.

---

### Post by wildmanne39 on 2011-06-23
> **alienmindtrick said:**
> Thank you! That is the most cogent answer I've gotten to this issue, and I appreciate your help.Hi, your welcome.

---

