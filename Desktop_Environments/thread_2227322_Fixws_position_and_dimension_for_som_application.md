---
title: "Fixws position and dimension for som application"
date: 2014-06-01
forum: Desktop Environments
---

### Post by trueancalagon-k on 2014-06-01
Hi, I have a problem with a program of my factory. the software house have no solution and on windows 7 there are no chance to solve the problem beside rebuild the program. We have tried to use third-party apps but, no good results.
We use a client program, Practor, and we need to set the position and dimensions of the windows of this program. I had think about and we have separate titles for every window so I had thought that we can make some rule like "win named "aaa" always on the left ad 0,0", "win named "bbb" always on the right at ...". So, I had tried some solution but after the inital position and size the user can always MOVE and RESIZE the window. And this must not happen. So, I have test the same situation on Fedora with KDE and KWin ha a lots of option but... is not stable. I can set position and the size of the window but I can use the mouse to resize and move the window. And I don't want that.


Do someone know if there is some application to set a fixed position and size of a window on linux?

---

### Post by deadflowr on 2014-06-01
You can all that with Ubuntu and unity.
Unity uses compiz and compiz has a few plugins that can help

First you would need to install ccsm(better known as compizconfig-settings-manager)
You would also need to make sure you have the plugins you need, basic compiz comes with a few default plugins, but there are a few more which you might need.
Open a terminal (for simplest installation)
```
sudo apt-get install compizconfig-settings-manager compiz-plugins
```
When that is installed, look for the program compizconfig-settings-manager.
Open it and  set window rule you want.
You can set the size, where it is, and whether or not it can ever be moved.

The two plugins to look at, for what purposes I see, are "Place Windows", which will allow you to place the windows in specific areas on the screen. And the plugin "Window Rules", which will aloow to set how the windows can function on the screen; eg resizablity, movabilty, etc,etc.

I hope some of this is helpful, or understandable.

---

