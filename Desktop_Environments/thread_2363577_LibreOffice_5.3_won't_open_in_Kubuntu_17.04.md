---
title: "LibreOffice 5.3 won't open in Kubuntu 17.04"
date: 2017-06-11
forum: Desktop Environments
---

### Post by llanitedave on 2017-06-11
I'm running both Unity and Kubuntu desktops on my laptop, with the idea of slowly weaning myself away from Unity once GNOME becomes the default.  I'm learning the KDE Plasma 5.9 desktop, and for the most part I'm getting it to work the way I want to.  However, today I discovered a show-stopper of a problem:

Libre Office will not open on the Plasma desktop.  It doesn't matter whether I try to open in from the launcher or by clicking a file.  It fails the same way in both Writer and Calc.  I get the bouncing icon for a few seconds, and then it silently disappears.  There's no message, no crash notification.  It simply doesn't work.

I have no issues with Unity opening the files, everything there is smooth and fast.  Is there something in the KDE System Preferences I might have set wrong?  I have been running both QT and GTK apps in Kubuntu with no issues, this is the first big problem I've encountered (a couple of small ones).

Anyone else experienced or have heard of this problem?  I'd really hate to abandon KDE (again) after all the effort I've put into setting it up.

---

### Post by vasa1 on 2017-06-12
Have you tried from the command-line?

---

### Post by llanitedave on 2017-06-12
Good idea.  I'll try that.

---

### Post by llanitedave on 2017-06-12
No, same issue.  I get the LibreOffice logo appearing momentarily, then it simply disappears with no message.

---

### Post by vasa1 on 2017-06-12
Grabbing at straws here, but do you have something like "libreoffice-kde" installed?

---

### Post by howefield on 2017-06-12
> **llanitedave said:**
> No, same issue.  I get the LibreOffice logo appearing momentarily, then it simply disappears with no message.

No message(s) in the terminal at all ?

---

### Post by llanitedave on 2017-06-12
> **vasa1 said:**
> Grabbing at straws here, but do you have something like "libreoffice-kde" installed?

It's the standard Libre Office that came installed with the Ubuntu 17.04 distribution that I installed a couple of months ago.  The Kubuntu desktop is something I added in later, and it shouldn't have changed any of the Libre Office software.

> **howefield said:**
> No message(s) in the terminal at all ?
Not at least in the terminal that I ran the libreoffice command from.

All my other Kubuntu software works fine so far (auto-hide on a side panel doesn't work reliably, but that had been my only issue up until now.)  

This failure effects both Writer and Calc, I haven't tried it on Draw yet.

---

### Post by speartip on 2017-06-13
It probably has something to do with the fact you added the Kubuntu Desktop on top of Ubuntu. This sometimes causes conflicting config files.
 In your Home folder there is a hidden .config folder. In there you will see a libreoffice folder. Delete the libreoffice folder so you have a fresh configuration, then see if it opens.

---

### Post by vanadium on 2017-06-13
>  Quote Originally Posted by vasa1 View Post
Grabbing at straws here, but do you have something like "libreoffice-kde" installed?

> **llanitedave said:**
> It's the standard Libre Office that came installed with the Ubuntu 17.04 distribution that I installed a couple of months ago.  The Kubuntu desktop is something I added in later, and it shouldn't have changed any of the Libre Office software.


Not at least in the terminal that I ran the libreoffice command from.

All my other Kubuntu software works fine so far (auto-hide on a side panel doesn't work reliably, but that had been my only issue up until now.)  

This failure effects both Writer and Calc, I haven't tried it on Draw yet.

Still, check whether the package libreoffice-kde is installed on your system. If not, try installing it.

You may also want to test starting libreoffice with the following commands
```

SAL_USE_VCLPLUGIN=gen && libreoffice

```
If it runs, it will not look very nice - no visual integration with your desktop
```

[code]
SAL_USE_VCLPLUGIN=kde4 && libreoffice

```
This would explicitly tell lo to use KDE4 theme integration. LO should normally attempt to do this automatically, so this command may fail.

---

### Post by llanitedave on 2017-06-13
Thanks, all.  I'll try these approaches this evening and report back.

---

### Post by llanitedave on 2017-06-13
> **speartip said:**
> It probably has something to do with the fact you added the Kubuntu Desktop on top of Ubuntu. This sometimes causes conflicting config files.
 In your Home folder there is a hidden .config folder. In there you will see a libreoffice folder. Delete the libreoffice folder so you have a fresh configuration, then see if it opens.

That was the solution!  I deleted the folder, opened Libre Office Writer, and it has opened and lets me work with my files now.

Thanks!

---

### Post by mr2131 on 2017-06-23
I'm having a very similar problem and I am running Ubuntu 17.04. The program simply will not open. The first error report said something about the compressed file ending too soon, or something like that. I can't afford to simply not have access to my Writer program.

---

### Post by speartip on 2017-06-24
> **mr2131 said:**
> I'm having a very similar problem and I am running Ubuntu 17.04. The program simply will not open. The first error report said something about the compressed file ending too soon, or something like that. I can't afford to simply not have access to my Writer program.

And so have you tried the fix in post 8?

---

### Post by vasa1 on 2017-06-24
This thread is about Kubuntu. Post #12 seems to be about Ubuntu. @mr2131, it maybe better if you start your own thread.

---

