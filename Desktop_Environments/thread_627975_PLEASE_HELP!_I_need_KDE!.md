---
title: "PLEASE HELP! I need KDE!"
date: 2007-11-30
forum: Desktop Environments
---

### Post by FRuMMaGe on 2007-11-30
I am having a serious problem with Gnome at the moment.

I get an error to the effect of "The gnome settings daemon could not be started" and I the  theme has been reset to the default gtk one.

I have searched and searched and no-one has a solution.

I have decided I want to get KDE to replace it. Will I lose anything by doing this?

Please reply quickly!

---

### Post by -grubby on 2007-11-30
you will not lose anything. You can install KDE by:

```
sudo apt-get install kde-core
```

---

### Post by FRuMMaGe on 2007-11-30
WIll it be the default desktop environment?

---

### Post by kopinux on 2007-11-30
last time i did it is, you can change it when you log out, you can even use e17 if you want.

---

### Post by bruce89 on 2007-11-30
Alt+F2:

```
gnome-settings-daemon
```

should work.

A minor issue like this shouldn't warrant a huge change like that.

---

### Post by FRuMMaGe on 2007-11-30
> **bruce89 said:**
> Alt+F2:

```
gnome-settings-daemon
```

should work.

A minor issue like this shouldn't warrant a huge change like that.

Nope, that does nothing.

I think the problem is that apparently my gnome-settings-daemon is "too large"

Here is the error:
[http://ubuntuforums.org/showthread.php?t=627990]("http://ubuntuforums.org/showthread.php?t=627990")

EDIT: Also, I installed the kde-core, but I don't know how to enable kde. I'm still in gnome after the restart

---

### Post by -grubby on 2007-11-30
go to session>kde and log in

---

### Post by FRuMMaGe on 2007-11-30
> **nathangrubb said:**
> go to session>kde and log in

Sorry, where is "session"?

---

### Post by Linuxratty on 2007-11-30
> **kopinux said:**
> last time i did it is, you can change it when you log out, you can even use e17 if you want.

WHAT!!???
 I'm going to be installing Kbuntu when the black Linux box is repaired (Loooong story.) ..How do I get e17?
sudo apt-get installe17-core?
Is that IT!?

---

### Post by p_quarles on 2007-11-30
First off, I agree with Bruce89: If you're otherwise happy with Gnome, I'm sure you'll be able to get this resolved. 

Anyway, to enable KDE, you have to click on the "options" or "sessions" menu in your login manager, and choose KDE. It will then ask if you want it to be default, which is up to you.

---

### Post by FRuMMaGe on 2007-11-30
> **p_quarles said:**
> First off, I agree with Bruce89: If you're otherwise happy with Gnome, I'm sure you'll be able to get this resolved. 

Anyway, to enable KDE, you have to click on the "options" or "sessions" menu in your login manager, and choose KDE. It will then ask if you want it to be default, which is up to you.

I have found the problem with gnome

I browsed to the control folder where gnome-settings-daemon is.

Apparently, my gnome-settings-daemon is 512 gigabytes.

This is really wierd because I'm on a 160GB laptop. Is there a way I can reinstall it?

---

### Post by bruce89 on 2007-11-30
> **FRuMMaGe said:**
> Apparently, my gnome-settings-daemon is 512 gigabytes.

Wow.

```
sudo aptitude reinstall gnome-control-center
```

---

### Post by FRuMMaGe on 2007-11-30
> **bruce89 said:**
> Wow.

```
sudo aptitude reinstall gnome-control-center
```

Thanks so much! That fixed it!

---

### Post by bruce89 on 2007-11-30
> **FRuMMaGe said:**
> Thanks so much! That fixed it!

Glad to help.

---

### Post by init1 on 2007-11-30
> **Linuxratty said:**
> WHAT!!???
 I'm going to be installing Kbuntu when the black Linux box is repaired (Loooong story.) ..How do I get e17?
sudo apt-get installe17-core?
Is that IT!?
```

apt-get install enlightenment 

```

---

### Post by SunnyRabbiera on 2007-11-30
> **init1 said:**
> ```

apt-get install enlightenment 

```

isnt it e16 though on the repos?

---

### Post by -grubby on 2007-11-30
> **SunnyRabbiera said:**
> isnt it e16 though on the repos?

yes that's e16, PM RAV TUX if you want to know where the E17 deb is, or RUI PAUS

---

### Post by FRuMMaGe on 2007-11-30
> **bruce89 said:**
> Glad to help.

One more thing, after the problem was solved there was one thing still wrong.

Basically, the preview pictures of pictures and videos no longer appear.

This is not a major issue, but still a big inconvenience when looking for certain photos, as camera have a nack of naming photos by number.

Any ideas?

---

