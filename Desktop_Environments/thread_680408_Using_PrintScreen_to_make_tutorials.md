---
title: "Using PrintScreen to make tutorials"
date: 2008-01-27
forum: Desktop Environments
---

### Post by weigh2tall on 2008-01-27
I didn't want to hijack any threads that seemed close to this problem, and I think this is a pretty simple question.

I am running Gutsy, with a USB keyboard plugged in to a StarView KVM switch (I have tested this without the KVM in the loop but the problems still exists)

What I've run into is Printscreen works fine if I want to take a picture of the screen or active window but If I am trying to take a screenshot of accessing a certain menu option printscreen doesn't work.  The nearest I can figure is that Ubuntu is waiting for input to the menu before it allows the printscreen.  

For example if I want to take a picture of the Firefox browser window it works flawlessly, but if I wanted to take a picture of getting to View -> Toolbars -> Customize, nothing happens.

My current workaround is to use Gimp's screen capture with a time delay, but I was wondering if this is something that everyone has run into? and if so is there a fix that would allow me to take pictures of the menus with the printscreen button?

Thanks!

---

### Post by mojoman on 2008-03-02
> **weigh2tall said:**
> I didn't want to hijack any threads that seemed close to this problem, and I think this is a pretty simple question.

I am running Gutsy, with a USB keyboard plugged in to a StarView KVM switch (I have tested this without the KVM in the loop but the problems still exists)

What I've run into is Printscreen works fine if I want to take a picture of the screen or active window but If I am trying to take a screenshot of accessing a certain menu option printscreen doesn't work.  The nearest I can figure is that Ubuntu is waiting for input to the menu before it allows the printscreen.  

For example if I want to take a picture of the Firefox browser window it works flawlessly, but if I wanted to take a picture of getting to View -> Toolbars -> Customize, nothing happens.

My current workaround is to use Gimp's screen capture with a time delay, but I was wondering if this is something that everyone has run into? and if so is there a fix that would allow me to take pictures of the menus with the printscreen button?

Thanks!

I'm using scrot and it's in the repositories. I've got fluxbox (the wm I use) set up so that scrot takes a screenshot when I hit 'print screen'. Scrot just takes a screenshot, it doesn't care if you've got menus open, applications running and whatnot, it just plain and simple captures whatever is on the screen.

/mojoman

---

