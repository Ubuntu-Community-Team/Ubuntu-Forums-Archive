---
title: "changing the screen output for nvidia-glx"
date: 2008-06-07
forum: Desktop Environments
---

### Post by 00zer0 on 2008-06-07
Hi there, ill start by saying im very new to ubuntu.

My video card (GF 7600) has two DVI plugs on the back of it. When i installed Ubuntu a few weeks ago the screen was pluged into DVI'1.

to keep it short, there seems to be a fault with the DVI'1 output now. (with the card itself) 

if I plug the screen into the DVI'2 slot, when the computer powers up the screen comes on as usual. The 'ubuntu' splash screen comes up and shows the loading process.
But the screen then turns off with the message 'no input detected' when the login window should come up.
If i press Ctrl+alt+F1, the screen comes back on at the console login.

is there something in X config that is telling it that the screens pluged into DVI'1?....everything else (the console or when it boots) doesnt seem to care..or it sends a clone display to both DVI's..with only one screen I cant tell.

Is there a file somewhere that I can edit to have my display sent to DVI'2?

I tryed putting in the Ubuntu Live cd, and it loaded up all the way into gnome fine with the screen in DVI'2
I have also tryed
"sudo apt-get remove nvidia-glx-new"
if i do a:
"sudo /etc/init.d/gdm restart"
the display comes up with the message 'graphics running in safe mode' which limits me to 800x600 but does allow me to login as usual


I tryed to reinstall nvidia-glx-new from the package manager, but  i still have the same problem when I restart to make the changes take affect.

someone please tell me whats going on : (

---

