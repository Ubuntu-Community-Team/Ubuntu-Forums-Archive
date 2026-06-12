---
title: "Screen Resolution Problem"
date: 2006-11-21
forum: Desktop Environments
---

### Post by Ringil on 2006-11-21
This morning when I started up Ubuntu (6.06) I noticed that everything was looking a bit too big. I figured it was the screen resolution messing up and went to fix it. The problem is, when I click on the drop down list there is only one option, and that's the resolution it has changed me to (640x480). This has never happened to me before on Ubuntu, and everything was running fine last night, and I have made no changes since the last time I started up my system.

Help would really be appreciated.

---

### Post by tzulberti on 2006-11-21
You should go to a consolte (ALT+Ctrl+F1) and type sudo dpkg-reconfigure xserver-xorg...

Then you should restart the X: 
sudo /etc/init.d/gdm restart...

Now it should allow you to change resolutions

---

### Post by Ringil on 2006-11-21
Thank you very much for the help. As you can probably tell, I'm still a beginner. I only installed Ubuntu last month.

Thanks again.

---

