---
title: "Xauth Error??"
date: 2005-10-03
forum: Desktop Environments
---

### Post by xthaparian on 2005-10-03
Hi Guys

I was playing aroung with xorg.conf
But after some playing around and using CTRL+ALT+Backspace

I as a user is getting the error of .Xauthorization. Please see attached screenshot for details???

Anyhelp please 

I cannot install packages and do system changes??

---

### Post by KingBahamut on 2005-10-03
Looks like X got screwed up. Did you make a backup of your xorg.conf file?

---

### Post by xthaparian on 2005-10-03
yes..and the xorg.conf is working fine..with no problems.

I mean I can do the startx after CTRL+ALT+Bkspace and i get right into graphical mode..

---

### Post by xthaparian on 2005-10-03
If I do reinstall of xorg...will that work??? what do you guys say...

I have my xorg configured tog et the Opengl accelaration etc..all set

---

### Post by XDevHald on 2005-10-03
Try reinstalling xorg and see how the process goes, also, please don't reboot until the problem is fixed as you might just get a nasty error from X, you don't want that.

Keep us noted.

---

### Post by xthaparian on 2005-10-03
ok..this is what I did..

CTL+ALT+Bkspace and from terminal i did

$ sudo startx

now I went to synaptic package manager and did reinstall of the xorg. then after that I started as user and still no success..

But when I looged out, i noted a message on the terminal

It said that 
"changes cannot be saved to .Xautoritzation"

Now I did change the 
$ sudo chmod a+x .Xauthorization

but still i get the error..

ANy other help??

---

### Post by xthaparian on 2005-10-03
This is how it looks in the desktop..

I see some 'x' mark on the file .Xauthority and .Xauthority.bak

can this be of help to you guys??

---

### Post by xthaparian on 2005-10-03
Ok..

I restarted aftet installing Xorg and looks like its perfect now..

I must have screwed something in the library..

Thanks for the response from every one..

I have no errors not..

Kool

---

