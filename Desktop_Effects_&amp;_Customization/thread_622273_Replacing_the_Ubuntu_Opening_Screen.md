---
title: "Replacing the Ubuntu Opening Screen"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by gjtoth on 2007-11-24
No... I'm not talking about the usplash.  I'm talking about the screen that you first get when Ubuntu first starts that shows a progress bar.

I'd like to change it.

I've searched these forums until my eyes are ready to bug out of my head and can't find what I'm looking for. :shock:

Can someone point me in the right direction?

---

### Post by Forlong on 2007-11-25
> **gjtoth said:**
> No... I'm not talking about the usplash.  I'm talking about the screen that you first get when Ubuntu first starts that shows a progress bar.
That *is* usplash.

---

### Post by gjtoth on 2007-11-25
> **Forlong said:**
> That *is* usplash.

Then, what is the screen called after you log on and it says Ubuntu with a 3-4 little icons for a short time?  I was under the assumption that was the usplash.

---

### Post by dips_xe on 2007-11-25
i don't know what that's called, but it's not usplash. just to make sure i typed usplash into my terminal and the progress bar you're talking up came up :)

---

### Post by Forlong on 2007-11-25
That's the (GNOME) splash screen.

You can refer to both as splash screens. I'd prefer naming the one with the status bar the *boot splash*.

In any case, usplash is for the boot splash.

---

### Post by dips_xe on 2007-11-25
this page has very good directions on how to change your usplash, just scroll down a little:

[http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468]("http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")

---

### Post by gjtoth on 2007-11-25
> **dips_xe said:**
> i don't know what that's called, but it's not usplash. just to make sure i typed usplash into my terminal and the progress bar you're talking up came up :)

Ok.. then, let me rephrase my question.

How do I change the screen that appears right after the grub prompt?

---

### Post by Schalken on 2007-11-25
The screen the appears right after the GRUB menu is the usplash. The login screen that appears after that is the GDM (GNOME Display Manager, technically not a splash screen), and the splash screen that comes after you enter your username and password I just call the GNOME splash screen.

Which would you like to change?

---

### Post by Forlong on 2007-11-25
> **gjtoth said:**
> How do I change the screen that appears right after the grub prompt?
Search for **usplash** in gnome-look.org and use startup-manager to change 'em.
```
sudo apt-get install startupmanager
```

---

### Post by gjtoth on 2007-11-25
Pardon my ignorance.

Thanks for all your help.  I believe I've got a handle on it now.  Great links and info.

---

