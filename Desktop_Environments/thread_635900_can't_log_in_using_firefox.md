---
title: "can't log in using firefox"
date: 2007-12-09
forum: Desktop Environments
---

### Post by grim192 on 2007-12-09
Hi everyone, this is my first post :)

i installed ubuntu 7.10 for the first time but i'm having problems with firefox, it wont let me log into any forums saying invalid username or password even though i've checked the details on several different forums. I've tried clearing the cache and cookies and checked java and java script is enabled. i've also tried re-installing the o/s but both before and after installing any updates i just can't get it to work. strangely i was able to log into these forums. anyone experienced this before ?

grim

---

### Post by grim192 on 2007-12-10
is this too early for a bump ? :(

grim

---

### Post by Rhubarb on 2007-12-10
There's a chance that there is something wrong with your firefox settings.

Please note:  This will delete any bookmarks, cookies, browsing history, firefox preferences.
Close firefox
Navigate to your home directory in nautilus (Places --> Home Folder)
Press Ctrl + H to show all hidden files.
go into the .mozilla directory
Delete the firefox directory there.
Restart firefox and check to see if it's working properly.

---

### Post by mozetti on 2007-12-10
Ok, let's get the basics out of the way:

Caps Lock/NumLock on?
Is your keyboard type correct? - open gEdit and type out your usernames/passwords to make sure they show up correctly.

---

### Post by kellemes on 2007-12-10
> **grim192 said:**
> Hi everyone, this is my first post :)

i installed ubuntu 7.10 for the first time but i'm having problems with firefox, it wont let me log into any forums saying invalid username or password even though i've checked the details on several different forums. I've tried clearing the cache and cookies and checked java and java script is enabled. i've also tried re-installing the o/s but both before and after installing any updates i just can't get it to work. strangely i was able to log into these forums. anyone experienced this before ?

grim

Can you give some examples of forums where you can't login?
I understand login-in to Ubuntu-forums works fine?

---

### Post by timseal on 2007-12-10
> **Rhubarb said:**
> There's a chance that there is something wrong with your firefox settings.

Please note:  This will delete any bookmarks, cookies, browsing history, firefox preferences.
Close firefox
Navigate to your home directory in nautilus (Places --> Home Folder)
Press Ctrl + H to show all hidden files.
go into the .mozilla directory
Delete the firefox directory there.
Restart firefox and check to see if it's working properly.

A better way to do the same thing:
```
firefox -ProfileManager
```
Then, just create a new profile and use that for your testing.

---

### Post by grim192 on 2007-12-10
> **kellemes said:**
> Can you give some examples of forums where you can't login?
I understand login-in to Ubuntu-forums works fine?

i cant log into:-

forums.overclockers.co.uk
[www.certforums.co.uk/forums](www.certforums.co.uk/forums)
[www.terminalcomputers.co.uk/forums](www.terminalcomputers.co.uk/forums)
forums.bit-tech.net

i can log into:-

[www.pistonheads.com/gassing](www.pistonheads.com/gassing)
ubuntuforums.org

> **mozetti said:**
> Ok, let's get the basics out of the way:

Caps Lock/NumLock on?
Is your keyboard type correct? - open gEdit and type out your usernames/passwords to make sure they show up correctly.

ive checked these already, tried typing them into the address bar.

grim

---

### Post by grim192 on 2007-12-10
i cant log in here now :confused:

grim

---

### Post by drenalinejunki92 on 2007-12-10
Im in the same situation. I can log into  some sites and not others, ironically i can get into ducatimonster.org but not hotmail. if it were consistent it would be easier. could certain sites have issues with linux?

---

### Post by drenalinejunki92 on 2007-12-10
hey 
well scanning round a bit i tried downloading  firebug and quite simply it fixed the problem. 
hope this helps

[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

-dren

---

### Post by grim192 on 2007-12-11
> **drenalinejunki92 said:**
> hey 
well scanning round a bit i tried downloading  firebug and quite simply it fixed the problem. 
hope this helps

[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

-dren

sweet i'll give that a try when i get home :D

i can get into hotmail and yougov all the time, these forums is the only inconsistent one.

grim

---

### Post by grim192 on 2007-12-11
it didnt work :(

grim

---

### Post by praxis22 on 2007-12-11
open a terminal and run a find for signons.txt (I think that's what it's called) That file contains your stored passwords, it's in your .mozilla directory in your default profile. remove that, (rename it) try again.

If that doesn't work move your entire .mozilla directory aside and try again. It could be that you're somehow blocking session cookies. 

Are you using either the noscript or adblock extensions? If so try disabling them, (though moving your .mozilla directory aside will also accomplish this.

---

### Post by grim192 on 2007-12-16
ive tried disabling all extensions with no luck.

i found 

/.mozilla/firefox/3b4e3p3z.default/signons2.txt
 
but i cant rename it

mv /mozilla/firefox/3b4e3p3z.default/signons2.txt /mozilla/firefox/3b4e3p3z.default/signons1.txt

grim

---

### Post by praxis22 on 2007-12-18
close firefox

**mv /.mozilla /.mozilla.old**

Then run firefox again.

---

