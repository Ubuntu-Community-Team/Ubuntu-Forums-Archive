---
title: "im a noob, so i need help BAD :("
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-09
okay, i cant figure out anything, i just installed ubuntu <newest version> and this is the very first time ive been messed with it, im use to xp, so like i need help with a few things...
first off  i installed emerald, but i didnt uninstall synaptic.... and now every time i try to it says "Cannot remove 'synaptic'

One or more applications depend on synaptic. To remove synaptic and the dependent applications, use the Synaptic package manager

.... and like for some reason it wont alow me to apply my special effect, i installed xserver-xgl" or something like that and it told me i could after i restarted my, computer... i did and it still wont alow me.... 
    
is there a place i can go to get more themes and how do i install them, ....

 i know im new at this but can someone please give me a-z instructions, i know i wont be able to get it all at once but i need help...

---

### Post by Scarath on 2008-03-09
1. Do not try to remove synaptic!!!!!!!!!!!!

2. If you want a fancy desktop use compiz

3. More themes [here]("http://www.gnome-look.org/")

4. Google for instructions

5. Dont fear the Ubuntu, its scary and often very annoying to start with but totally worth it in the end :D

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-09
okay i still dont underrstand why it wont let me apply the desktop effect,  im so confused...><

---

### Post by danielcc on 2008-03-09
bring up a terminal and type compiz --replace and post the output... there could be a little problem causing it to not want to load

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-09
okay im lost, i totaly dont unser stand what to type...

---

### Post by pbpersson on 2008-03-09
You get into a terminal session or a konsole session and type compiz --replace

A console or terminal session in the Windows XP world would be called the Command Prompt or DOS prompt

It is a text-only window

---

### Post by Afkpuz on 2008-03-09
Ok, first of all, you need to install your video drivers.

At your menus on the top left of your screen, click

System=>Administration=>Restricted Drivers Manager
Type in your password when it asks for it

Check the box for your graphics driver to install.
Once thats done, restart your computer.  Then, try to enable desktop effects.  

You said you installed xgl-sever.  This is only needed if you have an ATI graphics card.  If you have an Nvidia graphics card, you don't need it.  

I also suggest that you install the settings manager for compiz so you can actually tweak the desktop effects to your liking.  

First, open up a terminal.  Thats in Applications=>Accessories=>Terminal

Then, paste this into the terminal.  Please note: to paste something into a terminal, you have to press Ctrl+Shift+v.  This only applies to the terminal.  Everywhere else, like in office docs, it's the normal ctrl+v to paste.  Anyway, paste this into the terminal.

```
sudo apt-get install compizconfig-settings-manager 
```

See if that gets your desktop effects working.


Oh and by the way, you should never remove synaptic.  Why did you think you needed to remove it?

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-09
i have ati. and i already install the latest update of compiz < a buddy helped me yesterday> 
i after i instaled  xserver-xgl it told me that after i restart my computer that the  the desktop effect will work, but it didnt 


 i read some where that i should uninstall synaptic and instal emerald..... but i dont know i mean i still dont even know the command to the terminal.....

---

### Post by Afkpuz on 2008-03-09
Ok, but have you installed your video driver like I described in my last post?

---

