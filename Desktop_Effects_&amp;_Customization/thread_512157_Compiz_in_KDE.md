---
title: "Compiz in KDE"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by halon on 2007-07-28
Successfully installed Compiz and it works as long as I open an XGL session.  While in KDE, 
alt-F2 then 
```

compiz --replace

```
This does absolutely nothing.  Am I mistaken or shouldn't Compiz run under KDE?  Compiz settings manager is there, it simply wont run.  Any suggestions are great.

---

### Post by kodoku on 2007-07-29
try running that command in the terminal, you should see the errors that are causing problems

---

### Post by halon on 2007-07-29
Thanks, i get the following message:

halon@isolate:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

---

### Post by cporter23 on 2007-07-29
> **halon said:**
> Successfully installed Compiz and it works as long as I open an XGL session.  While in KDE, 
alt-F2 then 
```

compiz --replace

```
This does absolutely nothing.  Am I mistaken or shouldn't Compiz run under KDE?  Compiz settings manager is there, it simply wont run.  Any suggestions are great.

KDE itself is not a composition manager.  You need either AIGLX or Xgl running before you can use Compiz.  

If I understand your first sentence properly, it sounds like you already have a Xgl session running Gnome and Compiz.  If you want to run Compiz with a KDE desktop, I would think the most straightfoward approach would be to create a second Xgl login session that starts KDE instead of Gnome.  I used this guide,  [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl") , when I was setting up my Xgl session for KDE.  Since you appear to already have Xgl installed, you should be able to skip down to the section on setting up sessions.

HTH

---

### Post by halon on 2007-07-29
Yes, Thank you.  Works fine now.

---

