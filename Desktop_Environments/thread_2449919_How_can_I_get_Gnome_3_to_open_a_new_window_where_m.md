---
title: "How can I get Gnome 3 to open a new window where my mouse is?"
date: 2020-09-04
forum: Desktop Environments
---

### Post by Paddy Landau on 2020-09-04
I've always set my system to open a new window where my mouse is. To clarify, when I open a new window, it sees where my mouse is, and opens the window to centre on my mouse, subject to the limitations of the screen height and width.

But, that was during the days of Compiz (remember it?) and, until now, in Lubuntu.

I've moved to Ubuntu with Gnome, and I can't find a way to do this. How can I do this in Gnome?

I'm running Ubuntu 18.04 with Gnome 3.

Thank you

---

### Post by vanadium on 2020-09-06
Unfortunatelly, afaik, this is not possible with Gnome. You can have the default "smart" placement of new windows, or have new windows always centered, but that is it, I am afraid.

---

### Post by ActionParsnip on 2020-09-07
New window of what? You can't "Open a new window" in any OS? Do you mean "Run the default file manager"?

---

### Post by Paddy Landau on 2020-09-08
> **vanadium said:**
> Unfortunatelly, afaik, this is not possible with Gnome. You can have the default "smart" placement of new windows, or have new windows always centered, but that is it, I am afraid.
That's frustrating! I don't suppose that there's a Gnome extension for that (I haven't found one).
> **ActionParsnip said:**
> New window of what?
Any new window. For example, if I open Gedit, Files, gnome-terminal, Chrome, whatever. In Lubuntu, I could tell the system that a new window should open centred on my mouse (subject to the limitations of the screen edges), so I simply put my mouse where I wanted the window to open. But Gnome decides where the window goes, which means that, almost every time, I have to move the window to a more convenient point. It wastes time.

---

### Post by ActionParsnip on 2020-09-08
You could write a script that gets the mouse X and Y coordinate if you run the below:
```

sudo apt-get install xdotool

```

If you then run:
```

sleep 3; xdotool getmouselocation

```

You can move the mouse somewhere and after 3 seconds it will show the location.

Just need to work out how to use this information to launch a chosen application at this location. Possibly devilspie?

---

### Post by ActionParsnip on 2020-09-08
[https://unix.stackexchange.com/questions/43106/how-to-set-window-size-and-location-of-an-application-on-screen-via-command-line](https://unix.stackexchange.com/questions/43106/how-to-set-window-size-and-location-of-an-application-on-screen-via-command-line)

May be the key. Have a play. You could have hot keys that run gedit, nautilus and so forth but where your mouse is. Could be fun. Just spam the keyboard to fire up loads of text editors all over

---

### Post by Paddy Landau on 2020-09-08
> **ActionParsnip said:**
> [https://unix.stackexchange.com/questions/43106/how-to-set-window-size-and-location-of-an-application-on-screen-via-command-line](https://unix.stackexchange.com/questions/43106/how-to-set-window-size-and-location-of-an-application-on-screen-via-command-line)

May be the key. Have a play. You could have hot keys that run gedit, nautilus and so forth but where your mouse is. Could be fun. Just spam the keyboard to fire up loads of text editors all over
Hmm, thanks for the ideas. Unfortunately, that works only when you know in advance which window you're about to open. I'd have to write a custom script for each and every GUI app that I regularly use!

I have used Devilspie a long time ago, but there is the problem that you have to decide in advance where you want the window to open. I just want it to open where my mouse is.

Maybe I'll open a request for the Gnome team, if I can find out how to do so.

---

