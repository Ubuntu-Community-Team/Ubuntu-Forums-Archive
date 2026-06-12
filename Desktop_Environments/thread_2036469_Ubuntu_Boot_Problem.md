---
title: "Ubuntu Boot Problem"
date: 2012-08-02
forum: Desktop Environments
---

### Post by JuanTwoThree on 2012-08-02
I have installed Ubuntu onto my computer and I'm having trouble getting it to start up correctly. It used to boot into what I believe was the terminal (complete ubuntu noob, so I'm not sure), and it asked for my login info. I tried to perform some things suggested in _[COLOR=DarkOrange][this thread]("http://ubuntuforums.org/showthread.php?t=2036053")[/COLOR]_, and since then, the few times I've restarted have either taken me to a black screen or an actual login screen that just leads me to the same black screen.

So far I've tried to set nomodeset using _[COLOR=DarkOrange][this]("http://ubuntuforums.org/showthread.php?t=1613132")[/COLOR]_, only to have an error. I have also tried to use Boot-Repair and _[COLOR=DarkOrange][here's the pastebin]("http://paste.ubuntu.com/1124183/")[/COLOR]_.

I have a NVIDIA graphics card which I've read may cause problems. It's a NVIDIA GeForce 6150. And an AMD Athlon 64 X2 Dual Core processor, if that matters.

---

### Post by ranger1021994 on 2012-08-02
First line you type your username and press enter then enter your password.

Then type 
> sudo apt-get install nvidia-current
and then reboot your PC
If it boots up in terminal interface try pressing Ctrl+Alt+F7

---

