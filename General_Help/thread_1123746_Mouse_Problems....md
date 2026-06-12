---
title: "Mouse Problems..."
date: 2009-04-12
forum: General Help
---

### Post by Wally23 on 2009-04-12
Well I just recently did a dual boot with Vista and Ubuntu, and a couple days ago I was in Ubuntu and I was messing around with Compiz and after I was done I couldn't left click anything. After messing around with it a bit I found I could either Ctrl click or Alt click and then I could finally left click in windows. If I don't Alt/Ctrl click then all my cursor does is move the window. I'm kind of new to Ubuntu so if its really obvious whats wrong its probably because of that #-o

---

### Post by Wally23 on 2009-04-12
Any help would greatly appreciated. This is really bugging me, there has to be something I can do

---

### Post by aextance on 2009-05-04
You said bugging! :-D

Yes this is incredibly annoying. I have a similar problem that arose when I upgraded to Jaunty. I've gone back to Intrepid for the time being and reported this as a bug - 371563 in case you want to help out by saying what you're seeing. 

I think it might also be able to assign different keys to do the mouse functions, like the spare shifts and controls. 

Anyway, this is the main thread where I'm sharing my progress:

[http://ubuntuforums.org/showthread.php?p=7209852#post7209852](http://ubuntuforums.org/showthread.php?p=7209852#post7209852)

---

### Post by djchandler on 2009-05-05
You are not kidding when you say bugging.

I just upgraded from Hardy to Intrepid (preparing to go up to Jaunty after a MB and CPU swap, no reinstall) and after solving some BIOS problems finally got fglrx (AMD 780G) to work. I thought Compiz was working too. Then all of a sudden, while tweaking Compiz in Compiz Config Settings Manager, I could not left click anymore.

Turning off Compiz fixed the mouse problem, but of course I have no Compiz working now.

Mouse is a Logitech Wireless with ball sensors, M-RN68.

I'm going to check for a bug on LaunchPad. I've seen the other thread(s) referenced by Aextance, but none seem to relate to this particular problem.

---

### Post by aextance on 2009-05-06
Compiz is that flashy cube thing right? I've not installed it but I note that there are some hidden files related to it in my Jaunty boot. Does anyone know if it's supposed to have the basic capabilities installed as standard in Jaunty or something? Could that be the cause of my problems?

---

### Post by djchandler on 2009-05-06
Yes, Compiz is the "flasy cube thing." Compiz is activated in the last tab called Visual Effects in the Appearance applet.

System>Preferences>Appearance>Visual Effects

If that's activated, try selecting the first option,  i.e., None, aand see if the mouse problems go away.

Also, what video card are you using and what driver?

I have ATI Radeon HD 3200 Graphics integrated on my MB in the AMD 780G chipset, and I'm using the proprietary ATI flgrx driver, version 8.54.3.

---

### Post by djchandler on 2009-05-13
I think I've found a work-around for this left click mess. You can do this in gconf but I used CompizConfig Settings Manager. It doesn't install by default, so load it onto your HD via synaptic (compizconfig-settings-manager [0.8.2]) then try these steps:

Got to **System>Preferences>CompizConfig Settings Manager**

Scroll down to **Window Management**

Click (or press enter if you tabbed down with Compiz active) on the big **Move Window** button

Go over to the left side where it says **Button 1** across from the mouse icon to the right-middle thats next to the words **Initiate Window Move**--click, or, having tabbed over, press enter

When the **Edit Initiate Window** comes up, modify the command of *Button 1* by activating one of the four modifier keys, alt, shift, control, or super. Just changing which button to click did not work for me. I used the Super (Windows) key. Close that window. Exit by pressing **Back**. Now when you want to move a window, hold down the Super (Windows) key and grab it with a left mouse click. Release the mouse button when you reached the desired location for your window.

You may *have *to do this with Compiz active. That means a lot of tabbing and enter pressing. Luckily the left click problem was not present in the screen panels or the window title bars.

---

### Post by aextance on 2009-05-19
I'll bear this in mind. I don't have Compiz fully up and running and I'm not sure what will happen when I do, but for the time being I sorted stuff out by simply turning my touchpad off and using my trackpoint instead.

There was a difference between the two versions of Ubuntu, though, which I think is quite odd. The touchpad lasted for a couple of weeks longer in Intrepid than it did in Jaunty. Very strange.

---

