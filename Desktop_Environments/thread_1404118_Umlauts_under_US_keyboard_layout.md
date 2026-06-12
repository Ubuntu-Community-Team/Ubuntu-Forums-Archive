---
title: "Umlauts under US keyboard layout"
date: 2010-02-11
forum: Desktop Environments
---

### Post by efAston on 2010-02-11
Hi,

I'm running kubuntu 9.10 with the US Dvorak-international keyboard layout. I want to be able to enter the ä and ö characters as I also type in Finnish. I've tried holding Alt-Gr and pressing every key on the keyboard, and I get 

23&#8364;5&#8311;8[êëüfgçrl/=\àôéûîfdtnß-âöèùïbmwvz´´à´àààà´à"A'"""""""""""A"A''

, which gives me an ö, but by pressing the q key with Alt-Gr, so I don't understand the logic behind it and still can't produce an ä. Does anyone know what's happening the US international keyboards and how I can produce an ä?

Cheers,
Aston

---

### Post by semperfizh on 2010-02-11
> **efAston said:**
> Hi,

I'm running kubuntu 9.10 with the US Dvorak-international keyboard layout. I want to be able to enter the ä and ö characters as I also type in Finnish. I've tried holding Alt-Gr and pressing every key on the keyboard, and I get 

23€5&#8311;8[êëüfgçrl/=\àôéûîfdtnß-âöèùïbmwvz´´à´àààà´à"A'"""""""""""A"A''

, which gives me an ö, but by pressing the q key with Alt-Gr, so I don't understand the logic behind it and still can't produce an ä. Does anyone know what's happening the US international keyboards and how I can produce an ä?

Cheers,
Aston

I would suggest mapping a key to switch between finish keyboard in your case
and US keyboard

Cheers

---

### Post by Zorael on 2010-02-11
You can also use xmodmap to rebind what characters a given key (for your keyboard layout) will print. So with a simple script you could for instance rebind AltGr+a to output **ä**. Running '**xmodmap -pke**' in a terminal will list the current mappings. To resolve what keycode a physical key represents, you can start **xev** (in a terminal), press the key and then look at the output, alternatively just find it in the xmodmap wall of text.

Concrete example;
```
$ xmodmap -pke | grep "a A"
keycode  38 = a A a A ordfeminine masculine
```
So it seems the key returning **a** has the keycode **38** on my layout (Swedish). The key symbols **a, A, ordfeminine** and **masculine** represent the characters it will return when pressed normally, with Shift, with Alt, with Shift+Alt, with AltGr and with Shift+AltGr respectively. It's possible to rebind what modifiers to use, but that's the default setup.

It's probably listed in some file someplace, but by merely looking at the output of '**xmodmap -pke**' you get an inkling of what characters are available. **adiaeresis** represents ä, and **Adiaeresis** Ä.

So, to remap AltGr+a to be ä (and Shift+AltGr+a as Ä);
```
$ xmodmap -e "keycode 38 = a A a A adiaeresis Adiaeresis"
```
It used to be that you could merely save such lines in the file **~/.Xmodmap** and it would be executed upon login, but at some point it seems this functionality was removed. So you need to create a script that executes it.
```
#!/bin/bash

xmodmap -e "keycode 38 = a A a A adiaeresis Adiaeresis"
```
Save it in **~/.kde/Autostart** to have it be run automatically. Be sure to make it executable.

------------------------------------------

If you really want to adhere to the old **~/.Xmodmap** behavior (for whatever reason), you can save the keycode line (sans '**xmodmap -e**' and the quotes) in **~/.Xmodmap**, and then have your script restore the earlier behavior by manually telling xmodmap to read the file.
```
#!/bin/bash

if [ -r ~/.Xmodmap ]; then
        xmodmap ~/.Xmodmap
fi
```

---

### Post by efAston on 2010-02-11
Thanks Zorael. It seems funny that I have to modify the keyboard every time I boot, even if automatically, you'd think we'd be able to modify the keyboard layout itself. Even go back to the source with the modifications - to see if we can improve on the default. Maybe when I'm not such a newbie I'll think more about that.

---

### Post by efAston on 2010-02-12
Actually, it worked before I rebooted, but now that I've restarted it's back to the way it was before. I saved a file called "keyboard.sh" to /home/aston/.kde/Autostart with the entries you described.

---

### Post by Zorael on 2010-02-12
Is it set to be executable, or does Kate pop up and open it when you log in?

---

### Post by efAston on 2010-02-12
Kate doesn't pop up when I log in, how do I set it to executable?

---

### Post by efAston on 2010-02-13
Actually Wine does come up when I boot, and Wine is associated with .sh. How do I get it to execute?

---

### Post by Zorael on 2010-02-14
Right-click it in Dolphin, go to the Permissions tab and check Is executable.

Alternatively, in a terminal;
```
$ chmod +x ~/.kde/Autostart/keyboard.sh
```

---

### Post by efAston on 2010-02-16
Heh, I found the same just before reading this. Thanks heaps!

---

