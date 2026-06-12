---
title: "Drivers: Adjustable Resolution on a 7&quot; Screen"
date: 2012-09-19
forum: Desktop Environments
---

### Post by fiLmNut on 2012-09-19
Hello UBUNTU. 

The title says it all basically. I am after a driver that allows me to toggle my screen resolution beyond the ONLY single available option for resolution on my 7" screen Netbook. The majority of the OS is unreachable without such a driver. I am as green with Ubuntu as it gets, so if answering, I am used to Microsoft/Windows and alike and would need detailed step by step answers. From what I have heard, installation techniques are the same basically, it's just the language/terminology and order of things that needs special attention.

Here is what I have Ubuntu running on: [http://usa.asus.com/Eee/Eee_PC/Eee_PC_701SD/](http://usa.asus.com/Eee/Eee_PC/Eee_PC_701SD/)

Thank you so much, fN.

---

### Post by cortman on 2012-09-19
What is the top resolution for your netbook?
Have you tired resetting it in the "Displays" settings menu?

---

### Post by fiLmNut on 2012-09-19
800X480

16:10

Normal.

Yes, I have.

---

### Post by cortman on 2012-09-19
What's the output of

```
lspci
```

and

```
xrandr
```

---

### Post by fiLmNut on 2012-09-20
I'm sorry, what?

---

### Post by cortman on 2012-09-20
Open up a terminal and type

```
lspci
```

hit enter. Post what the terminal returns from that command. Do teh same with

```
xrandr
```

---

### Post by coffeecat on 2012-09-20
I used to have an Asus EeePC 7" until I disposed of it. Every version of Ubuntu I tried on it defaulted to the correct screen resolution of 800x480. I admit this was more than a year ago, but I'm sure this is still true. In which case, adjusting your screen resolution is not the answer. Not that you could - you cannot get a resolution above 800x480 and a lower resolution would be pointless. And if you have an Intel graphics, the driver that Ubuntu comes with is the only one you can try.

It sounds as though your problem is using the standard Ubuntu desktop on such a small screen. Which version of Ubuntu are you using? If the standard Ubuntu with the Unity desktop, you might be better off using the Lubuntu variant which, being leaner, would run better anyway.

If you are using the Unity desktop, one thing you need to do is to reduce the size of the launcher, and a hint for you. If you have a window spilling off the bottom of the screen and you want to move it above the upper edge of the screen, hold down the alt key and grab any part of the window with the mouse and then move it.

---

