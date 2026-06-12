---
title: "How do I find and install display drivers?"
date: 2009-02-19
forum: General Help
---

### Post by mdb0790 on 2009-02-19
I'm very new to Ubuntu.  I just installed it today, but had to do so in safe graphics mode because when I did it normally, I would get to the install screen and it would go white and stay that way.

When I go into Ubuntu's menu to change the resolution, I can't because there is only one resolution. I need to change this resolution because I can't see the bottom part of my screen. It hasn't "detected" my monitor. I'm guessing I need to install a display driver? I don't have a graphics card so it is whatever is on the motherboard, which is an Intel Pentium 4 2.0Ghz. 

So if anyone can help me, it would be greatly appreciated.

---

### Post by oldos2er on 2009-02-19
What video card do you have?

---

### Post by anlag on 2009-02-19
You might want to check under System -> Administration -> Hardware Drivers if any options show up there. If they do, mark, activate and follow instructions on-screen.

---

### Post by ajgreeny on 2009-02-19
Try using System > Administration > Hardware Drivers, which should have picked up by now which card you are running, and may offer drivers for it.  You must have a graphics card of some sort though it may be integral and on the motherboard.  Have a look in your computers instruction manual for more details, or if you are booted to ubuntu, either open a terminal or use Ctrl+Alt+F1 to get to a console and then use the command ```
sudo lshw
``` which will show you which video card you have.

---

### Post by mdb0790 on 2009-02-19
I googled my computer model, and found the correct motherboard (I believe) and this is what is says for video:

Integrated AGP Graphics Video VGA Connector plus AGP 4x/2x AGP Slot

I have tried installing numerous programs to try to find out what drivers I need (i.e. Driver Detective) but every time I try to I get an error message:

"An error occured while loading the archive.
(null)
Command Line Output:
End-of-central-directory signature now found. (Then it goes on to say how the program is either not a zip file or constitutes as a multipart archive, ect.ect.)"

I'd copy and paste but I'm using a different computer to type this. Any tips? If you need more information, I'll do my best to get it, I'm still new to this.

---

### Post by oldos2er on 2009-02-19
Can you please post the output of
```
sudo lshw
```
typed into a terminal?

---

