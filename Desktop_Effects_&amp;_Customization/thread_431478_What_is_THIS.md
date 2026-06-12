---
title: "What is THIS?"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by Jhongy on 2007-05-03
In this Beryl Video, there's a plugin that unfolds all workspaces out of the lower left corner, and allows you to select windows and drag them between the workspaces... very cool!

Also, the two-sided window thing... (although I don't see a use for that one myself).

How do I activate these? I'm using Beryl from the Ubuntu repos.

J

---

### Post by blackened on 2007-05-03
It's all in the SVN of Beryl (that I found to be unstable in Feisty, so use at your own risk).

Add Beryl SVN repo to /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
```

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Add the authentication key
```
wget http://3v1n0.tuxfamily.org/DD800CD9.gpg -O - | sudo apt-key add -
```

Update sources
```
sudo apt-get update
```

What you're looking for is mostly in the unsupported plugins package
```
sudo apt-get install beryl-plugins-unsupported
```

---

### Post by Jhongy on 2007-05-03
Thanks for the detailed post.

I uninstalled all Beryl packages, added the repo, and installed all laterst versions of the Beryl packages, including the plugins-unsupported.

While there are a few new options, such as the desktop "wall", I don't see those specific ones in the video...

:confused:

---

### Post by blackened on 2007-05-03
Do you have a link to the video? Maybe we can determine which plugin it is if we see for ourselves.

---

### Post by blackened on 2007-05-03
I think the desktop wall might be what you're talking about. In order to have it display properly, you need to increase your number of desktops in the "General Options". Also play with the Horizontal/Vertical Virtual Size sliders.

For the double-sided windows look under Window Management in Group and Tab Windows.

---

