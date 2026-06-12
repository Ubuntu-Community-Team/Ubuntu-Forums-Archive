---
title: "Disabling desktop effects in 11.04"
date: 2011-04-28
forum: Desktop Environments
---

### Post by Dry Lips on 2011-04-28
I've just upgraded to 11.04, but Unity is unfortunately not my cup of tea.
 I use the classic desktop but I cannot find a way to disable a certain 
graphical desktop effect... I'm thinking of how the current workspace
quickly slides into the next when I choose a different workspace. 

     If my recollection is correct, you could turn effects like that
 off in 10.10. This makes me dizzy, :-& does any of know how to turn this off?

---

### Post by cecilpierce on 2011-04-28
> **Dry Lips said:**
> I've just upgraded to 11.04, but Unity is unfortunately not my cup of tea.
 I use the classic desktop but I cannot find a way to disable a certain 
graphical desktop effect... I'm thinking of how the current workspace
quickly slides into the next when I choose a different workspace. 

     If my recollection is correct, you could turn effects like that
 off in 10.10. This makes me dizzy, :-& does any of know how to turn this off?

Open a terminal window and type ccsm, then look at Desktop>Desktop Wall, see if it disables the slider.

---

### Post by Dry Lips on 2011-04-28
I had to install
 ```
sudo apt-get install compizconfig-settings-manager
```  Really nice program, btw! I'm definitively going to have a closer look at it!
 
 I went to Desktop>Desktop Wall>Viewport Switching  
 and set &#8220;Wall sliding duration&#8221; to 0.
 
at Desktop>Desktop Wall>Viewport Switch preview
 I also set &#8220;Switch target preview visibility time&#8221; to 0.
 
Voila! Thanks a lot. My head has stopped spinning now! [B]8-)
[/B]

---

### Post by cecilpierce on 2011-04-28
> **Dry Lips said:**
> I had to install
 ```
sudo apt-get install compizconfig-settings-manager
```  Really nice program, btw! I'm definitively going to have a closer look at it!
 
 I went to Desktop>Desktop Wall>Viewport Switching  
 and set “Wall sliding duration” to 0.
 
at Desktop>Desktop Wall>Viewport Switch preview
 I also set “Switch target preview visibility time” to 0.
 
Voila! Thanks a lot. My head has stopped spinning now! [B]8-)
[/B]

Glad it worked out, I like the cube but its hard to get it going without a lot of editing files and I'm not to lucky sometimes !  :)

---

### Post by Krytarik on 2011-04-28
> **Dry Lips said:**
> 
 I went to Desktop>Desktop Wall>Viewport Switching  
 and set “Wall sliding duration” to 0.
 Thanks for that tip, I didn't notice that setting before. I regularly switch workspaces, and disabling those feature makes that indeed much snappier. =)
> **Dry Lips said:**
> 
 at Desktop>Desktop Wall>Viewport Switch preview
 I also set “Switch target preview visibility time” to 0.
 
You can disable those feature completely by unticking "Show Viewport Switcher Preview".

---

### Post by Krytarik on 2011-04-29
> **Dry Lips said:**
> 
 I went to Desktop>Desktop Wall>Viewport Switching  
 and set “Wall sliding duration” to 0.
 
And you can disable those feature completely by setting "Non Sliding Windows" to "any".

---

### Post by Dry Lips on 2011-05-02
> **Krytarik said:**
> And you can disable those feature completely by setting "Non Sliding Windows" to "any".

Thanks Krytarik! This made it even snappier.

However I'm having another problem. When a window is minimised, and you click on it again, it makes this jumping motion, if you know what I mean... Does any of you know how to disable this?

---

### Post by Krytarik on 2011-05-02
> **Dry Lips said:**
> When a window is minimised, and you click on it again, it make this jumping motion, if you know what I mean... Does any of you know how to disable this?
I guess your are meaning "CompizConfig Settings Manager -> Animations -> Minimize Animation", there is by default a single rule, which is set to "Zoom", just set it to "None".

---

### Post by Dry Lips on 2011-05-02
Yep! That's the one. Thanks again! :D

---

