---
title: "Compiz in Lubuntu?"
date: 2010-09-18
forum: Desktop Environments
---

### Post by BigBig5 on 2010-09-18
How can you get Compiz to work in Lubuntu. I tryed to change the window manager, but can't. Is there a way?

---

### Post by BigBig5 on 2010-09-18
I have change the windows manager to Compiz, but Compiz effcts don't work.

---

### Post by soldier1st on 2010-09-19
compiz ib Lubuntu is not easy to implement as Lubuntu is meant to be a lightweight Distro with lightweight applications and sadly compiz is not lightweight so if you want compiz then you will need to run Either Ubuntu or Kubuntu and possibly Xubuntu though i doubt Xubuntu could easily do compiz. to me Lubuntu feels too restrictive in what you can do.

---

### Post by meskes on 2010-09-21
While soldier1st is correct about Compiz not really being able to work with Lubuntu, he's incorrect about it not being easily enabled in Xubuntu. XFCE supports Compiz quite nicely and there is even a howto which walks you through installing and configuring it on the forums.

Matt

---

### Post by Tibuda on 2010-09-21
I see no reason why it would not work on Lubuntu. You can even use Compiz as a standalone window manager with no DE, like Openbox. EDIT: [this link](http://blog.lxde.org/?p=30) have some screenshots of Compiz in LXDE.

First, do you have your video drivers installed? Check the hardware driver manager. (I don't know how to use it on Lubuntu, but I guess it is similar)

Second, try running the following command from a terminal. It will replace whatever window manager is running for Compiz.
```
compiz --replace ccp
```

EDIT: Third, do you have another window decorator (Emerald or Metacity) installed?

---

### Post by nothingspecial on 2010-09-22
I run compiz in lubuntu and it works very nicely thankyou very much.

You need to add it to your start up applications

```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```

add a line to the bottom of that file

```
@compiz --replace
```

Press Ctrl-O then Enter to save then Ctrl-X to close nano.

It should start at login

---

### Post by 3Miro on 2010-09-22
Compiz + LXDE or XFCE is a contradiction of principles, since one aims at light- weight and snappiness and the other at wight and ostentation. This is like getting your Ford Mustang to pull a boat, when a F150 Truck will do a much better job.

That said, all you have to do to get this is to install compiz from Ubuntu Software Center and then run
```
 compiz --replace 
```

What I usually do under Gnome is that I install "fusion-icon" and then switch between Compiz, Openbox and Metacity depending on what I am doing. Openbox is best for work, Metacity is best to save energy, when I run on battery power and Compiz is best to showoff.

---

### Post by nothingspecial on 2010-09-22
> **3Miro said:**
> Compiz + LXDE or XFCE is a contradiction of principles, since one aims at light- weight and snappiness and the other at wight and ostentation. 

This is linux

If you want to run compiz and lxde then you are free to do so.

Like me.

And I do.

The principle is that you can use the tools to do whatever you want.

I see no contradiction. :)

---

### Post by 3Miro on 2010-09-22
> **nothingspecial said:**
> This is linux

If you want to run compiz and lxde then you are free to do so.


Of course. I was only making the observation that the biggest strength and reason to use LXDE and XFCE is the speed and Compiz will take a toll form that. If you don't mind, then go ahead and use whatever you want to use.

---

### Post by qamelian on 2010-09-22
> **3Miro said:**
> Of course. I was only making the observation that the biggest strength and reason to use LXDE and XFCE is the speed and Compiz will take a toll form that. If you don't mind, then go ahead and use whatever you want to use.
Actually, both of those desktops feel much snappier and more responsive on my laptop with compiz turned on. Everything runs smoother and renders observably faster on the screen. Personally, I would never run either without compiz just for that reason. It's actually why I prefer compiz over Metacity's own compositing manager...compiz just performs better.

---

### Post by 3Miro on 2010-09-22
> **qamelian said:**
> Actually, both of those desktops feel much snappier and more responsive on my laptop with compiz turned on. Everything runs smoother and renders observably faster on the screen. Personally, I would never run either without compiz just for that reason. It's actually why I prefer compiz over Metacity's own compositing manager...compiz just performs better.

This is very interesting. On my Laptop with Intel video and Pentium Dual Core, both XFCE + xfwm and Gnome + Openbox work way faster than compiz (compiz works, it is just slowing the system). The interesting part is that on my a quad core AMD + Nvidia desktop, compiz is again slower. 

So I am curious, what are the specs of your machine.

---

### Post by qamelian on 2010-09-22
> **3Miro said:**
> This is very interesting. On my Laptop with Intel video and Pentium Dual Core, both XFCE + xfwm and Gnome + Openbox work way faster than compiz (compiz works, it is just slowing the system). The interesting part is that on my a quad core AMD + Nvidia desktop, compiz is again slower. 

So I am curious, what are the specs of your machine.
It's a 5-6 year old Compaq Presario R3000T with a 2.4 Ghz P4 and an ATI Mobile Radeon 9000 IGP running the open source ATI driver. With compiz active, everything draws to the screen smoothly, windows can be moved with no visible jerkiness, etc. Using Metacity compositing (or no compositing at all) results in tearing when moving windows and the redraw speed of Windows is noticeably slower. The same applies to my desktop running an AMD X3 Phenom and an ATI Radeon 2400HD, but the difference isn't as noticeable as it is on the older laptop.

---

### Post by 3Miro on 2010-09-22
> **qamelian said:**
> It's a 5-6 year old Compaq Presario R3000T with a 2.4 Ghz P4 and an ATI Mobile Radeon 9000 IGP running the open source ATI driver. With compiz active, everything draws to the screen smoothly, windows can be moved with no visible jerkiness, etc. Using Metacity compositing (or no compositing at all) results in tearing when moving windows and the redraw speed of Windows is noticeably slower. The same applies to my desktop running an AMD X3 Phenom and an ATI Radeon 2400HD, but the difference isn't as noticeable as it is on the older laptop.

Big variety on the hardware, so this is totally not what I was expecting based upon my experience. Well, if compiz works better for you, then use it by all means.

---

### Post by nothingspecial on 2010-09-22
Compiz runs well on my lubuntu

Under 2% of PCU and RAM

even when using a couple of fancy effects.

Gnome-Do and Chromium are the culprits......

---

### Post by Gaygerbil on 2010-10-12
I can't get Compiz to work under Lubuntu I installed it through Synaptic Package Manager that along with Emerald, I then try the terminal command:

```
compiz --replace
```

My screen'll flash and then all of a sudden the window decoraters are all gone and I can't move any windows or anything and I'm stuck at the terminal window where I just have to give it the reboot or logout command to start over. :\ What am I doing wrong?

---

### Post by travlemon on 2011-03-08
> **Gaygerbil said:**
> I can't get Compiz to work under Lubuntu I installed it through Synaptic Package Manager that along with Emerald, I then try the terminal command:

```
compiz --replace
```My screen'll flash and then all of a sudden the window decoraters are all gone and I can't move any windows or anything and I'm stuck at the terminal window where I just have to give it the reboot or logout command to start over. :\ What am I doing wrong?


I'm having this exact issue as well.  The effects worked fine on my previous Xubuntu installation on the same machine, and even in Gnome.  I tried changing the window decorator to GTK, but no luck. 

Are there anymore packages I could install to make it stable?

---

### Post by sgtslwilson on 2012-04-13
> **nothingspecial said:**
> I run compiz in lubuntu and it works very nicely thankyou very much.

You need to add it to your start up applications

```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```

add a line to the bottom of that file

```
@compiz --replace
```

Press Ctrl-O then Enter to save then Ctrl-X to close nano.

It should start at login

Thank you very much! That worked! The only thing I did differently was to replace the word nano with leafpad (which serves me just fine.)

Anyway, thank you!

---

