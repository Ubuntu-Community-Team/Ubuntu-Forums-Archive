---
title: "Firefox won't launch with Launchy"
date: 2009-01-21
forum: General Help
---

### Post by demii on 2009-01-21
Good day.

Whenever I type "firefox" in Launchy and hit enter, Firefox's script (I believe it's the script; I'm somewhat new to Linux) is opened in gedit instead of the web browser. Under firefox in Launchy, it says "Firefox Web Browser: /usr/bin/firefox." Initially it was "/usr/bin/firefox %u".

However, when I hit tab and type a website, google.com for example, Firefox launches with the site I entered.

Why does the script launches instead of the browser and what could I do to remedy this?

---

### Post by DeMus on 2009-01-21
> **demii said:**
> Good day.

Whenever I type "firefox" in Launchy and hit enter, Firefox's script (I believe it's the script; I'm somewhat new to Linux) is opened in gedit instead of the web browser. Under firefox in Launchy, it says "Firefox Web Browser: /usr/bin/firefox." Initially it was "/usr/bin/firefox %u".

However, when I hit tab and type a website, google.com for example, Firefox launches with the site I entered.

Why does the script launches instead of the browser and what could I do to remedy this?

I doesn't start with your homepage when you use the %u at the end of the command?
In Applications | Internet you also find a launcher. Does it start?
When you copy it to your desktop or panel at the top of the screen (just right-click on it and choose: Add this launcher to desktop (or panel) does it start?
When you right-click the new launcher and choose properties, select tab launcher, what does it start?

---

### Post by Stefanie on 2009-01-21
try gnome-do . it's like launchy but it has got more possibilities.

---

### Post by demii on 2009-01-21
> **DeMus said:**
> I doesn't start with your homepage when you use the %u at the end of the command?
In Applications | Internet you also find a launcher. Does it start?
When you copy it to your desktop or panel at the top of the screen (just right-click on it and choose: Add this launcher to desktop (or panel) does it start?
When you right-click the new launcher and choose properties, select tab launcher, what does it start?

No, when %u was at the end, it didn't start with my homepage.

It launches from my panel, desktop, and Applications > Internet > Firefox Web Browser just fine. 

There is no "tab launcher" when I right click it from my desktop (or panel).

---

### Post by demii on 2009-01-21
> **Stefanie said:**
> try gnome-do . it's like launchy but it has got more possibilities.

Ah. I'm duel booting Ubuntu from OSX and gnome-do is just like QuickSilver. I like launchy more though... 

How does gnome-do have more possibilities?

---

### Post by DeMus on 2009-01-21
> **demii said:**
> No, when %u was at the end, it didn't start with my homepage.

It launches from my panel, desktop, and Applications > Internet > Firefox Web Browser just fine. 

There is no "tab launcher" when I right click it from my desktop (or panel).

Strange, I copied the launcher from the Applications menu onto my desktop and panel so I can use them easily. When I rightclick on the one on my desktop and choose properties I see the picture as attached.
Strange this doesn't work with you.

---

### Post by Stefanie on 2009-01-22
> **demii said:**
> Ah. I'm duel booting Ubuntu from OSX and gnome-do is just like QuickSilver. I like launchy more though... 

How does gnome-do have more possibilities?

check out the plugins. if you click on the arrow in the upper right corner you can select preferences and then the plugins. i use them all the time.

---

### Post by fedoroff on 2009-05-25
One of the possible ways to solve this problem is to add new command with "firefox" name to Runner plugin list.

Launchy -> Options
Plugins tab
Runner menu from the left list
hit "+" to add new command (name - "firefox", command - "firefox").

After this, you can just type "firefox" in launchy main window and choose your created command (not the one with firefox logo).

---

