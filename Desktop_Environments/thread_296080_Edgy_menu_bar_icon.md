---
title: "Edgy menu bar icon"
date: 2006-11-09
forum: Desktop Environments
---

### Post by johnny9794 on 2006-11-09
Hey all.

I have spent the whole day googling and searching the Ubuntu forums on How-to change the menu bar icon that sits to the left of Applications.

I have ran into a lot of how-to's and tried all the ones that I have found but none of em have worked and plus there all mainly for ubuntu 6.06.1 and under, breezy and other distro's except I have not ran into one for Edgy eft.

I would like to change the Ubuntu menu bar icon to the gnome foot icon for Ubuntu 6.10.

Would anyone have any suggestions to help a fellow out?

Thanx :).

---

### Post by Ghaagsheblah on 2006-11-09
Just replace the distributor-logo in the places-folder for your current theme.

The iconthemes are located in either /usr/share/icons/ or ~/.icons/

---

### Post by johnny9794 on 2006-11-10
I tried that it does not work.

[edited]
Has anyone successfully changed the menubar icon to the gnome foot in edgy 6.10?
if so could you plz reply with instructions.

thank you.

---

### Post by Ghaagsheblah on 2006-11-10
does the theme you have use png or svg icons? is it various sizes on the icons or scalable?

tried it on a edgy 6.10 computer at office and it worked just fine to replace the distributor-logo to another icon.

---

### Post by johnny9794 on 2006-11-10
> **Ghaagsheblah said:**
> does the theme you have use png or svg icons? is it various sizes on the icons or scalable?

tried it on a edgy 6.10 computer at office and it worked just fine to replace the distributor-logo to another icon.

um I don't know what the Human theme uses but this screenshot should sum things up a little i cannot figure out why the logo will not change
I have changed all the distributor-logo.svg logo's to the gnome foot.
I have changed all the distributor-logo.png logo's to the gnome foot.

What theme were you using on your computer at the office and what did you do to change it?

Here is the screenshot
[http://johnny9794.googlepages.com/Screenshot.png](http://johnny9794.googlepages.com/Screenshot.png)

Maybe I am asking the wrong question or not asking it correctly.

---

### Post by johnny9794 on 2006-11-10
Few hours later

I went ahead "curious" and right clicked on the panel then click add to panel and the foot is in Add to panel/Utilites/Main Menu and Menu Bar.
Screenshot
[http://johnny9794.googlepages.com/AddToPanel.png](http://johnny9794.googlepages.com/AddToPanel.png)

Main Menu Utility:
So i added Main Menu Utility to the bar and the foot is there in the panel
[http://johnny9794.googlepages.com/MainMenu.png](http://johnny9794.googlepages.com/MainMenu.png)

Menu Bar Utility:
I added an extra Menu Bar Utility just to see if the second menu bar showed up with a foot but does not.
[http://johnny9794.googlepages.com/MenuBar.png](http://johnny9794.googlepages.com/MenuBar.png)

i have no clue why it will not appear I am sorry if i am being annoying to the forums about this.

---

### Post by johnny9794 on 2006-11-10
I got the foot :)...

How-to that worked for me on edgy that i figured out on my own.

I downloaded my gnome foot .svg image from [http://live.gnome.org/BrandGuidelines](http://live.gnome.org/BrandGuidelines) to my desktop.

Then I opened up the terminal and typed in sudo nautilus and navigated to /usr/share/icons/gnome/scalable/places ,
when i got to that location i backed up my original distributor-logo.svg by renaming it to distributor-logo.svg.BACKUP

Now that new .svg image that i downloaded to my desktop, I renamed that to distributor-logo.svg then I right clicked it, copy and then right click, paste in the nautilus window in /usr/share/icons/gnome/scalable/places

Now close everything.

Then I opened up Theme manager under System/Preferences/Theme and selected any theme and that refreshed and applied that gnome foot icon next to Applications.
Screenshot:
[http://johnny9794.googlepages.com/Gnomefoot.jpg](http://johnny9794.googlepages.com/Gnomefoot.jpg)

This works using gnome icon theme in theme manager.

I hope that this helps someone else out if they are having a problem changing there menu logo.

I been on this mission for 2 days now :S alot of time for one little thing lol.

---

