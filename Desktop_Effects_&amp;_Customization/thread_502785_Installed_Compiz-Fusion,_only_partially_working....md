---
title: "Installed Compiz-Fusion, only partially working..."
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by Hexydes on 2007-07-17
Ok, so  bit the bullet and installed Compiz-Fusion, despite the fact that Beryl was running fine...

So at the end of the tutorial I ran (from Alt + F2), "compiz -- replace". That seemed to work fine. Some stuff happened, and then when I tried to do the standard cube rotate, it looked like compiz-fusion took over and turned the cube into a flat plane (only two virtual desktops, instead of four). They were all shaded and nice looking, so I take it that it was working.

So I logged out, and logged back in. Now, only some of the plug-ins are working. It seems like the ones that don't require any keyboard input (i.e. translucent windows when dragging, wobbly windows, etc) work fine, but when I try to do something like the desktop cube, or paint fire, nothing works.

I have compiz-fusion starting automatically by having the following in the startup list:

- "beryl-manager"
- "compiz -- replace"

I am using Ubuntu 64-bit edition, if that makes any difference.

Thoughts? Thanks!

---

### Post by abrichr on 2007-07-17
The number of desktops you'll see in the "cube" depends on the number of desktops you set in GDM.  You can change this by right-clicking on the workplace switcher applet on one of your panels (if you don't see this, right-click on one of the panels, click "add to panel", and select the workplace switcher applet).  You'll need to kill compiz-fusion before you do this.

As for the plugins, make sure they're enabled in the compiz config settings manager.  To access this, hit ALT+F2 and type in "ccsm".

---

### Post by crazyhunk on 2007-07-17
try removing Beryl-manager...

and try it...and also check if all the plugins u said are enabled and correctly configured....

---

### Post by Hexydes on 2007-07-17
Heh, yeah, I have all those. I wish it was that easy. ;)

I added the workspace application, for some reason it was set to one (even though I could ctrl + alt + right/left through them...), so I bumped it up to four, but no dice. I logged out/in to make sure, but it still doesn't work.

I have all of the effects enabled, and the shortcuts set...it's just that nothing happens when I activate them. It never had any trouble on Beryl. :(

So just to get this straight, I still have Beryl-Manager loading on startup, as well as compiz -- replace. If I don't have beryl-manager set to run, then I lose all of my window borders. Does that sound right? It sounded wrong to me because I thought compiz-fusion replaced Beryl/Compiz, but maybe I'm wrong?

---

### Post by crazyhunk on 2007-07-17
> **Hexydes said:**
> Heh, yeah, I have all those. I wish it was that easy. ;)

I added the workspace application, for some reason it was set to one (even though I could ctrl + alt + right/left through them...), so I bumped it up to four, but no dice. I logged out/in to make sure, but it still doesn't work.

I have all of the effects enabled, and the shortcuts set...it's just that nothing happens when I activate them. It never had any trouble on Beryl. :(

So just to get this straight, I still have Beryl-Manager loading on startup, as well as compiz -- replace. If I don't have beryl-manager set to run, then I lose all of my window borders. Does that sound right? It sounded wrong to me because I thought compiz-fusion replaced Beryl/Compiz, but maybe I'm wrong?

ok I am not sure if I am 100% right....

but try stopping beryl-manager and if u have the latest Emerald (assuming u use emerald) try starting just emerald for the window decoations.....

```
compiz --replace -c emerald &
```

---

### Post by the_maassk on 2007-07-17
Try updating emerald and its libs from the Trevino's repos. The version I was using was not compatible with Compiz Fusion.

---

### Post by Hexydes on 2007-07-17
> **crazyhunk said:**
> ok I am not sure if I am 100% right....

but try stopping beryl-manager and if u have the latest Emerald (assuming u use emerald) try starting just emerald for the window decoations.....

```
compiz --replace -c emerald &
```

So for this, can I just remove beryl-manager from my session startup, log out, log in, and then run that command using Alt + F2?

---

### Post by Hexydes on 2007-07-17
> **the_maassk said:**
> Try updating emerald and its libs from the Trevino's repos. The version I was using was not compatible with Compiz Fusion.

Ok, I will indeed try that if Crazyhunk's suggestion doesn't work. Does Trevino's repo have 64-bit support?

---

### Post by Hexydes on 2007-07-17
Could maybe this be something to try as well (sorry, I'm not at home so I can't try anything for a few more hours):

[http://ubuntuforums.org/showthread.php?t=492752](http://ubuntuforums.org/showthread.php?t=492752)

Seems like it might be something, especially considering that Compiz-Fusion worked one time, and now it is only partially-working...

---

### Post by Hexydes on 2007-07-18
> **crazyhunk said:**
> ok I am not sure if I am 100% right....

but try stopping beryl-manager and if u have the latest Emerald (assuming u use emerald) try starting just emerald for the window decoations.....

```
compiz --replace -c emerald &
```

Just FYI for anyone that encounters the same problem, the above worked. Just kill beryl-manager, and run the above line of code using Alt + F2. If it works, just go to your sessions, remove beryl-manager, and add the above code as a new item for "Compiz-Fusion".

Thanks a lot Crazyhunk! :)

---

