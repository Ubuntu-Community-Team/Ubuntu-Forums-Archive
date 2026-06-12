---
title: "Programs from All Workspaces Show on Same (Classic) Taskbar After 12.04 Upgrade"
date: 2012-05-02
forum: Desktop Environments
---

### Post by OzzyFrank on 2012-05-02
OK, this is a new one: when I switch workspaces, the taskbar (I'm obviously using Gnome 3 Classic) is the same in each, meaning even if I have nothing open in Workspace 2, the taskbar will be full of apps open in Workspace 1, and clicking any will see me back at Workspace 1. Similarly, any apps I have open in Workspace 2 will be visible in the taskbar in Workspace 1, and clicking one will take me to Workspace 2.

Now, I know right-clicking a taskbar button can give you the option of "Only on This Workspace", but besides the fact I don't really want to do this for every thing I ever open (especially since I never had to before the upgrade), but it simply doesn't work, so isn't even an option.

I've had to fiddle with some Compiz settings after the upgrade - like disabling Unity within the Classic desktop so both weren't running at once, and enabling "Place Windows" so everything wasn't opening in the top-left with the titlebars hidden under the top panel - but I simply can't find where to change this really annoying setting which renders the whole concept of workspaces useless. Any ideas?

PS: The obvious solution of opening "Window List Preferences" and disabling "Show windows from all workspaces" is a no-go, as it is already set to "Show windows from current workspace", which is the default.

---

### Post by mc4man on 2012-05-02
right click on the left edge of the window list applet till you get it's preferences.
change there - screen

---

### Post by OzzyFrank on 2012-05-02
> **mc4man said:**
> right click on the left edge of the window list applet till you get it's preferences.
change there - screen

Thanks buddy, but I'd actually covered that, explaining that it doesn't work. Or should I say, it was already set at the default of "Show windows from current workspace", so it wasn't the answer. Thanks anyway.

---

### Post by mc4man on 2012-05-02
Somehow missed the PS
It works fine here, have you tried another user or guest session?

What does it show in dconf-editor?, screen

---

### Post by OzzyFrank on 2012-05-06
Hi. DConf was no help, but I stumbled on a workaround. At first I couldn't tell you what I did, as I went playing with all the Compiz workspaces settings, and the Window List preferences, until it worked as it should. The reason I couldn't tell you is that besides just clicking this and that till all the wacky combinations of "almost working" got me where I wanted, in the end I had actually reset everything to the way it was when I started! But I got it working fine... till the next reboot.

So this time I decided to try one thing at a time, and it isn't Compiz or Window List Preferences - the answer is this:

Make sure the **Workspace Switcher** is on the panel - I had to to add it again, as I got rid of it years back (easier to Ctrl+Alt+Arrow to another desktop), and **right-click it and choose Preferences**. At the bottom under **Workspaces**, my setting was 2, and setting it to 4 wasn't the answer - but **setting it to 1** seems to be.

---

### Post by OzzyFrank on 2012-05-08
UPDATE: I had to switch to Metacity to test an EOG (Image Viewer) display issue in Compiz, and when back in Compiz, the taskbar issue reappeared. Sure enough, the preferences for the Workspace Switcher showed the number of desktops had been reset to 4, so changing that back to 1 gave me my 4 desktops each with their own unique taskbar.

---

### Post by astro_dave on 2012-06-26
Thank you for posting the solution OzzyFrank; I very much appreciate it.

---

### Post by alan89mx on 2012-10-08
I have this same problem and when I try to right click on the workspace switcher nothing happens. I don't get any options. Anyone has any idea why I don't get anything?

---

