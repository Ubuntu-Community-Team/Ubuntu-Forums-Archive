---
title: "Unity sidebar getting in the way"
date: 2011-11-10
forum: Desktop Environments
---

### Post by djsmaximus on 2011-11-10
When I have Firefox maximized, every time I go over to hit the back button, the Unity sidebar keeps popping out and getting in my way. It is frustrating and causes me to lose a lot of time. Maybe if the back button wasn't so close to the edge of the screen, or maybe if the sidebar could only be revealed if the mouse was more towards the center-left side of the screen? I don't know how to fix it, but it is a real showstopper for me.:confused:

---

### Post by Copper Bezel on 2011-11-10
Do you have Compizconfig installed? If not, grab it from the Software Center, or run: ```
sudo apt-get install compizconfig-settings-manager
```

Open it up and navigate to the Ubuntu Unity plugin. You can change the Launcher Reveal Mode from Left to Top Left (click the little button that says Left, click the left side on the little monitor display that comes up to deselect it, and click the upper-left corner.) Now it will only display when you hit the upper-left hot corner instead of the whole left side.

There's no way to set it to a specific region (like the left center) but see if the corner works for you.

---

### Post by stinkeye on 2011-11-10
Change the hide launcher to never in... *ccsm > unity plugin*.
or
Change the reveal mode to top left or bottom left in... *ccsm > unity plugin*.
or 
In *firefox > view > toolbars > customize*... add a couple of spaces to the left of the back button.

---

