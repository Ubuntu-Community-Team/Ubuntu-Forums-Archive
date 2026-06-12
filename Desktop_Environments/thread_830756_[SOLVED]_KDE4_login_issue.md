---
title: "[SOLVED] KDE4 login issue"
date: 2008-06-16
forum: Desktop Environments
---

### Post by aaronp on 2008-06-16
Hi all,

I recently installed KDE4 on my existing Ubuntu installation. I started with Gnome, moved on to KDE3.5 which is now my 'preferred' desktop environment and then decided to give KDE4 a try. 

After installing it there were no issues. For a week or so I have been able to log into KDE4 without issue by simply selecting the correct session at login.

Yesterday I was playing around with desktop and icon configuration in KDE4 (as you do with a new toy!!) and after making a particular change (unfortunately can't remember exactly what I was doing) the screen went black and I was thrown out back to the login screen.

Since that every time I try to log in to a KDE4 session it seems to run ok as it goes through the initialisation/splash screen but then the screen goes black and the login screen appears again after a second or two. The behaviour is exactly the same as when I choose to 'restart the X server' from the login window. i.e. quick change to black screen and then back to the login screen.

I am still able to log into KDE 3.5 and Gnome with no issue. I don't really have enough knowledge to know where to start with this problem and looking around at other forums on this matter I note a few people have experienced the same thing but there doesn't seem to be a successful or unique answer to the problem.

Anyone have any ideas or guidance?

thanks in advance
Aaron

---

### Post by benerivo on 2008-06-16
If you're willing to lose all your kde4 settings, then you can delete the

/home/YOURNAME/.kde4

folder and the try to log in. It will load kde4 with the default settings, and you'll lose whatever setting that you may have broken it with in the first place.

Actually, it may be better to rename the ~/.kde4 folder to ~/.kde4BACKUP. You will get the same effect as above, but will also keep the settings in case you want to try another fix.

---

### Post by aaronp on 2008-06-17
thanks benerivo, that fixed the problem.
Assuming this was 6 months down the track and I was not willing to lose all of my settings what other options would there be? (i.e. are there any logs that might point me to what caused the issue? also might be a bug that we can raise officially...)

thanks
Aaron

---

