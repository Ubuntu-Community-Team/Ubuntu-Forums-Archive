---
title: "How can I create a launcher on a panel to a hard drive?"
date: 2009-04-07
forum: General Help
---

### Post by jermsie on 2009-04-07
Basically, I want to create a launcher that will open sda1 which is the windows C drive, and I want this launcher to be on one of my panels.

Can this be done?

---

### Post by VCoolio on 2009-04-07
Sure. Right mouse button on panel, click Add to panel. Choose Custom application launcher. Change type application to location and enter /media/sda1 [edit: this was wrong, thread concludes that location must be entered as file:///media/sda1] in the location entry box. Name and comment are free. Icon can be set by clicking on it. Click ok and you're done.

Edit: I tried this myself got an error message, lol. A location launcher works on desktop but not on panel, which seems a bug. If it's the same for you, then create panel launcher with type application and command: nautilus /media/sda1. Or change nautilus to whatever file manager you want to use.

---

### Post by jermsie on 2009-04-07
> **VCoolio said:**
> Sure. Right mouse button on panel, click Add to panel. Choose Custom application launcher. Change type application to location and enter /media/sda1 in the location entry box. Name and comment are free. Icon can be set by clicking on it. Click ok and you're done.

Following those instructions I get the error "**Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'**
"

As the location, I typed: /media/sda1

---

### Post by coffeecat on 2009-04-07
Have you seen VCoolio's edit? You need 'nautilus /media/sda1'

However, this will only work if the partition is already mounted. If you don't want to go to the Places menu, which would make a panel launcher unnecessary anyway, you'll have to add an entry to fstab.

---

### Post by jermsie on 2009-04-07
> **coffeecat said:**
> Have you seen VCoolio's edit? You need 'nautilus /media/sda1'

However, this will only work if the partition is already mounted. If you don't want to go to the Places menu, which would make a panel launcher unnecessary anyway, you'll have to add an entry to fstab.

Just tried it now and get "Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'"

sda1 and sda5 are always mounted. I recall doing something with fstab a long time ago

---

### Post by VCoolio on 2009-04-07
Did you make a new launcher with type application instead of location?
Edit: ok, found it. Either you do application with command 'nautilus /media/sda1' or you do location with location 'file:///media/sda1'. The last will automatically open with your default file manager.

---

### Post by jermsie on 2009-04-07
> **VCoolio said:**
> Did you make a new launcher with type application instead of location?

Opps! My bad. Thanks everyone. Problem solved!

---

### Post by coffeecat on 2009-04-07
That's a curious error message. I'm not getting it. I'm in Jaunty by the way, but I doubt that would make a difference.

Well - the final slash in /desktop/gnome/url-handlers/ is what it seems to be grumbling about, and that is a path in the g-conf editor. I've had a look in my  /desktop/gnome/url-handlers and I can't see anything that would be relevent. Have you fiddled with settings in g-conf before this? Does that path sound at all familiar?

**Edit:** Didn't see your last post when I posted.

---

### Post by coffeecat on 2009-04-07
Posted in error.

---

### Post by VCoolio on 2009-04-07
That's my error message allright. No, I didn't mess with that key in gconf-editor. I think problem is that link starts with /, as in /media/sda1. It is not the final / of the path but the first of the location. That's why it has to start with file:// I guess. Sucks though, it is not to be found anywhere and when you click browse you cannot point to a directory. I just got the idea of file:// because that's how a browser locates files. Anyway, it's solved.

---

