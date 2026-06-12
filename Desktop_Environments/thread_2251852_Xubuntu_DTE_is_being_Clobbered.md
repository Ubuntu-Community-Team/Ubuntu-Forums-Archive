---
title: "Xubuntu DTE is being Clobbered"
date: 2014-11-07
forum: Desktop Environments
---

### Post by kim-lyon on 2014-11-07
Hi, need some serious help. I have just bought a Dell XPS13 developers edition running Ubuntu 12.04. I installed XUbuntu and set it up as I usually do. I created several users. One of these (not the initial one) being my private user account. It worked perfectly ok. for the first week+ . I solved the touchpad issue and the white noise issue in the last couple of days. Then I went out yesterday evening and operated the ultrabook without any problems but not on any WiFi network. When I got back I fired it up and logged onto my WiFi network and the XUbuntu had big problems :- 

1) the window borders and the bar at the top of the windows is missing, 2) Thunderbird is only displaying halfway across, 3) the workspace button is only showing 1 workspace - if I increase it to 2 it will not display the 2nd. in either the list nor in the taskbar at top, 4) the windows are not coming to the front - if I have the browser on top on the email and I click on the email it does not come to the front, 5) I can grab Thunderbird and move it up under the taskbar to the top of the screen, I can't grab the browser - Chromium. 

Unity does display ok. . I backed up then deleted the private user and then reinstalled it from scratch. It was working perfectly ok. . I was logging off and on and rebooting without any problems. I then went out and fired it up without logging onto a WiFi network and, again, the XUbubtu DTE was clobbered. Help in solving this is much appreciated - thanking you very much in advance.

---

### Post by kim-lyon on 2014-11-07
Fixed - in terminal type - xfwm4 -- replace - [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361) .

---

### Post by Bucky Ball on 2014-11-07
Good news and well done. Please help future travelers by using the second link in my signature. Good luck. ;)

---

