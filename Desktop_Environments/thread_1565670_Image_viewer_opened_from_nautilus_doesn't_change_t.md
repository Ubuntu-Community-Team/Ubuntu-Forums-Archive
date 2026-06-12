---
title: "Image viewer opened from nautilus doesn't change the active window"
date: 2010-09-01
forum: Desktop Environments
---

### Post by yoel.koenka on 2010-09-01
Hi all,
There's something very annoying about how Nautilus opens "image viewer" windows.
They open, I can see them, but when I press the keyboard, it's still Nautilus which gets the commands.
This is because Nautilus stays the active window!

Most annoyingly, when I want to have a quick look at an image, and then close it, Nautilus closes instead (Alt+F4).

Does anyone know what I'm talking about?
How to solve it?

Thanks a lot and good day,
Yoel

---

### Post by gadelat on 2011-01-23
i've same problem

---

### Post by Krytarik on 2011-01-23
Check the "Focus Prevention Level" in "System -> Preferences -> CompizConfig Settings Manager -> General Options -> Focus & Raise Behaviour". I have it at "Low", which is also the default, any higher value prevents the opened image window from taking focus. Didn't know that option until now either.

---

### Post by yoel.koenka on 2011-01-24
Thanks a lot!
Can you please tell me how to do that from the command line?
I don't have that menu item.

---

### Post by Krytarik on 2011-01-24
Then just install CCSM:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Humphreybas on 2012-02-01
Mine was at the default, low like you said, but to get Image Viewer to focus I had to turn it off completely. I am not sure what impact that will have on other things yet. But it is quite undesirable that this isn't working out of the box.

---

### Post by cmavr8 on 2012-02-19
> **Humphreybas said:**
> Mine was at the default, low like you said, but to get Image Viewer to focus I had to turn it off completely. I am not sure what impact that will have on other things yet. But it is quite undesirable that this isn't working out of the box.


Any side-effects noted?

---

### Post by Humphreybas on 2012-02-20
No none, upon your question I googled briefly and the side effects I should have noticed where windows popping up in front of my active window (for example Update Manager I can imagine). But even update manager stays nicely under my firefox for example. And besides update manager I can't imagine any windows just popping up (maybe different without adblock plus).

---

