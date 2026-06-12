---
title: "Locale in Firefox not working"
date: 2005-04-10
forum: Desktop Environments
---

### Post by 8086 on 2005-04-10
Because I was not connected to the net whilst installing UBUNTU I could not download the language packs for norwegian at that time. I did so afterwards, though, but the menus are all in English, even though I have installed all the language packs I need.
I do not get it. In "Help->About" it says it is an En_us build, but as long as I have the language packs that should not really make a difference. It is not like there is an norwegian ubuntu build, anyway...

Can anyone help (this concerns *any* locale - not just Norwegian)?

---

### Post by erkki70 on 2005-04-10
Hi,
You should be able to select your language from the Language Menu on the login screen if locales are correctly installed.
When you'll click the Language button a window will pop-up with all locales installed and you'll just select Norwegian-UTF8 probably.
After typing your name and password a new window will pop and ask if you want to make this language default or use it only for current session.

In case you don't see Norwegian in the list you can try the following on console:
 ```
sudo dpkg-reconfigure locales
```
type your password and select the language pack you need to install from the list, so this one I guess **no_NO.UTF-8 UTF-8**.
Once done, you'll be able to use Ubuntu in Norwegian.

Good luck and hope it helps.
Cheers,
Erkki

---

### Post by 8086 on 2005-04-12
I got a message saying I had recieved a reply, but since I can't see it in the thread I'll post it here (didn't work though!). 

8086

--------------------------------------------------------------

Hi,
You should be able to select your language from the Language Menu on the login
screen if locales are correctly installed.
When you'll click the Language button a window will pop-up with all locales
installed and you'll just select Norwegian-UTF8 probably.
After typing your name and password a new window will pop and ask if you want to
make this language default or use it only for current session.

In case you don't see Norwegian in the list you can try the following on
console:
 sudo dpkg-reconfigure locales
type your password and select the language pack you need to install from the
list, so this one I guess no_NO.UTF-8 UTF-8.
Once done, you'll be able to use Ubuntu in Norwegian.

Good luck and hope it helps.
Cheers,
Erkki

---

### Post by 8086 on 2005-04-12
[QUOTE=8086]Because I was not connected to the net whilst installing UBUNTU I could not download the language packs for norwegian at that time. I did so afterwards, though, but the menus are all in English, even though I have installed all the language packs I need.
I do not get it. In "Help->About" it says it is an En_us build, but as long as I have the language packs that should not really make a difference. It is not like there is an norwegian ubuntu build, anyway...

Can anyone help (this concerns *any* locale - not just Norwegian)?[/QUOTE]
 Unfortunately the tip did not work - Firefox is stil showing its menus in English even though I can remember installing the firefox-no-*sth*-locale. All the Gnome menus are showing in Norwegian, so the settings there are allright, I guess.
I even tried:
** sudo dpkg-reconfigure locales**
But that didn't do me any good either. Norwegian.UTF8 was already selected, so the only thing I did was to also select the NO.ISO88591 package. Did not do any good (or bad:) for me.

---

