---
title: "installing xfwm4 from svn"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by alvinistic on 2007-11-11
Hi all,

I'm running Ubuntu Gutsy with metacity replaced by xfwm4 to get its stable compositor. So far so good, I have to say. It's enough eye candy for me and it does not slow down my computer :D

But apparently the svn in gutsy repo has a bug working with awn, which cause xfwm not able to focus on any window. The xfwm4 in the svn repo has this fixed.

Can anyone please guide me on how to install (or even better build package) from svn repo?
Thanks in advance.

---

### Post by alvinistic on 2007-11-11
Alright, done some research. Here is what I did:

sudo apt-get build-dep xfwm4

svn co [http://svn.xfce.org/svn/xfce/xfwm4/trunk](http://svn.xfce.org/svn/xfce/xfwm4/trunk) xfwm4
cd xfwm4
./autogen.sh --enable-compositor
make

and I'm supposed to continue with: 
sudo make install

Is there any way to know which files are getting installed? Because I'd like to be able to uninstall it one day if it screws up my system.

Any help? 

PS: Tried with sudo checkinstall with no luck.... :(

---

