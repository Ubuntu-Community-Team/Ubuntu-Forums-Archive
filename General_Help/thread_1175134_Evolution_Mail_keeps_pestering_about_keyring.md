---
title: "Evolution Mail keeps pestering about keyring"
date: 2009-05-31
forum: General Help
---

### Post by DeusExM1 on 2009-05-31
Hey Everyone !

Here is the problem:Every time i boot up my computer and try to run evolution it says something along the lines of "Evolution Cannot open default keyring". Basically i have to enter this password or it wont work. I have looked on the workarounds other people posted but none seem to pertain to me (for example several people suggested to using preferences -> Encryption and Keyrings -> passwords tab. Problem is i have no passwords tab...) . I have the 64 bit Ubuntu 9.04 version. 

So any ideas how to fix this?
[I]




Rant[/I]

I am really puzzled why the Evolution devs decided to add this via an "update" to this email client. I have read that users are only prompted for the password if their computers are set to autologin. Is this true? If so i think these guys are completely insane. If i dont use a password to protect my computer, why would i want to use one to protect emails? Majority of users arent little kids and can look out for themselves, adding "Features" like this are just a hassle more than anything else. If they wanted to add it so bad why not just include an *option* for evolution to ask for passwords in this manner? Linux users are already prompted for passwords quite often, why would anyone want to increase this even more? There is a line that needs to be drawn between security and paranoia, and this is probably a good time to do that. 

It would be alright for me, but i recently convinced my father to abandon Vista and try Ubuntu. I set up everything, and i promised things would be easier... But Evolution insists on asking not only for this password, but also the passwords to the email account (although its supposed to be remembering it). What is the point of the email client then? why not just have a shortcut to Gmail on your desktop and use that? Sorry for the rant, Evolution is my favorite email client, but seriously... Was this really THAT necessary?

---

### Post by expelledboy on 2009-06-01
I am relucatant to give [this]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") link as it does leave your system vunerable.. but what the heck.. risk for reward.

---

### Post by fballem on 2009-06-01
Post number 7 in this thread: [http://ubuntuforums.org/showthread.php?t=1109736](http://ubuntuforums.org/showthread.php?t=1109736) gives the correct instructions for changing the password on the keyring in ubuntu 9.04.

Apparently, when you change your login password, the password to access the keyring is not changed. It is still the old password. I have learned that when I change my ubuntu password, I also have to change my keyring password to match my new login password.

Hope this helps,

---

### Post by VMC on 2009-06-01
> **expelledboy said:**
> I am relucatant to give [this]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") link as it does leave your system vunerable.. but what the heck.. risk for reward.

Thanks for that link. And for the risks involved, the author has made some valid points.

---

### Post by DeusExM1 on 2009-06-01
Thank You very much for the tips. I got it to work on both my machine and my father's. You guys are life savers !

---

### Post by expelledboy on 2009-06-02
np.. :)

---

