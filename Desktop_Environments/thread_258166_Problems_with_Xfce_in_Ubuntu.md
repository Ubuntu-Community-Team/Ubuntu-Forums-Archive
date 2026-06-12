---
title: "Problems with Xfce in Ubuntu"
date: 2006-09-15
forum: Desktop Environments
---

### Post by iflanery on 2006-09-15
For some reason, Xfce has decided NOT to remember (or acknowledge) my preferences for desktop wallpaper, default file manager, etc. Everytime I try to change any of these preferences, the WM doesn't do anything. I've tried saving sessions upon logging out (which somehow fails to remember my preferences even though it's set to automatically save them), running xfdesktop (as suggested to me on another forum) doesn nothing while in Xfce. Right now I'm entertaining the idea of just reinstalling Xfce from the source code. 

I've only been using Xfce for the past couple of nights, so any suggestions about what I can do to remedy these problems are appreciated.

---

### Post by brucevangeorge on 2006-09-15
How did you install xfce?

Did you use Xubuntu? Server install with xubuntu-desktop? Or server install with the modules: xfce4, thunar... and etc. individually?

---

### Post by iflanery on 2006-09-15
I believe it was a server install with xubuntu-desktop.

---

### Post by brucevangeorge on 2006-09-15
You do realize... you might have just installed from the Xubuntu cd instead. I found it to be exactly the same, same software, same settings, same everything.

Its just a waste of time to download all of that.

Here is what you do:

Try reinstalling. Do if from a CD this time. I am using XFCE as i am typing this. I have not had a problem since I installed it last month. I did it a different way (I installed it piece by piece with only  what I liked). But the CD version... never had a hiccup.

---

### Post by iflanery on 2006-09-15
I guess what I did was install Xfce using apt-get instead of aptitude. Therefore I uninstalled everything on Xfce completely and reinstalled it using aptitude. Seems to be working just fine now.

---

