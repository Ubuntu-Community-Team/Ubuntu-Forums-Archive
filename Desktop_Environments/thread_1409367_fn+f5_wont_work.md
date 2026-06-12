---
title: "fn+f5 wont work"
date: 2010-02-17
forum: Desktop Environments
---

### Post by cespinal on 2010-02-17
Hello guise, 

I need some help in here. 

I have an hp dv9000 running the last version of kubuntu. Everything works ok. but I cant suspend the system using the fn+f5 shortcut. That option is simply not available in Kde's global keyboard shortcuts. However, it seems it can be added as a scheme. 

Looks like the command needs to be written down in a text file and the imported to the global shortcut options. 

Can anyone give me a hand on this? I sure It could help some folks suffering from this. 

Cheers!!!! Thanks as always!.

---

### Post by cespinal on 2010-02-18
bump

---

### Post by Hero of Time on 2010-02-18
Start Konsole and type 'xev'. A new window will popup. Make sure it has focus. Now press the keyboard shortcut you want to use. Some text should show up in Konsole. That text shows you the keycode that is send by that shortcut. If nothing shows up, then the button simply doesn't work. I have a Toshiba Tecra M10 laptop and it has two 'sleep' buttons, one for suspend to RAM and one for suspend to HDD. Only the suspend to RAM combination works, the suspend to HDD doesn't do anything.

---

