---
title: "Cannot login to my session"
date: 2014-08-27
forum: Desktop Environments
---

### Post by nat00 on 2014-08-27
To sumarize, the issue is this : When I turn on my computer, the login screen comes up just fine, and my session shows up. However, when I enter the right password, the screen blinks black and then goes back to login screen.

I can login as a guest and the computer works just fine. I checked via tty and all my files are still where they should be. I restarted the computer and it changed nothing. I got this issue in ubuntu 13.10 , I updated to 14.04 through tty in hope of solving the problem, but it still does the exact same thing. 

It seems that my session still exists, just that I can't access it. I can't explain it, and I have no idea what caused it. 

If you can explain it or give me advice, I would be gratefull.

---

### Post by deadflowr on 2014-08-27
What does 
```
ls -la .Xauthority
```
tell you?
It should list your username(possibly twice, the first means owner and the second means group)

You, as you might already know, can do this by logging in via tty1-6 (ctrl+alt+F1-6)
The full path to the file would be /home/your-username/.Xauthority, but if you are already in your home folder, which is the default you can run the above command just the same.

---

### Post by nat00 on 2014-08-28
I ran the command 
> ls -la .Xauthority

and it returned

>  -rw------- 1 root root 56 august 27 09:24 .Xauthority 

---

### Post by deadflowr on 2014-08-28
Try either to change ownership back to you
```
sudo chown yourusername:yourusername .Xauthority
```
or maybe even try to delete it (you can simply move it and change the name. The file should regenerate a new one
```
sudo mv .Xauthority .Xauthority.bak
```

I would opt for the first option first and see what happens.
Since you're most likely doing this from tty1 or 2 or something, after you've made the changes run
```
sudo restart lightdm
```
This will restart the login session so you can see if the changes took effect immediately.
I do not remember if it might require a full reboot, though, but just in case you could also try
```
sudo reboot
```

Hope something here helps...

---

### Post by nat00 on 2014-08-28
Thanks.

I used

> sudo chown yourusername:yourusername .Xauthority

and then

> sudo restart lightdm

and it was fixed. Now my computer seems to work just fine.

---

