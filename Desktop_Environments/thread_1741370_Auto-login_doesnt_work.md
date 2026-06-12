---
title: "Auto-login doesnt work?"
date: 2011-04-28
forum: Desktop Environments
---

### Post by edgue on 2011-04-28
Hello,

I am running xubuntu 11.04 (ISO from early this week). During install, I selected to NOT auto login but to present this gdm panel where I have to enter the password (or other users could log in).

Now I decided to enable auto-login (and to start the screensaver right afterwards) ... so I opened up the "login screen settings" (systems menu), unlocked that window and changed it to "login as xxx".

Then i rebooted and would have expected to be greeted with my screen saver on a logged-in session afterwards. But what happens is that there is a gdm panel sitting ... showing me

AUTOMATED login
Other

where the first item wont do anything.

So I have to select other and enter user name + password ?!

Is that how it is supposed to work?

---

### Post by mutinystudios on 2011-04-28
Give me a screen shot because i dont really understand what your saying. But if i took in any information it screams MISCONFIGURATION

---

### Post by edgue on 2011-04-28
> **mutinystudios said:**
> Give me a screen shot because i dont really understand what your saying. But if i took in any information it screams MISCONFIGURATION

OK, I attached a png of the settings window (where I grayed out my user name). 

Then I rebooted, and as there is no running system, I cant create a screen shot, so more precisely what I see:

a) xubuntu boots up ... so it says "xubuntu" for a few seconds
b) screen flashes, "nvidia" shows up because my nvidia driver loads
c) the typical gdm/xubuntu login panel:
blue-ish background, with a grey panel and the xubuntu mouse icon.

Normally that panel would say: "login as xyz"; I would press enter and
provide my password.

But now, the panel says:

Automatic Login
Other

when I hover the mouse over the first row, a help text shows up that says:
"Automatically log in the system after selecting options"

When I click on the first row ... nothing happens.
So, the only thing I can do is: 
- click on "Other"
- then I have to enter username
- then I have to enter password
- then the xfce session is started

That is not what I expected ...

btw:

/etc/gdm$ cat custom.conf 

[daemon]
DefaultSession=xubuntu
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=guenthne
AutomaticLogin=guenthne
TimedLoginDelay=5

Sounds pretty reasonable

---

### Post by edgue on 2011-07-28
RESOLVED:

this is not a generic (x)ubuntu problem ... but:

our company enforces a toolset for security stuff on our machines.
This toolset prevents auto-login. Simple as that.

---

