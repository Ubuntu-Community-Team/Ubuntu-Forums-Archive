---
title: "bar bug in compiz"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Drag2004 on 2007-10-22
Hi, so im having a problem, only seems to happen when Compiz is enabled, but when i mouse towards the top of the window when it's full screen, or stretched across the entire screen, part of the bar with the minimize, and exit buttons turns half white and covers the buttons.

im currently at work, but ill try to get a screenshot later. couldnt find any problems like this in a search, so any help would be appreciated.

---

### Post by Drag2004 on 2007-10-22
Ok, finally got it to let me take a screenshot, it would sometimes dissapear when i hit the prntscreen button:

[IMG]http://i111.photobucket.com/albums/n141/Draget2004/Screenshot-1.png[/IMG]

---

### Post by BigSilly on 2007-10-23
I get this too. It looks just like yours. I don't know whether it's a Compiz thing, but I have found out that it only does it when using the default "Human" theme. I switched to the "Glider" theme and I don't see this anymore. Nevertheless it's still a bug isn't it? I like the Human theme!

---

### Post by omegamike on 2007-10-23
I had the same problem in another post. Here is how I got it working:


1. Crank open a terminal and install the advanced compiz settings manager:

```
sudo apt-get install compizconfig-settings-manager
```

2. Click on the Main Menu -> System -> Preferences -> Advanced Desktop Effects Settings

3. On the left side under "Category" click on Window Management

4. Click on "Place Windows"

5. Change the Placement mode to Centered

Hope this helps!

---

### Post by omegamike on 2007-10-23
Crud, I just realized my post was for a problem with the window when it wasn't maximized. Having the advanced settings installed might still allow you to change some settings though. Sorry bout the premature posting.

---

### Post by FuturePilot on 2007-10-23
I get the same thing sometimes. I've found out that it only happens when you use the Human Metacity or Glossy Metacity theme.

---

### Post by trmiv on 2007-10-23
I'm getting it while using clearlooks as well.  I've found I can always reproduce it if I click a link in Firefox that opens in a new tab.  It seems to happen frequently when clicking between tabs as well, but I can't always reproduce it that way.

---

