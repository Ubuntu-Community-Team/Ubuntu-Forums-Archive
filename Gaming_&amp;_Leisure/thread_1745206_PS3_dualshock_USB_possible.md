---
title: "PS3 dualshock USB possible?"
date: 2011-04-30
forum: Gaming &amp; Leisure
---

### Post by saioke on 2011-04-30
I've searched and searched but can't find any information available that actually works for my condition. I've found plenty of tutorials for getting a PS3 controller working via bluetooth, but I have no bluetooth adapter and don't really want to spend the cash for one just to get my controller working again. This makes emulation difficult while playing complex games that are hard to control using the keyboard alone. Has anyone found a way to get the controller working connected by USB?

---

### Post by doorknob60 on 2011-05-01
Mine works fine just plugged in with the USB cable, don't have to do anything special, just plug it in and set up your game/emulator to use it.

---

### Post by saioke on 2011-05-01
I tried that, however when I try to configure buttons it don't register right. Every button I press happens to go to the same input for some reason.

---

### Post by doorknob60 on 2011-05-01
Which program are you trying to use it with? It's worked in everything I've tried (I belive I've used snes9x, mupen64plus, and a few other emulators and all worked fine). I know that the PS3 controllers have analog buttons, which a few games have issues with, but it's fine for most things.

---

### Post by disturbedite on 2011-05-01
> **saioke said:**
> I tried that, however when I try to configure buttons it don't register right. Every button I press happens to go to the same input for some reason.
this is the problem: [http://forums.pcsx2.net/Thread-ps3-controller-setup](http://forums.pcsx2.net/Thread-ps3-controller-setup)
it has nothing to do with the controller being used via USB or wirelessly with bluetooth.

---

### Post by saioke on 2011-05-01
> **doorknob60 said:**
> Which program are you trying to use it with? It's worked in everything I've tried (I belive I've used snes9x, mupen64plus, and a few other emulators and all worked fine). I know that the PS3 controllers have analog buttons, which a few games have issues with, but it's fine for most things.

I've tried both Zsnes and Mupen64 and both had the same thing. No matter what button I press, it registers as the same button.

This is no analog manner. This is full button configuration.

---

### Post by saioke on 2011-05-04
Bump.

Doing further research turns no information on how to get it working properly.

Edit: Little extra information. When trying to configure the controls, it chooses a button known as J19 automatically. This button does register, so I know the driver works to some extent, however I just can't configure the buttons or anything. I've tried different USB cords and different PS3 controllers and they all do the same, so this is a system issue.

---

### Post by mister_playboy on 2011-05-04
As the link disturbedite pointed to mentions, this problem lies with too-sensitive analog stick input detection.  If you have a well-worn controller like I do, your analog sticks do not center perfectly.  The PS2/3 tolerates this problem, but the button assignment program does not.

I have not found anyway to turn off the analog functionality of a PS2 or PS3 controller when using it with Linux.

If you are playing older games that don't need analog input, my recommendation is to use a non-analog PS1 controller or one of the PS look-a-likes made by Logitech, etc.  These cost about $10 and work just fine.

---

### Post by saioke on 2011-05-05
> **mister_playboy said:**
> As the link disturbedite pointed to mentions, this problem lies with too-sensitive analog stick input detection.  If you have a well-worn controller like I do, your analog sticks do not center perfectly.  The PS2/3 tolerates this problem, but the button assignment program does not.

I have not found anyway to turn off the analog functionality of a PS2 or PS3 controller when using it with Linux.

If you are playing older games that don't need analog input, my recommendation is to use a non-analog PS1 controller or one of the PS look-a-likes made by Logitech, etc.  These cost about $10 and work just fine.

I don't believe that problem corresponds to what I'm dealing with. For one, I've had the controller working on a windows machine prier to trying to get it to work in Ubuntu and it worked fine. Each button configuration would show up as "J14" or something similar while the analog sticks would show up as an entirely different set such as "something_Y". I can't remember exactly what it was, but I know it wasn't in the form of "J19". Also, the other controller I've tried has only been used once since I've bought it so I know the analog sticks on it are as straight as an arrow.

Maybe there's a way to remove the current controller driver and reinstall?

---

### Post by disturbedite on 2011-05-05
i experienced the same problem. it IS what i described. just because it works fine some times doesn't mean it doesn't work fine other times. the analog stick is a very touchy thing.

and the driver situation on linux is FAR different than on windows, so uninstalling and reinstalling the driver wouldn't do any good, even if you could.

---

### Post by saioke on 2011-05-06
> **disturbedite said:**
> i experienced the same problem. it IS what i described. just because it works fine some times doesn't mean it doesn't work fine other times. the analog stick is a very touchy thing.

and the driver situation on linux is FAR different than on windows, so uninstalling and reinstalling the driver wouldn't do any good, even if you could.

After doing some further research and testing on a different emulator (Gens-GS), I can confirm the controller works fine. However, when trying to set the controls for other emulators, it does not. This indicates that the analog sticks are indeed the problem. Is there any way to lower the sensitivity of the analog sticks at least enough to set proper controls? Or should I just get another controller?

---

### Post by disturbedite on 2011-05-06
no, i don't think there is a way to do that. i'd just try it with a new controller unless you're willing to do what i did: find out what the buttons/axes are read as by the emulator you're using and program them manually in the config file.

---

