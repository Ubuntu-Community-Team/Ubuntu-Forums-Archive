---
title: "Gamepad/Joystick Macro Application"
date: 2008-07-14
forum: Gaming &amp; Leisure
---

### Post by Felson on 2008-07-14
I am looking for an application that will do macros for game pads. I know there is QJoypad, but that just lets you remap buttons to the keyboard or mouse. Granted, that is over half the work, but I would also like to be able to map joystick buttons to other joystick buttons, and or sequences of buttons. 
Eg. Press: A results: (A+B B B+C C)
With the ability to set hold times and repeat rates and pauses as well. I have seen a number of commercial apps for winblows that do this. Most of them are specific to the game pad in question. Thrust mapper is an example. Does anyone know if there is anything that does this for Linux? Anything being built to do it?

---

### Post by grossaffe on 2008-07-15
Can't say that i've seen anything past qjoypad.  shame, really.

---

### Post by Felson on 2010-11-13
Been almost 2 years since I posted this. Anyone know of any new apps that can do this?

---

### Post by Felson on 2010-11-15
bump

---

### Post by Alan502 on 2011-08-23
I have created an application that does this, you can find it at: [http://code.google.com/p/java-joystick-to-key/](http://code.google.com/p/java-joystick-to-key/)

---

### Post by Felson on 2011-08-24
Sweet! 

Can't wait!
I tried running the current version for download, and I got "java.lang.ArrayIndexOutOfBoundsException: 32" I will message you the rest of the error.

---

### Post by FrostyC on 2011-11-02
> **Alan502 said:**
> I have created an application that does this, you can find it at: [http://code.google.com/p/java-joystick-to-key/](http://code.google.com/p/java-joystick-to-key/)

This thing's GUI is wonderful. Much better than QJoystick's, but it doesn't support mouse input or mouse buttons. No rapid fire, and I actually can't get it to work, because every time I hit "start mapping" (I'm guessing this is what would activate the keys you set up?), it crashes complaining that it couldn't create a tray icon.  Also, I was not able to insert a key-combo for 1 button (well you kind of can, you have to set a button to a key & make it switch profiles, adding your second key to the other profile & switching back upon release. Kind of hacky, but I think it would work if the switching works correctly & is quick enough). Also it seems to be really sensitive to my analogs, and the "deadzone" control does nothing as far as I can see.

Still, the program is extremely nice and DEFINITELY a step in the right direction. The GUI is much more intuitive than any program like this for Linux. It lights up showing which button is which & clicking on them lets you set the key. Can't get much simpler than that...

It could easily be expanded upon to become the XPadder of the Linux platform. And since it's Java, I can take my profiles over to windows partition with ease. I'd really love to see this get some more attention, but I can't program in Java...

---

