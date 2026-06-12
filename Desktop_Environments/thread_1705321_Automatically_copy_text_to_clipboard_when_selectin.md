---
title: "Automatically copy text to clipboard when selecting text"
date: 2011-03-12
forum: Desktop Environments
---

### Post by fermulator on 2011-03-12
There are two clipboards in linux:
 1) the "clipboard" (CTRL+C / CTRL+V)
 2) the "select text" buffer (select text, middle mouse click)

Is there a way to merge these two?  I want it such that when I select text using the mouse, it automatically goes into the clipboard, and I can paste it using either Shift+Insert, Ctrl+V, or MiddleClick.  When I copy text w/ Ctrl+C, I can paste it using all 3 methods.

---

### Post by Krytarik on 2011-03-12
Wow, nice feature, you can use "Parcellite" for that, it's in the official repos.

Choose in its options, at the "Behavoir" tab, "Use Copy (Ctrl-C)" (default), "Use Primary (Selection)" and "Synchronize clipboards".

---

### Post by amont on 2011-04-01
Great, Krytarik, you have solved half of my problem. Let's see if you can help me with the other half :)

My mouse had lost the ability to copy and paste (I have no idea why). Now, with "Parcellite", I can copy, enlightening text with the left button, but can't still paste with the centre button (actually a wheel). So I must do it with the contextual menu. Any idea about what the problem can be? (Or how to workaround). 

Thanks in advance for any help.
Toni

---

### Post by Krytarik on 2011-04-01
Do you have any other buttons at your mouse you could assign to that?

Please check if the middle button and the button you could use as the alternative are getting recognized by X.

Run
```
xev
```in a terminal and press the concerning buttons. Also, please note the button numbers that may get displayed.

---

### Post by amont on 2011-04-02
Thank you, Krysarik, for your quick reply.

My mouse (Logitech) has two buttons and a central wheel that, if pressed, act as a third button. (And up to a couple of weeks worked perfectly).
   
When I run xev the screen appears so full that I barely can catch it. Pointing at the test windows, but out of the square, I get, for the buttons 1 and 3 the following response:

```
ButtonPress event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1719320, (44,133), root:(662,186),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1719502, (44,133), root:(662,186),
    state 0x100, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1720976, (44,133), root:(662,186),
    state 0x0, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1721142, (44,133), root:(662,186),
    state 0x400, button 3, same_screen YES


```

But if clicking into the square I get, regardless of the button pressed:

```
ButtonPress event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0xc00002, time 1142720, (36,26), root:(575,79),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1142720, (36,26), root:(575,79),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  17  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0xc00002, time 1142838, (36,26), root:(575,79),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 36, synthetic NO, window 0xc00001,
    root 0x111, subw 0x0, time 1142838, (36,26), root:(575,79),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0 
```  

When pressing the wheel (that act as a third button) I have no response at all, regardless if I click in or out of the test square.

Greetings

---

### Post by amont on 2011-04-02
Something strange happened that puzzled me. I tried with another mause, and it happen to work well. So I said Aha! its a device's fault. But then, testing again with the original mouse, it work fine also! So, I conclude that when my laptop recognized the second mouse, something misconfigured had been fixed. :confused: Now testing with "xev" I see de second button:

```
ButtonPress event, serial 36, synthetic NO, window 0x4000001,
    root 0x111, subw 0x0, time 1040078, (57,135), root:(60,188),
    state 0x0, button 2, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4000001,
    root 0x111, subw 0x0, time 1040286, (57,135), root:(60,188),
    state 0x200, button 2, same_screen YES
```

Thank-you very much for your time and guidance.

---

### Post by Krytarik on 2011-04-02
Glad that you figured it out! :)

---

