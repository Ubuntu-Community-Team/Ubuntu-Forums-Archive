---
title: "Assaultcube problems"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by Enarchay on 2009-08-09
I started playing Assaultcube a few days ago. It worked fine the first day I downloaded it, but recently when I open the game, the character view is aimed up at the sky, and when you try to move the mouse up and down, it rapidly spins in circles. I assume this is a mouse sensitivity issue. I have a Logitech G5 mouse and it worked when I first downloaded the game.

    Additionally, I set the resolution to 1920x1080, but it doesn&#8217;t seem like everything is showing up. For example, my health bar and such isn&#8217;t on the screen. This is odd because when I first started playing Assaultcube, I played it at the same resolution. 

  The only thing I can think of that might be causing this is that I updated my motherboard&#8217;s BIOS software and my video card&#8217;s drivers. I don&#8217;t see why this would be affecting Assaultcube, though.
    Any idea how I can fix these two issues?

Oh, and by the way, I've re-installed the game twice - it didn't help.

---

### Post by Soulcage on 2009-08-10
Did you try to delete the setting files rm ~/.assaultcube_v1.0 ?

---

### Post by Enarchay on 2009-08-10
No, I didn't. How do I do that?

---

### Post by noerrorsfound on 2009-08-10
Applications | Accessories | Terminal

```
cd ~/.assaultcube_v1.0/config
rm init.cfg saved.cfg
```
Or, without the terminal, you can go to your home folder, push Ctrl-H to reveal hidden files, open .assaultcube_v1.0, open config, and then select and delete those two files.

---

### Post by Enarchay on 2009-08-10
I couldn't find either of those two files. Maybe I'm misunderstanding you.

I went into Program Files, Assaultcube, and then the Config folder. I unlocked hidden folders. Didn't see either of the two files.

I'm using Vista by the way.

---

### Post by noerrorsfound on 2009-08-10
Oh, you're not on Linux. For Vista, check: C:/Users/YourUsername/Documents/AssaultCube_v1.0/config

---

### Post by Enarchay on 2009-08-10
The files you said to delete are not in the Config folder.

---

### Post by 569874123 on 2009-08-11
> **Enarchay said:**
> The files you said to delete are not in the Config folder.

I know this is kind of off-topic, but how about trying it on ubuntu?

---

### Post by Enarchay on 2009-08-11
I really don't feel like installing a new OS. The only reason I joined these forums is because when I searched google for the issue I'm encountering on Assaultcube, a few threads came up on this forum.

---

### Post by Enarchay on 2009-08-20
Anyone have any other ideas?

---

### Post by Enarchay on 2009-08-20
I tried the game again and the problem just resolved itself. No idea what went wrong. Hopefully it doesn't happen again.

---

