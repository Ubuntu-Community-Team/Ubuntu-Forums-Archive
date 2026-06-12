---
title: "Gnome won't load after power outage"
date: 2006-06-23
forum: Desktop Environments
---

### Post by wazoo on 2006-06-23
My machine lost power while logged into Gnome (a big regional power outage). My computer starts fine, and goes to login. But when I try to log in again, I hear the Gnome startup music, then I get top and bottom flashing panels for 8-10 times, then it freezes. If I hit ctrl-backspace, I get the nVidia screen -- which never goes away.

I also had KDE on this machine, and that still works. But I assume I have a borked gnome-session file somewhere. Any tips on how to recover?

Thanks.

---

### Post by rowanparker on 2006-06-23
Reinstall ubuntu-desktop (using apt-get).

---

### Post by Anduu on 2006-06-23
At the login screen instead of selecting "default" or "last" session select gnome and try to login.

---

### Post by wazoo on 2006-06-24
Yeah, I did try selecting Gnome, and that didn't work. I guess reinstalling the whole desktop is it, eh?

---

### Post by tukuyomi on 2006-06-24
Can you try with a new user profile?
On a command-line:  sudo adduser *new-user-name* and try to log-in with that new user

---

### Post by jatilq on 2006-06-24
I wonder if we are having the same problem. Last night I installed KDE, then upgraded it. My gnome session with xgl worked a little and when I did a restart it will either load the panels/freeze or say that the panels are already loaded. 

That is my default session gnome/xgl or just gnome. I reinstalled ubuntu-desktop through adept, but will try the newuser and then again through apt.

---

### Post by raptros-v76 on 2006-06-24
try reinstalling it through aptitude. do sudo aptitude reinstall ubuntu-desktop

---

### Post by wazoo on 2006-06-27
OK, just to let you all know how this is playing out. I tried:

1. Dragging all my .gnome folders away, so a new session might recreate them. No go.

2. I tried to reinstall through the sudo aptitude reinstall ubuntu-desktop command. No go.

3. I created a new user. That worked -- but I have no idea which profile is throwing things off. 

It occurred to me that another issue might be the Compiz stuff I installed.

So, since I've been using Ubuntu since two version back, and have mucked it up with all kinds of add-ons that I never actually used, I think I've decided to take a new Dapper Drake disk and take this back to scratch: a unified Gnome desktop that has the basics.

Thanks for your help, everybody.

---

