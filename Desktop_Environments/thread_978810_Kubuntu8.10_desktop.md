---
title: "Kubuntu8.10 desktop"
date: 2008-11-11
forum: Desktop Environments
---

### Post by okkadiroglu on 2008-11-11
Hi,

I have upgraded my AMD64/Kubuntu8.04 machine to 8.10. Somehow the task bar has changed without my involvement. It becomes black and if I move the cursor on it, after few tries, I can see the panels. The order has been changed and kickoff button disappeared from the very left side of the bar. I added it as a widget but I can not put it in its proper place. I can not click any operating program on the right hand side of the task bar. I read the help pages and tried to do what is said there but I was not successful. Either the help pages do not mention a remedy for my problem or there is something else I am missing. Kde3.5 was very easy in controlling the desktop. I think kde4 needs some ironing. I would be pleased if you tell me what to read.

Best regards

---

### Post by kernelhaxor on 2008-11-11
Sorry I don't hav a solution .. but I can only recommend a fresh install ..
Upgrades sometimes cause weird issues .. it might not be worth your time to debug ..
Also, KDE 4 is not yet as stable/polished as KDE 3.5 but I think it is still usable .. I have been using it since a while and have been more than satisfied with it

---

### Post by okkadiroglu on 2008-11-11
Thank you very much for your prompt help. I had upgraded 8.04 t0 8.10 through Internet. How can I reinstall it?

---

### Post by aged hippy on 2008-11-11
You would need to re-install it by downloading and burning the latest .iso from here: [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

That will install Intrepid on your machine.

In the installer, if you select to format the **/** partition, and to mount your /home partition - **but not to format it** - you will find that your settings are preserved.

---

### Post by gsmlinux on 2008-11-11
Before re-installing try the following:

Remove or rename the following 2 files

.kde/share/config/plasma-appletsrc
.kde/share/config/plasmarc

Then log out and back into your kde4 session.

This sorted out my task panel problems when I upgraded from 8.04 to 8.10.

---

### Post by okkadiroglu on 2008-11-11
Thank you very much, I finally solved it. I did changed plasmarc and plasma-apllet to new names buy no matter what I did it did not do the trick. Then I realized for some reason I have .kde and .kde4 directories. Most probably under 8.04 I did try kde4. I did the changes in .kde4 directory and nothing happened. I created a new user and there I realized that there is no .kde4 directory. So I changed the above mentioned names in .kde and everything worked well. Thanks a million.:)

---

