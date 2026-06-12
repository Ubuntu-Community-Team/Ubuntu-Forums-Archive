---
title: "Custom Nautilus Action Button in Toolbar"
date: 2009-05-14
forum: General Help
---

### Post by niokei on 2009-05-14
**Hi!**
I recently played with a nautilus a little, and customized the standard nautilus window, and I have a two part problem: I'm able to insert buttons on the toolbar which are predefined as seen on the picture, basically what I would like to do is to be able to insert custom "Go to Folder" buttons, and for some actions that are already defined to show an icon, rather than text like the "Show Hidden Files" button.
All this I modified in the folder usr/share/nautilus. In this folder I didn't find anything where this actions like "Go to Computer" are defined, and with my basic programming knowledge there should be somewhere a segment at least, where these variables and such are defined.
**What workarounds I already tried:**

[LIST]
[*]Some other formats of location like: Go to Documents, Go to /usr etc.
[*]For the icon part of the problem: I found the folder where the other actions icons are and made an icon with the same name structure the others had, but I guess somewhere this should be also defined which actions uses which icon.
[*]I looked around in the usr/share folders that would have been logical for such a file.
[/LIST]
I'm still searching here on the forum, but I'm not sure what for should I exactly search for.
**I appreciate every help!**

[[IMG]http://f.imagehost.org/t/0955/Screenshot-1.jpg[/IMG]]("http://f.imagehost.org/view/0955/Screenshot-1")

---

### Post by frodon on 2009-05-18
Moved to general help

---

### Post by niokei on 2009-09-14
Bump.

Basically this is the code I need to edit:

```
</menubar>
<toolbar name="Toolbar">
    <toolitem name="Back" action="Back"/>
    <toolitem name="Forward" action="Forward"/>

    <!-- <toolitem name="Up" action="Up"/> -->
    <!-- <toolitem name="Stop" action="Stop"/>
    <toolitem name="Reload" action="Reload"/> -->
    <toolitem name="StopReload" action="StopReload"/>
    <!-- <separator/> -->
    <toolitem name="Home" action="Home"/>
    <!-- <toolitem name="Computer" action="Go to Computer"/>
    <separator/> -->
    <!--toolitem name="Search" action="Search"/-->
    <placeholder name="Extra Buttons Placeholder">
   [COLOR=Red] <toolitem name="Music" action="Music"/>[/COLOR]
              <placeholder name="Extension Actions"/>
        </placeholder>
    <!-- <separator/> -->
</toolbar>
```

---

### Post by NoaHall on 2009-09-14
sudo apt-get install nautilus-actions. There you go.

---

### Post by niokei on 2009-09-14
> **NoaHall said:**
> sudo apt-get install nautilus-actions. There you go.

Thanks, but thats not what I mean. Here is a quick mockup:

[[IMG]http://h.imagehost.org/0890/Screenshot.png[/IMG]]("http://h.imagehost.org/view/0890/Screenshot")

This would eliminate the need of the quite ugly side pane for me.

---

### Post by NoaHall on 2009-09-14
Oh, hm. You want to get to the computer screen? I think it's called "computer:///"

---

### Post by niokei on 2009-09-14
> **NoaHall said:**
> Oh, hm. You want to get to the computer screen? I think it's called "computer:///"

Nope, in nautilus on the menubar there are and can be some "actions". Currently there is for example the go-to Home folder action. I would like to have several similar go-to actions, like go-to downloads etc. 
Now there are the bookmarks in the side pane, but thats takes up a lot of space and is fugly. 
I found this file: /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml where I could add additional actions or buttons but if I simply type in the folders name that doesn't work. I guess there is an another file somewhere where these variables are defined, but I don't no where that is. 

But you can see on the mockup what I mean.

---

### Post by NoaHall on 2009-09-14
Ahhhh, I see. Sorry, I got a bit lost in what you meant :) I'll take a look now.

Uch - no good. I think you need to declare somewhere what the actions do, but I can't work out where.

---

### Post by niokei on 2009-09-14
> **NoaHall said:**
> Ahhhh, I see. Sorry, I got a bit lost in what you meant :) I'll take a look now.

Here is a before-after mockup:

[[IMG]http://h.imagehost.org/t/0638/Screenshotx.jpg[/IMG]]("http://h.imagehost.org/view/0638/Screenshotx")

I think it would be very useful.

---

### Post by NoaHall on 2009-09-14
I'm afraid I'm too tired to work it out - I'll check tomorrow.

---

### Post by niokei on 2009-09-14
> **NoaHall said:**
> Ahhhh, I see. Sorry, I got a bit lost in what you meant :) I'll take a look now.

Uch - no good. I think you need to declare somewhere what the actions do, but I can't work out where.

Yeah:) thats what I'm looking for three months now. I tried on the nautilus IRC, looked for the developers email addresses too but found nothing.

Thanks for your time anyway!

---

