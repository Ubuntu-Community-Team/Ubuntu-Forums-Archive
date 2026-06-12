---
title: "Locked Desktop for All Clients"
date: 2013-06-21
forum: Desktop Environments
---

### Post by swu on 2013-06-21
I have a edubuntu 12.04 installation that is working fine. It's being used in a shared environment and what I would like to do is have the same desktop for all of my client stations, that cannot be altered. Or, if it is altered, when the station is rebooted, the "set desktop" is put back in place.

Any tips, url or 10-step program that will point me in the right direction? I know there is Kiosk mode, but I don't want to lock it to just browser use.

Thanks!

---

### Post by zombifier25 on 2013-06-22
There is guest session (which is selectable from the login screen), which does what you want: when logged in the guest session, you can do anything a normal user can (surfing the web, writing a document, NOT altering the system), but when logged out, all changes are wiped and the next person to use the guest session will be presented with a fresh desktop.

---

### Post by swu on 2013-06-23
We are using the autologin feature, so that's why we don't see the Guest login button. Can you auto login as "Guest?"   Can you also customize the desktop and settings for the Guest account? 

Thanks!

---

### Post by sudodus on 2013-06-23
You don't need to autologin as guest.

I think it works like this: if the other users have user id numbers below 500, they will not be shown at the log in screen, and the user will see only the guest user account, which is available without password. Try it to find out the details!

---

### Post by zombifier25 on 2013-06-24
> **swu said:**
> We are using the autologin feature, so that's why we don't see the Guest login button. Can you auto login as "Guest?" 
If you want to autologin as guest, then you need to add this line to the end of the file /etc/lightdm/lightdm.conf:
```
autologin-guest=true
```
Note that when you log out, you will still be presented with the login screen.
> **swu said:**
> Can you also customize the desktop and settings for the Guest account? 

Thanks!

It's slightly complicated. Basically, when a new user is created. the content of /etc/skel is copied into the user's home folder (which contains all the personal configs, etc.) But when a new guest user is created, the content of /etc/guest-session/skel is copied into the guest user's home folder. So what you want to do is to add stuffs into /etc/guest-session/skel.

tl;dr Create the directory first: 
```
sudo mkdir -p /etc/guest-session
sudo cp -r /etc/skel /etc/guest-session
```
Then create a new regular user, "example" for example. Log in that user and customize whatever you want. When done, log out and log back in your admin account, and run this command:
```
sudo cp -r /home/example/* /etc/guest-session/skel
```
to make sure the guest receive the customizations. When done, delete the user "example".

---

### Post by swu on 2013-06-25
In my lts.conf file I removed the auto login and set LDM_GUESTLOGIN = True

I still have the entries for IP/Username/Password.

Rebooted everything. When I start up a client station, I now get a login window and below it, a button to login as "Guest."  When I login as Guest, I see the desktop and settings that are associated with the LDM_USERNAME for that client station. So the Guest is inheriting those settings.  As Guest, I can change settings, move things to the desktop, change the background, move programs on/off the toolbar.

When I logout and back in, everything is still there, as it was when I logged off. So the Guest account can change things and those changes are being saved.

What am I doing wrong?

Thanks in advance!

---

### Post by zombifier25 on 2013-06-26
Well, you should have stated that you're using LTSP, whose guest session requires a normal account. My post refers to LightDM, the login screen of local machine, which has the disposable guest feature described. I have no knowledge with thin clients outside Google so I can't help you, but one way to do it is to create a log out script which automatically wipes everything clean.

---

### Post by swu on 2013-07-03
Sorry, edubuntu has always meant LTSP to me...   

If the "Guest" environment isn't going to really lock things like we'd like it to, how can we simply restore the default desktop when kids trash the one that's up? That might be the simplest way for right now.

Thanks!

---

