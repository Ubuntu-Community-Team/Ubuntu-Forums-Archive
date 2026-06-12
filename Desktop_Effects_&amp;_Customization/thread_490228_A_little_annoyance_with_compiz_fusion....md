---
title: "A little annoyance with compiz fusion..."
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by orange2k on 2007-07-02
Compiz fusion runs just fine and I love it!
But there is something that annoys me: when I start VLC to play a video and I put it fullscreen, the picture is half-transparent, so I can see the wallpaper or whatever there is in the background.
Is there a way to turn off this "feature"? I was looking all over the compiz settings but I couldnt find anything...:(

---

### Post by Ub1476 on 2007-07-02
Well, I know when you hold a window (to drag around usually) the background gets half transparent. I don't see how it could be hold down on fullscreen, but...

[Checking movie with VLC]

Same problem here..  It helps if you put video size on double/ stretching the window. Also I have no problem withthe transparent in the preinstalled video player. 

Hope you figure out something, might be something around Accessibility or  Effects.

Good luck

Between, you can quite simple turn of CF when watching a movie. I see no reason to use it then.:p

---

### Post by AriciU on 2007-07-02
I removed the default transparency all together. Menu's, player, etc.

Open Compiz config settings manager and go to General options / Opacity settings. You will have a line there about Windows Opacity. I removed it all together to get rid of the whole thing but if you want to get rid only of the video player window transparency then experiment with it by removing only certain "words" from that line and see what has changed. Do it untill you find the one witch controls window transparency for the player and you're set.

---

### Post by outphase on 2007-07-02
Under CCSM, General Options, Opacity Settings:

((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer | **state=fullscreen**) you can also do something like name=vlc in the same box.

---

### Post by crimesaucer on 2007-07-02
This also worked for me:

To remove transparency for video playback:

open ccsm 

and click:  General Settings-->--Opacity Settings-->--Windows Opacity, and edit the Opacity windows string by highlighting the string, and then pressing "Edit" below it.

...edit the "Unknown" part, out off the string in Opacity windows, then press OK.

the string should look like this now:

```
((type= Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

---

### Post by l-fever on 2007-07-10
> **crimesaucer said:**
> This also worked for me:

To remove transparency for video playback:

open ccsm 

and click:  General Settings-->--Opacity Settings-->--Windows Opacity, and edit the Opacity windows string by highlighting the string, and then pressing "Edit" below it.

...edit the "Unknown" part, out off the string in Opacity windows, then press OK.

the string should look like this now:

```
((type= Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

Sweet! Worked for me as well! Thanks!

---

### Post by l-fever on 2007-07-10
I also noticed that when the screensaver becomes active, the screen darkens and becomes transparent as well. Hmmmm....

---

### Post by QwUo173Hy on 2007-07-22
My screensaver is partially transparent too. And I have removed the Unknown part from the Window Opacities. Does anyone know how I can fix this?

---

### Post by l-fever on 2007-07-22
> **jarlath said:**
> My screensaver is partially transparent too. And I have removed the Unknown part from the Window Opacities. Does anyone know how I can fix this?

I edited the opactiy line and removed everything between the ( )'s and saved the setting.

---

### Post by QwUo173Hy on 2007-07-23
Does that not mean you have no opacities for anything though? Or did it work?

---

### Post by l-fever on 2007-07-23
> **jarlath said:**
> Does that not mean you have no opacities for anything though? Or did it work?

It appears that when I drag or move a window it is transparent. When I place or let go then the opacity goes away.

---

### Post by QwUo173Hy on 2007-07-23
Thanks l-fever. My screensaver is good again! I've lost my menu opacities as a result but I pasted that line into Text Editor and saved it so I can put it back in another day and start tweaking to see what I get.

Thanks again.

---

### Post by l-fever on 2007-07-23
> **jarlath said:**
> Thanks l-fever. My screensaver is good again! I've lost my menu opacities as a result but I pasted that line into Text Editor and saved it so I can put it back in another day and start tweaking to see what I get.

Thanks again.

Cool!:)

---

### Post by tschneiter on 2007-08-04
The offending entry in the opacity menu turned out, for me, to be the "DropdownMenu" part of the line. Removing it kills opacity on dropdown menus but makes VLC work proper-like. Perhaps a screensaver fix too?

---

