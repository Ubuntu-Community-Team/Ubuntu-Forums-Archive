---
title: "How to install themes in Ubuntu 8.10?"
date: 2009-01-12
forum: General Help
---

### Post by alejobar on 2009-01-12
Hi there, yesterday I did a clean install of ubuntu 8.10 on my pc, everything went ok and it seems to boot faster than Hardy Heron so I'm very happy about it. One thing that I couldn't figure out is how to install a theme, because I have a Moomex theme from Hardy Heron, and I use to just drag and drop the file in to preferences, appearence, theme and it was installed automatically, I tried that and i got an error, somethig like you can't drag a file in here. 

So the question is, how can you install a new theme?

---

### Post by gettinoriginal on 2009-01-12
Download your preferred theme (remember where you download it to), then System > Pref > Appearance > Theme > install

---

### Post by alejobar on 2009-01-12
> **gettinoriginal said:**
> Download your preferred theme (remember where you download it to), then System > Pref > Appearance > Theme > install

Thanks for your help, I'll try that when I get home and let you know if it work.

---

### Post by Jameshardy88 on 2009-01-12
if that doesn't work move the theme file to your desktop and use this code

sudo cp -r $HOME/Desktop/themename /usr/share/themes

---

### Post by alejobar on 2009-01-14
I figure it out! the problem was that I had the theme in a file and in order to install it using the install button I need to tar it or zip it, then I can install it without problems.

Thanks for your help!

---

