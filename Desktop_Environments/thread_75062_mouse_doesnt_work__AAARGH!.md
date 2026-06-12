---
title: "mouse doesnt work  AAARGH!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by greengrass on 2005-10-13
I have installed ubuntu from the installation CD  using a standard install on a 10G  harddrive.  I have a CLIX ES mouse with an old style connector.  How do I get linux to recognize it?  I have tried moving around the desktop with the keyboard and can get to the menu to configure the mouse, screen resolution, ect., but I havent been able to change any of the appropriate radio buttons with the keyboard.  Is there a way to get the keyboard to select different radio buttons?

---

### Post by RawMustard on 2005-10-13
Did you try and press the spacebar?

---

### Post by greengrass on 2005-10-13
no

---

### Post by taavi on 2005-10-13
Try moving around using Tab and Shift-Tab?

---

### Post by greengrass on 2005-10-13
I tried using the tab key to get to different areas in the menu but it skips over the radio buttons.   But it DOES work when I'm at the logout window.  Also are there drivers that linux needs for this mouse?  Also there is no sound either.

---

### Post by KingBahamut on 2005-10-13
The Old style connector? you mean a serial 9 pin?

---

### Post by greengrass on 2005-10-13
yes, sir

---

### Post by KingBahamut on 2005-10-13
Your system is probably trying to use ps2 instead of serial or whatever. 

The first thing to do is to make sure the software can find the mouse. Work out which serial port your mouse is connected to - usually this will be /dev/ttyS0 (COM1 under DOS) or /dev/ttyS1 (COM2). (ttyS0 is usually the 9 pin socket, ttyS1 the 25 pin socket, but of course there is no hard and fast rule about these things.) There are also an equivalent number of /dev/cua devices, which are almost the same as the ttyS ones, but their use is now discouraged. For convenience make a new link /dev/mouse pointing at this port. For instance, for ttyS0:

    ln -s /dev/ttyS0 /dev/mouse

---

### Post by greengrass on 2005-10-13
I am extremely green at this.   So you type in  ln -s/dev/ttySO/dev/mouse at the $ and then reboot?  

How do you get to the $ prompt from the desktop?

---

### Post by KingBahamut on 2005-10-13
You need to determine which device it is first.

---

### Post by jalanbuntu on 2005-10-13
[QUOTE=greengrass]I am extremely green at this.   So you type in  ln -s/dev/ttySO/dev/mouse at the $ and then reboot?  

How do you get to the $ prompt from the desktop?[/QUOTE]

Do you mean terminal?????? :-k Just open it at 
Menu -> Applications -> Accesories -> Terminal, or you can try to move to other tty by pressing CTRL + ALT + F1, CTRL +ALT + F2, .......

---

### Post by Mustard on 2005-10-13
and type this rather than the mess you have in your last post. :)

```
ln -s /dev/ttyS0 /dev/mouse
```

..assuming it is ttyS0

---

### Post by greengrass on 2005-10-13
how do you do that?

---

### Post by peteyp666 on 2005-10-13
try pluggin a ps/2 mouse in

---

### Post by prsnbx on 2005-10-17
I am also experiencing this problem. I have my mouse connected to COM2 and have tried the suggested 'ln' option. Which was cribbed from [here]("http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html#s3")

I have also tried the procedure recommended [here]("http://ubuntuforums.org/archive/index.php/t-23926.html")

amongst other things. Still no joy :(

Can anyone help???

thanks prsnbx.

---

