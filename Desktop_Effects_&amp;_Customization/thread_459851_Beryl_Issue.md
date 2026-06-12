---
title: "Beryl Issue"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by Chang An on 2007-05-31
Hi all,
I was messing with the advanced settings option you get from right clicking on the Beryl  Icon(Bad idea) and I changed the rendering settings from auto to force glx I believe.  I cant launch Beryl now cause it freezes.  I have tried uninstalling and reinstalling but it seems to keep the same broken settings.  Is there a way to completly remove all the files even the pakages that go to the  /user/share/app-install/desktop folder.  
Or is there a way to change the rendering settings back to auto from the command line.  Any help would be great.

---

### Post by Chang An on 2007-05-31
Any ideas?

---

### Post by Kuoi on 2007-06-01
Maybe you can try to type the following in terminal > beryl-manager --no-force-window-manager

Hope this way you can change the setting back.

Kuoi

---

### Post by grazzt on 2007-06-01
I did this once too, I think I removed the .beryl-manager file (or directory?).. Of course back this up first so you can always refer back to it.

---

### Post by pacman2440 on 2007-06-01
I actually did the same thing where I forced XGL and it froze with a blue screen.

I got around it by pressing <Control><Alt>Backspace and restarting. Then I quickly right clicked on the beryl icon and changed the settings to autoselect and had no problems. I know this doesn't really help the first person, but it might help someone else.

---

### Post by louislepperd on 2007-06-04
hi
anyone still here?
i have the same problem and cant fix it 
thanks in advance
louis

---

### Post by Kuoi on 2007-06-04
Have you tried my above reply ?

Kuoi

---

### Post by louislepperd on 2007-06-05
yes i tried it and it did not work
thanks in advance 
louis

---

### Post by Kuoi on 2007-06-05
Maybe you can try my reply in this topic : [http://ubuntuforums.org/showthread.php?t=458744]("http://ubuntuforums.org/showthread.php?t=458744")

It's more for the settings , but you'll never know it helps , Kuoi

---

### Post by Soybean on 2007-06-05
Beryl-manager stores all its settings in ~/.beryl-managerrc
So deleting that file might help, or even just editing it. My rendering setting is "Automatic" (I assume that's what you want too), and my file says ```
rendering_mode=0
```

So I suspect that if you open that file, and change your rendering mode to zero, that should probably do the trick.

---

### Post by Kuoi on 2007-06-05
> **Soybean said:**
> Beryl-manager stores all its settings in ~/.beryl-managerrc
So deleting that file might help, or even just editing it. My rendering setting is "Automatic" (I assume that's what you want too), and my file says ```
rendering_mode=0
```

So I suspect that if you open that file, and change your rendering mode to zero, that should probably do the trick.

And I was looking for a settings file in the .beryl folder ? 

Thanks to your tip , I've searched for the settings file , and it was right in the "home" folder.
As easy as it is sometimes ;)

And I think you're right , that should do the trick for louis.

Thanks for this  , Kuoi

---

### Post by louislepperd on 2007-06-06
hi i had a look at that and my rendering_mode was 0 too 
can you see any differences here? 

[wm-settings]
active_wm=0
fallback_wm=0
active_dm=0
iconsize=24
use_fallback_wm=true

[beryl-settings]
render_path=0
cow_mode=0
rendering_mode=0
platform=3
binding=0

thanks in advance
louis

---

### Post by Kuoi on 2007-06-06
This part changed a bit , so I suggest you  try my settings , it won't hurt i guess :

> [beryl-settings]
render_path=2
cow_mode=0
rendering_mode=0
platform=0
binding=0
no_gl_yield=false

Kuoi

---

