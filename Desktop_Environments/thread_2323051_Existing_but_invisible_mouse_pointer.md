---
title: "Existing but invisible mouse pointer"
date: 2016-05-02
forum: Desktop Environments
---

### Post by Samuele_Giraudo on 2016-05-02
Hello,


my problem is this. Just after reactivating my system after a sleep or a screen lock, the mouse cursor becomes invisible. The mouse and the actions it offers remain however active. I can indeed still use the mouse provided I guess where the pointer is. This problem occurs only in this circumstances: after a system boot, the pointer is visible and functioning normally.

I use Xubuntu 16.04 with the XFCE desktop. Before, I used Ubuntu 15.10 and I had no problem.

Thank you in advance for your help.

---

### Post by QDR06VV9 on 2016-05-02
So far this is a cheesey hack.

```
sudo apt-get install unclutter

```
And then put the following in a script on the desktop.
```
unclutter -idle 1 -root -grab -visible

```
Name it **"unclutter.sh**"
Now this
```
chmod +x unclutter.sh

```
Then, after the mouse pointer disappears after suspend, use mouseover of icons to target the script and run it; this will start unclutter, which will simply hide (the already invisible) mouse pointer after 1 second of mouse inactivity; but then when you move the mouse after that, finally the mouse pointer will show :) ... however note that to stop unclutter after that, you'd have to do from terminal: 
```
sudo killall unclutter

```
This will stop uncluter from running in the background

---

