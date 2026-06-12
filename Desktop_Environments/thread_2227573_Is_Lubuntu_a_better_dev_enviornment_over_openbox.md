---
title: "Is Lubuntu a better dev enviornment over openbox?"
date: 2014-06-02
forum: Desktop Environments
---

### Post by PeterTaps on 2014-06-02
Folks,

Here is a little background so that my question makes more sense.

Usually, within my Windows environment, I create a Ubuntu-based virtual box for my application development (C++, java, etc.). 

However, with my new laptop, I want to make Ubuntu as my primary environment. For Windows specific things that I need, such as Outlook/Word/Excel, I intend to create a Windows-based virtual box.

Typically, I install plain Ubuntu server. Next, I simply run "sudo apt-get install xorg openbox."

This gives an environment where no unnecessary demons or applications are running. Every remaining bit of CPU cycle and memory resource could be used towards application development.

I can simply go with "xorg + openbox" and I know it will work. However, various posts on the forum suggest that lxde provides a "lighter" X environment. Also, from the online help pages, it appears installing Lubuntu is as simple as "sudo apt-get install xorg lxde." 

There are two things that I am confused about.

1. How is lxde lighter than openbox? Does lxde disable certain features within x-window that openbox is not doing?
2. What exactly am I getting with LXDE that I won't get with openbox? Remember that I don't need email client, image editing software, etc. All I need is the fastest application development experience.

This is not an argument. All I need to do is make a decision if I should just stick with openbox, as I have done in the past, or may be give lxde a chance.

Thank you in advance for your help.

Regards,
Peter

---

### Post by vasa1 on 2014-06-02
> **PeterTaps said:**
> ... However, various posts on the forum suggest that lxde provides a "lighter" X environment...
Lighter than what?

---

### Post by sudodus on 2014-06-03
> **PeterTaps said:**
> 
1. How is lxde lighter than openbox? Does lxde disable certain features within x-window that openbox is not doing?
2. What exactly am I getting with LXDE that I won't get with openbox? Remember that I don't need email client, image editing software, etc. All I need is the fastest application development experience.


1. It is not. LXDE is Openbox plus a lot of packages.

2. All the other packages in LXDE makes it a complete desktop environment with a panel etc, while Openbox is only a window manager.

*. If you are happy with Openbox, continue using it :-) I don't know how much you have tweaked it, but it works 'without tweaks' too, and that way it is lighter and the system will be snappier.

---

