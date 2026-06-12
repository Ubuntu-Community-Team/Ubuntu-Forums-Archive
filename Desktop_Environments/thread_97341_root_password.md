---
title: "root password"
date: 2005-11-30
forum: Desktop Environments
---

### Post by freronn on 2005-11-30
So, I installed Ubuntu. It was a very easy install process, maybe a little too easy, because I never got a chance to decide a root password, and now what? Have I missed someting very very obvious? 

Please help!

---

### Post by Iandefor on 2005-11-30
If you need to run a program with root priveleges, it'll ask you for your password. Just enter your user password. Ubuntu does not use the root account by default. Check the [wiki]("https://wiki.ubuntu.com/RootSudo") as to why.

---

### Post by freronn on 2005-11-30
It doesn't use the root account??? How odd, indeed. Ok, I'll check that link out, thanks!

---

### Post by Iandefor on 2005-11-30
To be totally accurate, it *is* available, it's just Ubuntu does some trickery with sudo to make it so that you don't need it to perform administrative tasks. 
If you *really really *want it*, *go to "Users and groups". This is easily accessible through the system-->administration menu. Check "Show all users and groups" and scroll down to root. Click on "Properties" and change the password to whatever you want. As is, you still can't log in using GDM, however. To enable logging in with GDM, open up the GDM configuration dialog (I think it's "login screen" under administration menu), go to the "Security" tab and check "Allow root to login with GDM," and while you're at it, make absolutely certain that "Allow root to login remotely with XDMCP" or some such thing is unchecked. There are few legitimate reasons to login remotely as root.

---

