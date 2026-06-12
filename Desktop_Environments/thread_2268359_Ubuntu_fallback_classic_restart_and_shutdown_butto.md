---
title: "Ubuntu fallback classic restart and shutdown button problem on cancel"
date: 2015-03-08
forum: Desktop Environments
---

### Post by ubuserone on 2015-03-08
I tried reinstall [http://askubuntu.com/questions/452665/fallback-to-gnome-classic-desktop-ubuntu-14-04](http://askubuntu.com/questions/452665/fallback-to-gnome-classic-desktop-ubuntu-14-04) a fallback to classic.

I notice the shutdown or restart option doesn't get cancel even I click on cancel when it pop out.
When I click cancel , it get shutdown , even I click close it also get shutdown.
And fix for the problem.It happen on restart too.

---

### Post by v3.xx on 2015-03-08
What window manager are you running?
```
update-alternatives --get-selections | grep x-window-manager
```
or
```
wmctrl -m | grep Name | awk '{print $2}'
```
You could boot into your guest session and see if it also happens there.

And its called fallback in 12.04 and flashback in 14.04.  But you can install flashback with the fallback command in 14.04, it gets confusing.

---

### Post by ubuserone on 2015-03-09
> **v3.xx said:**
> What window manager are you running?
```
update-alternatives --get-selections | grep x-window-manager
```
or
```
wmctrl -m | grep Name | awk '{print $2}'
```
You could boot into your guest session and see if it also happens there.

And its called fallback in 12.04 and flashback in 14.04.  But you can install flashback with the fallback command in 14.04, it gets confusing.
```
x-window-manager               auto     /usr/bin/metacity

``````
wmctrl -m | grep Name | awk '{print $2}'
The program 'wmctrl' is currently not installed. You can install it by typing:
sudo apt-get install wmctrl




```
Should I install wmctrl ?

---

### Post by v3.xx on 2015-03-09
Wmctrl has several uses, but is totally optional.  You were either running compiz or metacity and now we know :)

What about using the guest session?

---

### Post by haytham-med on 2015-03-12
same problem here, happens also on logout, 

"What about using the guest session? 				"
same behaviour in guest session in fallback not unity

---

### Post by v3.xx on 2015-03-12
Could it be

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1234394](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1234394)

[http://ubuntuforums.org/showthread.php?t=2182090](http://ubuntuforums.org/showthread.php?t=2182090)

---

### Post by Kleenux on 2015-03-31
It's a known bug in 14.04 fixed in 14.10 - **not** fixed in 14.04 ?! 14.04 is **LTS** though ...

---

