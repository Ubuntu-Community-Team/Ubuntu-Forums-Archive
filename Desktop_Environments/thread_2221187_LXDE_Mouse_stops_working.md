---
title: "LXDE: Mouse stops working"
date: 2014-05-01
forum: Desktop Environments
---

### Post by vrghost on 2014-05-01
So basically, been working away on this one really annoying issue, not in any way made worst that I am working on it over the phone as it is my father in law, I promise

So basically, what happens is that when he uses the laptop he gets to a point where the mouse just stops working, often he can still move the cursor, but it is stuck in input mode (or its an upper case I in the words of my mother in law).Keyboard works, and Alt+F1 changes to terminal, but I cant get the mouse back to working. Any ideas?

The install is about two weeks and I have updated the system, the issue was there all the time I think, there was a second issue about system crashing as well, but that one is sorted (I think)

/Ben

---

### Post by bapoumba on 2014-05-01
Not sure I can help you all through your issue, but what kind of mouse is it ? Plain usb or wireless ? If wireless, no battery issue ? Does the track pad work ? You say this is a laptop, so I assume there is one. Does it stop working on any application or on specific ones ? Please also give some details about the laptop. Thanks.

---

### Post by vrghost on 2014-05-01
Think it is a acer laptop (will get model number)
He is using the trackpad rather than a mouse. Seems to happen with all kind of applications, like chrome, the LX console and others. 

The mouse don't quite stop working, you can move the cursor, but you can't click anything, and whatever shape the pointer is when it happens will stay in.


/Ben

---

### Post by bapoumba on 2014-05-01
Please try```
 ibus exit
``` and see if it helps.

---

### Post by vrghost on 2014-05-01
I shut down ibus the applet. Seemed to make it run a bit better, so will try ibus exit.
Is there any way in lubuntu to stop ibus completely. Seems like a pretty useless application to me?

---

### Post by bapoumba on 2014-05-01
> **vrghost said:**
> I shut down ibus the applet. Seemed to make it run a bit better, so will try ibus exit.
Is there any way in lubuntu to stop ibus completely. Seems like a pretty useless application to me?

Some uninstall it. I keep on running the exit command when logging in for now, will probably make an autostart file at some point when I get tired of it. Bug report : [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

---

### Post by vrghost on 2014-05-01
They ran ibus exit
It still happens, so the machine SEEMS to be running perfectly, but you can't click anything on the screen, but you can move the mouse cursor as much as you like, and give keyboard commands...

---

### Post by bapoumba on 2014-05-01
So that may be a video driver issue, please give the computer specs. Others will help you :)

---

### Post by vrghost on 2014-05-07
Its an ASUS X58L
[COLOR=#333333][FONT=Segoe UI]Chipset: Mobile Intel® GL960 Express Chipset + ICH8M
Graphics card: [/FONT][/COLOR][COLOR=#333333][FONT=Segoe UI]Embedded Intel® GMA X3100 Gfx 

Full spec 
[/FONT][/COLOR]http://www.asus.com/Notebooks_Ultrabooks/X58L/specifications/

---

### Post by bapoumba on 2014-05-07
I wont be much able to help you with video, but just to make sure, have they tried another mouse, even borrowed from someone just to test ?

---

### Post by vrghost on 2014-05-07
No I haven't, because they live two hours drive away and don,t have a extra mouse around.
Is there a way to use the keyboard to simulate a mouse click?

---

### Post by bapoumba on 2014-05-07
> **vrghost said:**
> No I haven't, because they live two hours drive away and don,t have a extra mouse around.
Is there a way to use the keyboard to simulate a mouse click?
When in a window, usually you can move from one clickable item to the next with <tab>, then hit <enter>.

---

