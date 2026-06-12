---
title: "Login screen is just black and a mouse, can't log in!"
date: 2010-08-11
forum: Desktop Environments
---

### Post by reydempto on 2010-08-11
Hello again, folks!

My girlfriend has a laptop with a French-language install of Ubuntu 10.04. She wanted a mac theme installed, and wanted to do it herself to learn how to use linux. She used a tutorial that has several steps, but I have pinpointed where things went wrong. Here is the tutorial she followed:

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-max-osx-leopard/2008/07/23")

She was unaware of the difference between 'hardy' and 'lucid' names, so she didn't know it was the incorrect tutorial.

Things went wrong for her when she got to the step named "Change the menubar", at the step where you install 'globalmenu'. 


> Next, we are going to install globalmenu so as to display the menubar for each application. In your terminal,

```
cd Mac_files
wget http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz
tar zxvf gnome-globalmenu-0.4-svn964.tar.gz
cd globalmenu
sudo dpkg -i *.deb
```

If you have any errors when installing the package, try

```
sudo dpkg -i –force-overwrite *.deb
```

If you are having some installation problems with the gnome-globalmenu-applet, try

```
sudo apt-get install -f

```
Once finished, right click on the top panel and select ‘Add to panel‘. Scroll down the list and add ‘Global Menu Applet‘.

```
menubar-add-globalmenu
```

You might not see anything initially. Log out and log in again, you should now see the menubar for each application showing on the panel.

But when she logged out and back in, she got a blank black login screen with a mouse, and we can't do anything from here. We are able to access a terminal by pressing Ctrl+Alt+F2.

What can be done to reverse the changes so that the gnome login screen will show up again?

---

### Post by reydempto on 2010-08-11
Nevermind, I fixed it by connecting it to my wired internet source, then running

```
sudo apt-get update && upgrade
```

---

