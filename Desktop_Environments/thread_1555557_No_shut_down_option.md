---
title: "No shut down option?"
date: 2010-08-18
forum: Desktop Environments
---

### Post by Roasted on 2010-08-18
Within the kickoff launcher where logout/suspend/etc is, there's no shut down or reboot option. I'm also not finding it within the panel itself. I tried looking through the available widgets to  add one, but I'm not finding anything.

So uh - how do I turn my pc off? :P

---

### Post by dabl on 2010-08-18
> **Roasted said:**
> 

So uh - how do I turn my pc off? :P

KMenu > System > Konsole and enter ```
sudo shutdown now -h
```

---

### Post by Roasted on 2010-08-18
> **dabl said:**
> KMenu > System > Konsole and enter ```
sudo shutdown now -h
```

Hate to say it like this, but that is certainly not a valid solution.

There's the button in the GUI? I ran Kubuntu before - where did they go?

---

### Post by depeha on 2010-08-19
You have installed GDM, right? Using KDM will solve the problem ;)
```
sudo dpkg-reconfigure kdm
```
and choose KDM.

---

### Post by Roasted on 2010-08-19
> **depeha said:**
> You have installed GDM, right? Using KDM will solve the problem ;)
```
sudo dpkg-reconfigure kdm
```
and choose KDM.

I don't understand. Isn't using KDE at the login screen using KDM? 

If I do that, will anything happen to GDM/Gnome?

---

### Post by Roasted on 2010-08-19
up... hoping for a quick answer. :(

---

### Post by depeha on 2010-08-20
You are probably using GDM as default. Just run
```
sudo dpkg-reconfigure kdm
```
and choose KDM. And don't worry... it's not going to do anything with GDM or Gnome. You'll be still able to login into gnome ;)

---

### Post by ankspo71 on 2010-08-20
> **Roasted said:**
> Within the kickoff launcher where logout/suspend/etc is, there's no shut down or reboot option. I'm also not finding it within the panel itself. I tried looking through the available widgets to  add one, but I'm not finding anything.

So uh - how do I turn my pc off? :P

Hi, 
Try going to Settings > System Settings > Click on the Advanced tab > Session Manger. Make sure that "Offer Shutdown Options" is enabled. If I uncheck this, it will remove the shutdown buttons from my kickoff menu and the classic looking menu. 

If that doesn't help, you can add the "Lock/Logout" widget (which offers shutdown options) to your panel until you can get to the bottom of it.
Hope this helps.

---

### Post by Termaim on 2010-09-08
Woot! Thank you so much, I have been searching the forums all night and finally found this post.  I recently installed the kubuntu-desktop package to try out kde and *love* it... but I was having the same issue.  Can't wait to get home from work now and reconfigure it so kdm is the default (I left gdm as default when it was installed as I had no idea if I'd like it or not).  Again, thank you for the help :D

---

### Post by wkhasintha on 2010-09-08
> **depeha said:**
> You are probably using GDM as default. Just run
```
sudo dpkg-reconfigure kdm
```
and choose KDM. And don't worry... it's not going to do anything with GDM or Gnome. You'll be still able to login into gnome ;)

Thanx for this. :D

---

