---
title: "KDE Desktop and Chromium"
date: 2012-02-18
forum: Desktop Environments
---

### Post by jorritTyb on 2012-02-18
Hi all,

Today I (accidently in fact) switch to KDE Desktop because I had another problem with xfwm4 not starting again and was getting bored of that. So I tried KDE Desktop and it looks pretty good. However I just discovered one rather big problem. With Chromium browser I'm not getting any save dialogs or whatever. If I do 'Save As' (to save a web page) or 'Save Image As' no dialog appears and I can't save anything. The Print dialog works but not the save dialogs. Other applications (like gvim) have no issues with their save dialogs.

Any ideas about what could be wrong?

Greetings and thanks,

---

### Post by jorritTyb on 2012-02-19
Nobody? This is a really annoying problem.

BTW. Seems any dialog with a file requester is the problem. Sites where you have to upload things also don't work.

---

### Post by oldos2er on 2012-02-19
Which version of Kubuntu or Xubuntu are you using? Have you tried rebooting or logging out and logging back in?

---

### Post by jorritTyb on 2012-02-19
> **oldos2er said:**
> Which version of Kubuntu or Xubuntu are you using? Have you tried rebooting or logging out and logging back in?

How can I see that?

I'm using Ubuntu 11.10 btw. Not Kubuntu.

Rebooting doesn't help.

Greetings,

---

### Post by oldos2er on 2012-02-19
11.10 is 11.10 no matter which desktop environment you're using. ```
lsb_release -d
```

I don't know what else to suggestion regarding Chromium, sorry.

---

### Post by jorritTyb on 2012-02-20
> **oldos2er said:**
> 11.10 is 11.10 no matter which desktop environment you're using. ```
lsb_release -d
```

I don't know what else to suggestion regarding Chromium, sorry.

lsb_release says 11.10. Is there nobody else with this problem?

---

### Post by azmyth on 2012-02-20
Works for me. Make sure you have this installed.

kde-baseapps-bin

and/or, test

which kdialog

---

### Post by jorritTyb on 2012-02-20
> **azmyth said:**
> Works for me. Make sure you have this installed.

kde-baseapps-bin

and/or, test

which kdialog

Yes! That fixed it! Why wasn't the installed by default?

Thanks a lot!

---

### Post by azmyth on 2012-02-20
Can't argue with you on why it wasn't installed by default. Seems like kdialog would be important but then again IDK as it just MHO.

---

