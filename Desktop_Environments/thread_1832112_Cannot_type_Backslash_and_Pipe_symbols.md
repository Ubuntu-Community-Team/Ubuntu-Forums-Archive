---
title: "Cannot type Backslash and Pipe symbols"
date: 2011-08-24
forum: Desktop Environments
---

### Post by jaz6ix on 2011-08-24
Hello, I cannot type Backslash(\) and Pipe(|) symbols with my keyboard in Ubuntu 11.04 x64 Desktop which runs as guest in Windows 7 x64 VirtualBox 4.1.0.

In windows I can type backslash with the key next to left-shift and I can type pipe key using the same key while holding shift. In ubuntu however, I get < or > respectively which means that key is completely useless for me in ubuntu because I already have other keys to type these.

I'm using US keyboard layout.

I also asked this question in superuser.com but it seems there is nobody who knows the answer. [http://superuser.com/questions/326908/no-pipe-symbol-in-ubuntu-11-04-running-in-windows-7-x64-virtualbox](http://superuser.com/questions/326908/no-pipe-symbol-in-ubuntu-11-04-running-in-windows-7-x64-virtualbox)

Thanks

---

### Post by Bradburts on 2011-09-15
Hi,
I have the same problem in 10.04 server. Pretty sure I choose the right keyboard during install etc as well.
I could not find an answer.
So I installed SSH and use Putty.
 
sudo apt-get update
sudo apt-get install openssh-server
 
I had a lot of other problems using the console, could not see what scrolled off the screen, 'd' key minimised window unless full screen, could not copy and paste text etc etc.
So Putty was the best option & forget the console!
 
You are using Desktop but I think that you could get round most issues using Putty.
Post if you find the proper answer!

---

### Post by yjchin on 2012-02-02
i had the same problem because of a wrong keyboard layout.
you can change  your keyboard layout by:
sudo dpkg-reconfigure keyboard-configuration

---

