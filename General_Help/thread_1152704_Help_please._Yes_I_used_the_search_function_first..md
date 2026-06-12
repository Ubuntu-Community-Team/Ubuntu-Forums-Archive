---
title: "Help please. Yes I used the search function first."
date: 2009-05-08
forum: General Help
---

### Post by LifeIsFlimsy on 2009-05-08
So I am trying to install Windows XP from a CD onto my computer currently running Ubuntu 8.04. I cannot figure out how to get into the BIOS to make it boot from the DVD Drive upon Startup. I have tried hitting every key on each different boot screen, but to no avail. It even says "Press any key to boot from blah blah" but nothing happens when I do that.

Basically I am trying to get rid of Ubuntu and put Windows XP back on. Sorry to break it to ya, and I hope you still help me regardless, but the framerates are much better in games when using Windows. At least on this computer. Thank you in advance for any help you have given me.

---

### Post by MysticalRiotCandy on 2009-05-08
I would say, "reflash your BIOS firmware", except most flashers are in Windows.  Eh.

Can you get into the BIOS settings screen at all?  Perhaps it's not recognizing your keyboard at BIOS level, and the OS is interpreting it.

---

### Post by Peter09 on 2009-05-08
What is the computer - model number, manufacturer. Do you know what BIOS you have.

Are you saying that you can get into the BIOS but cannot find how to change the boot order to CDROM first, or can you not get into the BIOS?

---

### Post by LifeIsFlimsy on 2009-05-08
What I am saying is that I cannot even get into BIOS. Maybe I am doing the wrong command (key smashing wise) to get to it? Is it ctrl+anything else or something of the sort?

This computer used to have XP on it but apparently it wasn't genuine (how the hell did I know that at the time) so I installed Ubuntu and have been using it ever since. I now have an XP CD and would like to put it back on there, which would require booting from the CD drive (I would guess a DVD drive would work as well since XP is on a DVD). The problem is that when I boot, I see Intel for a fast second, then Pentium 4, then a screen that looks like the beginning of The Matrix, with a little flashing underscore for about 30 seconds, then it says something like "To blah blah press any key..." at which point I have about 3 seconds before it starts to show text about GRUB and all that jazz and boots to Ubuntu.


For that other reply, the computer is a Sony Vaio and no I do not have a clue what bios I have. I did a command in terminal to check what BIOS **version** I have and it came back with 2003, if that helps at all.

Thanks for the swift replies folks.

---

### Post by cdwillis on 2009-05-08
Did you try pressing F2 when you booted? A quick google search could help you figure out what key it is to bring up the bios menu.

---

### Post by pastalavista on 2009-05-08
On the very first splash screen when you boot, the one with the PC's brand name or motherbord manufacturer, there is usally some text saying press such and such key to enter "Setup". That's the BIOS. It's firmware embedded in a chip so the mother board knows what to do with all its components.

---

### Post by Peter09 on 2009-05-08
Try one of these soon after it starts to Boot.

F2
F4
Del
Esc

---

### Post by dcstar on 2009-05-08
> **LifeIsFlimsy said:**
> So I am trying to install Windows XP from a CD onto my computer currently running Ubuntu 8.04. I cannot figure out how to get into the BIOS to make it boot from the DVD Drive upon Startup. I have tried hitting every key on each different boot screen, but to no avail. It even says "Press any key to boot from blah blah" but nothing happens when I do that.
......

Some old PCs are set by default to only respond to PS2 keyboards until you go into the BIOS and enable the USB keyboard option.

If you have one of these and are using a USB keyboard, use/borrow a PS2 keyboard and see if that works and allows you to go into the BIOS.

A well, IIRC the Windows install CD waits 30 seconds for you to press a CD to boot off it before it goes to the Hard Disk, so when you get the "blank screen" for that 30 second period then hit a key.

---

### Post by lisati on 2009-05-08
> **Peter09 said:**
> Try one of these soon after it starts to Boot.

F2
F4
Del
Esc

On my laptops it's F12 while the "Toshiba" splashscreen is being displayed that lets me choose which device to boot from.

---

### Post by LifeIsFlimsy on 2009-05-08
Thanks for the help so far folks, but still no luck. The keyboard is already PS2, and no matter what screen I hit the keys on, nothing works. The keyboard works fine when I get to the login screen and from then on, but before that I get no response. Even on the screen saying "To boot from CD, press any key." It only gives me about 3 seconds to hit a key at that point before it boots up, so I try to hit what was recommended above during that time.



Any other thoughts?

---

### Post by bacardiandwatermelon on 2009-05-08
Confused... If is says "To boot from CD, press any key" then it must already be in the correct boot order. Doesn't it boot to cd when you press a key? Maybe try a different keyboard? If you are wanting to get into the bios you need to press the keys before this stage when it is turning on, there is a chance that your monitor isn't turning on in time and you are missing this part...

---

### Post by pastalavista on 2009-05-08
What is the model number of your Sony? If you can't Google it to find the BIOS key, allow me. Also, does the keyboard have lights on it? Do they come on when the computer does or does it take a while?

---

### Post by LifeIsFlimsy on 2009-05-08
Sony Vaio PCV-2253.

It appears that it might be the keyboard, but I don't understand why that is, considering it's not a USB keyboard, and it has worked fine (and still continues to do so after boot).

---

### Post by ACupOfCoffee on 2009-05-08
When it says press any key just do it. It doesn't matter which key or even how many. You say you've tried all the suggested keys for getting into the BIOS at this screen. If I understood that right then you're doing it on the wrong screen. The screen you want is before the one you're trying.

---

### Post by pastalavista on 2009-05-08
OK, I did some looking and for later models, the usual key to press is F2. But on some older models you had to press two keys in sequence kinda quickly. At the Sony splash screen, press F3 and then immediately press F1. If your keyboard works, that ought to do it. If not, sorry. Sometimes things break and can't be fixed... only replaced

---

### Post by bacardiandwatermelon on 2009-05-08
For my Gf's Sony PCG-5JBP you have to press F2

---

### Post by Tipped OuT on 2009-05-08
Okay dude, this what you do. Turn off your computer completely, then press the power button to start it up, and immediately start tapping one of the following keys:

F2
F10
F12
ESC

If F2 (for example) doesn't get you into the bios, then repeat the process over again, but this time try F10, and so on and so on.

If you get into the bios, set the settings to default and make sure the boot order, is set for the CD/DVD Drive to boot first, and good luck.

---

### Post by Falcon1002 on 2009-05-08
Just wondering. What type of drive do you have CD or DVD?
And does the drive make noise after you push the keyboard key at the "To boot from CD, press any key." screen? Thanks.

---

### Post by cariboo on 2009-05-08
The does cd/dvd show up in Ubuntu when you put it into the drive?

---

### Post by Tipped OuT on 2009-05-08
> **cariboo907 said:**
> The does cd/dvd show up in Ubuntu when you put it into the drive?

I think his CD/DVD drive is fine, otherwise it wouldn't ask to boot from it when he has the Vista installation disk in. Maybe I'm wrong though.

---

### Post by Falcon1002 on 2009-05-08
I was kinda thinking it might be a cd drive trying to boot a DVD. :D
Thats why I asked.

---

### Post by Tipped OuT on 2009-05-08
Well test it out, try putting a DVD movie in it and see if it'll play in Ubuntu. :popcorn:

---

