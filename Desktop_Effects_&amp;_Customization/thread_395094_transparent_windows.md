---
title: "transparent windows"
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by Jeremy88 on 2007-03-27
I have Kubuntu Edgy installed on my computer and I am wondering how to make my windows transparent without using XGL With Compiz/Beryl.

Is there a way to do this, by just using a theme or installing a package. I just want my outer windows transperent or the windows to be transparent.

---

### Post by 23meg on 2007-03-27
You can use xcompmgr, but it's quite dated and isn't very stable.

---

### Post by russellc on 2007-03-27
If you're using an ATI video card which isn't supported by the open source radeon drivers, then you'll have to use XGL either way. Xfwm is a nice window manager that has a composite option and is a little more straight-forward to use than Beryl (less features). It performs window transparency as well as shadows. You can also choose to have just the window decorations to be transparent.

I wouldn't recommend xcompmgr as it is quite buggy and unstable.

---

### Post by DrQuincy on 2007-03-28
I'm in a similar situation - will xfwn work with a Radeon X1300 Pro?

---

### Post by russellc on 2007-03-28
> **DrQuincy said:**
> I'm in a similar situation - will xfwn work with a Radeon X1300 Pro?

Well, a composite manager requires that you are capable of having a video card accelerated desktop. So, if you are using XGL (which you probably are if you are using fglrx with the X1300) or AIGLX, then you should be able to use Xfwm. If you aren't using XGL or AIGLX, you could still use it, but it'll be slow since its rendering using software and not hardware.

---

### Post by Jeremy88 on 2007-03-29
Is there just a theme to have the border of your windows transparent? I have an ATI card but I have the Closed Source(ATI Drivers) installed. 

I was hoping not to install a window manager since I want to keep my computer running at a top notch speed with KDE.

---

### Post by ethaniscool on 2007-05-22
This is almost exactly the same situation I am in. I want some transparency for my desktop but I do not want to install Berly/XGL/Compiz. A solution would be greatly appreciated.

---

