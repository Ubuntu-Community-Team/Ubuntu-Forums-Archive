---
title: "Trying to get new Icons installed"
date: 2009-08-19
forum: Desktop Environments
---

### Post by Rick Abraham on 2009-08-19
Hi guys sorry to be a pain but I have another quick question.
I just downloaded a icon package called Mashup.
So I have a folder called Mashup on my desktop with a heap of stuff in it.

Now heres the question how do I install it ???????????????

---

### Post by Rick Abraham on 2009-08-19
Im using Ubuntu 9.04 Gnome if that helps any

---

### Post by mcduck on 2009-08-19
Go to System/Preferences/Appearance, Theme-tab, and then just drop the icon package into the window.

Since it's just an icon package and not a complete theme you'll then have to click "Customize" and select your new theme for use in the Icons-tab.

---

### Post by wotsit on 2009-08-19
you would need to make sure that it is an icon set that can actually be installed, rather than just some folders with icons in them. Look for some sort of index.theme file or similar.
 
The usual way would be from the terminal. cd to the directory containing your theme folder, then
 
```
sudo mv themename ~/.icons
```
 
for just you, or
 
```
sudo mv themename /usr/share/icons
```
 
for all users
 
then by system> preference> appearance, click on edit custom theme, and the new set should appear under the icons tab.

---

### Post by Rick Abraham on 2009-08-19
thanks guys all is working ok

---

