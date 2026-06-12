---
title: "How do I disable a key?"
date: 2006-10-08
forum: Desktop Environments
---

### Post by hermesrules on 2006-10-08
I am posting this as a continuation of this thread: [http://www.ubuntuforums.org/showthread.php?t=272998](http://www.ubuntuforums.org/showthread.php?t=272998).

I found what caused that problem, and it is very annoying, especially in Linux. Something has happened with the Print Screen key on my keyboard, so that now it appears as if pressed all the time. While in Windows, this only copies the screen into the clipboard, in KDE it starts KSnapshot. Since the key seems pressed all the time, I get multiple instances of KSnapshot popping up blocking the entire system from functioning. Even after I uninstalled KSnapshot, this behavior continues and makes Konqueror open up trying to locate KSnapshot.

I even went to disable the shortcuts that used the Printscreen key, but I may have forgotten a few, so now this continues.

I am thinking that the best way to solve this problem until the keyboard gets fixed (it's on a laptop, so a new keyboard is not an option), is to disable that key, so that Linux just ignores it.

I am currently using Kubuntu Edgy. How do I go about disabling a single key?

Thanks!

---

### Post by azxsdcvf on 2007-07-13
In "Control Center", open the "Regional & Accessibility" tree and select the "Input Actions" sub-option to show the Actions control panel.

In the "Actions" box, expand the "Preset Actions" tree and selec the "PrintScreen" sub-option. In the "General" tab look half way down and click the "Disable" checkbox. Click "Apply", and the Prt Scrn key will cease to annoy you.

---

### Post by hermesrules on 2007-10-30
Hi, and very belatedly thank you for your reply!!!

I have not been checking some of my posts recently, but since I found another thread today on a similar issue, and posted there as well, I came across this older one.

I see your explanation is specific to Gnome, and I have found more or less successful way to remedy the annoyance in KDE too. I am not quite certain how low-level is your solution. The thing, it seems, now happens with such intensity that it prevents my machine from proper booting and screws up the entire booting process so that I can't log in into Linux anymore. Occasionally there is a chance, but it's more like 1 in 10 attempts I can boot.

I am no longer sure this is only caused by the key alone, and suspect it is a more serious hardware issue, but Windows boots normally, and though the annoyance is present, it does not prevent me from doing my work. Only makes copy-paste operations nearly impossible...

---

### Post by bingoUV on 2007-10-30
It might be, that the key remains pressed i.e. it is not getting pressed repeatedly. Try turning off the autorepeat of the print screen key. 
```

xmodmap -pk | grep -i print

```

This will print something like 
```

    111         0xff61 (Print)  0xff15 (Sys_Req)

```

The first number (111) is what we need. Now run
```

xset -r 111

```

Try this out, and see whether it solves the problem. This way, you can keep your PrintScreen key. Only change is that if you keep it pressed, the associated action takes place only once.

---

### Post by hermesrules on 2007-10-30
Thanks, BingoUV! I tried as you suggested, and will now try a few scenarios to see if it would work. As far as I can tell (and by no means am I an expert), this is X-related, that is - it won't have an effect during boot. But it will have an effect on both KDE and Gnome. Am I right?

The key does not stay pressed all the time, so it is not being repeated all the time. It just "gets pressed" way too often, but sometimes could be as far as a few seconds apart. It's a good start though, and definitely something useful to learn.

---

### Post by bingoUV on 2007-10-30
Yes, it will have no effect during boot, or non graphical terminals. It will work both on KDE and Gnome. 

If you are sure you want to disable the key, just run the following. I am assuming the number you received from the previous command is 111.
```

xmodmap -e "keycode 111 = "

```

I did not want to deprive you of the pleasure of "PrintScreen"ing. But, it seems necessary.

---

### Post by hermesrules on 2007-10-30
> **bingoUV said:**
> I did not want to deprive you of the pleasure of "PrintScreen"ing. But, it seems necessary.

Oh, well! So be it! I assure you I feel in no way deprived of anything :). I do not take screenshots anyway, and can live without the PrintScr key.

Indeed, I got the 111, and followed your instructions. In Yast (QT-based, and run as root) the Yast Screenshot utility keeps coming up, blocking everthing else that Yast is doing. So I have to keep pressing Esc, which gives the keyboard some "air". Now I will try your PrintScr-less solution.

One more question though - how do I get it back (you know, in case I upgrade my keyboard, which I seriously doubt is the problem any more)?

Thanks!

---

### Post by bingoUV on 2007-10-30
cool. How to get it back depends on what you had before removing it :wink: . Actually just restarting the X server with good old ctrl-alt-backspace would restore your default key mappings. If you want to bring back without restarting, read on.

What does that key do besides PrintScreen? In my keyboard, it does something like Sys_Req(when shift-pressed). I do not know what it means. Before doing the xmodmap thing, just do 
```

xmodmap -pke | grep -i print

```

This shows what the keys are bound to. First one is when the key is pressed alone, second when pressed along with shift. For me it says
```

keycode 111 = Print Sys_Req

```

To restore, you just do 
```

xmodmap -e "keycode 111 = Print Sys_Req"

```

If it works, to make it permanent, put the command to remove the key in your ~/.xsession file. When you change your keyboard, or want the print screen to happen repeatedly, just remove the command from  ~/.xsession.

---

### Post by hermesrules on 2007-11-02
Well, it's now official - the laptop keyboard is at fault. I disconnected it and connected an external keyboard, and now no bad things happen.

Thanks for all the help!

---

