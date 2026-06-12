---
title: "Can't load the game Civ 1 with Firefox/Mozilla"
date: 2009-04-20
forum: General Help
---

### Post by darkenergy4 on 2009-04-20
So I need some assistance on this issue. I have the Civ 1 disk and I see  Civ - File Browser   What's next?

---

### Post by codeseer on 2009-04-20
What? Where?

---

### Post by darkenergy4 on 2009-04-21
I can't load the game on the computer. I am stuck at the point of seeing on the files on the screen.

---

### Post by codeseer on 2009-04-21
It's a Windows game is it not? Run the installation with Wine.

Alternatively: [http://freeciv.wikia.com/wiki/Main_Page]("http://freeciv.wikia.com/wiki/Main_Page")

---

### Post by darkenergy4 on 2009-04-21
It is a Windows game. I'm not much interested in FreeCiv.

---

### Post by codeseer on 2009-04-21
> **darkenergy4 said:**
> It is a Windows game. I'm not much interested in FreeCiv.

So, yeah.. just open a terminal and type something like this:

```
wine /media/cdrom0/Setup.exe
```

---

### Post by darkenergy4 on 2009-04-21
Punched in the wine etc at terminal was okay.

Then I went to the files page and double clicked on crucial.exe and I got the Adobe manual loaded. The front page of the game appears giving choices to click on Install Game, View Electronic Manual, Help, Exit, yet nothing happens when I click or double click Install Game to start Civ 1.

---

### Post by codeseer on 2009-04-21
After you've installed it to wine using the previous command, you will then need to run it under wine using something like this:

```

wine ~/.wine/drive_c/Program\ Files/Civ1/Civ1.exe

```

Just hit Tab on your keyboard to find the proper paths below 'program files'.

---

### Post by darkenergy4 on 2009-04-22
Is the first - a tilde or a dash?

---

### Post by codeseer on 2009-04-22
> **darkenergy4 said:**
> Is the first - a tilde or a dash?

Tilde. Shift+[The Key Left of the Number One, at the Top Left of the Keyboard].

---

