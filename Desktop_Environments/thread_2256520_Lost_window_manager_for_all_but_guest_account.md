---
title: "Lost window manager for all but guest account"
date: 2014-12-13
forum: Desktop Environments
---

### Post by neil.the.blue on 2014-12-13
Hello,

I have ubuntu 14.10.

I was trying to resolve a problem with the machine not resuming from suspend and so installed fglrx, but it prevented unity starting when I logged into my account, I got the desktop but no menus or dash. So I removed the driver, but this still my account will only show the background image when I log in. 

So I created a test user and found that logging in with that user gave a normal desktop.

Following some google searchers I tried to reset unity with:

```

$ sudo apt-get autoremove ubuntu-desktop 
$ sudo apt-get autoremove unity 
$ sudo apt-get update 
$ sudo apt-get install unity
$ sudo apt-get install unity-2d 
$ sudo apt-get install ubuntu-desktop 
$ sudo shutdown -r

```

This didn't work and now I can no longer get a normal desktop from any new test accounts. I can however get a desktop using the guest account I am in now.

Please can any one advise :)

---

### Post by neil.the.blue on 2014-12-13
OK I have got some of this working by moving .config folder to a backup. I them logged in and got a basic desktop. I then replaced each sub folder in .config from the backup and rebooted until the .config folder was re-populated and I had a desktop. 
I guess there must be a better way to fix this but it worked :)

---

