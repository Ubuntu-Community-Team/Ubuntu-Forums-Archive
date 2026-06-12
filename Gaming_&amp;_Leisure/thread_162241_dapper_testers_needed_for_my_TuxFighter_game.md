---
title: "dapper: testers needed for my TuxFighter game"
date: 2006-04-18
forum: Gaming &amp; Leisure
---

### Post by HorstJENS on 2006-04-18
Hi,
i'm looking for testers willing to give me feedback about  my TuxFighter game (an little asteroid-like shooter). I tested my game on ubuntu dapper and i need to know:
did you can install / run the game ? (on what system/distro)
what framerate / score do you get ? (on what resolution/prozessor) ?
what is most needed missing feature ? (the most annoying bug) ?

The game is open source / gpl and you can download it at
[http://sourceforge.net/projects/pygamebook]("http://sourceforge.net/projects/pygamebook")
screenshots also aviable at the sourceforge site.

thank you in advance,
 /Horst

---

### Post by Perfect Storm on 2006-04-19
Okay. Testing the .deb package on Dapper Drake, gnome DE.

- Installing: Smooth, just a doubleclick on the package and it's rolling and solve the dependency. Though this is a minor thing: A launcher isn't made in the Application tab. So I had to run tuxfighter.py in the commandline.

I get 63 fps on my 1600x1200 24bit 19" screen. 2.4 Ghz P4 1024 mb (800Mhz). Gf 6600 GT.
Though I ran Tuxfighter while I had a lot of application running at the same time.

One thing I noticed if you shoot a window logo to close to you, you die. I don't know if it's a feature  or a bug.
Another thing is when you setting Screen resolution in the game, it don't resize the window. (added screenshot)

Edit: Also if the topten.txt could been saved as .topten.txt so it gets hidden away.

---

### Post by HorstJENS on 2006-04-19
Screen-resolution switching actually works, it is just ugly: you have to press ENTER at the "return to main menu" entry and after that activate the "Start new game" entry. The game then will start with the selected resolution. Next version of TuxFighter will have a better menu.

Collision-Detection: is a bit weak right now (invisible rect-boxes around the sprites), will improve it in the next versions.

---

### Post by Perfect Storm on 2006-04-19
Okay :)

Just forgot to mention it's fun and very addictive :)

---

### Post by HorstJENS on 2006-04-20
[QUOTE=Artificial Intelligence]Okay :)

Just forgot to mention it's fun and very addictive :)[/QUOTE]

That's my favorite posting ever ! Thank you :mrgreen:

---

### Post by HorstJENS on 2006-05-15
New Version of TuxFighter is aviable at 
[http://sourceforge.net/projects/pygamebook]("http://sourceforge.net/projects/pygamebook")
Game is tested under ubuntu dapper. a .deb package is aviable Thanks to AMDUser. Have Fun !

---

### Post by Perfect Storm on 2006-05-15
What about a Balmer monster :mrgreen: :mrgreen: :mrgreen:

---

### Post by Footissimo on 2006-05-15
Does it shoot chairs? ;)

---

### Post by benplaut on 2006-05-16
a pot powerup?!

that's just wrong...

---

### Post by Perfect Storm on 2006-05-16
It's for medication use.

---

### Post by HorstJENS on 2006-05-16
[QUOTE=Footissimo]Does it shoot chairs? ;)[/QUOTE]

Please enlighten me, i don't get this: Did Ballmer throw chairs around ?

---

### Post by HorstJENS on 2006-05-16
[QUOTE=benplaut]a pot powerup?!

that's just wrong...[/QUOTE]

Hi benplaut, you did me a big favor: my game is controversly debated worldwide ! :D :D :D 

To calm you down: The hemp symbol is acutally a power-down because it makes your shots very inpredictable and you get no points for shooting down aliens.

But if you really don't like it you can replace the line 308 in the File TuxFigher50.py:

```
            self.text = random.choice(("hemp","debian","wine")) 
```

with 

```
            self.text = random.choice(("debian","wine"))
```

it's a open source game, so you can modify it at will.

---

