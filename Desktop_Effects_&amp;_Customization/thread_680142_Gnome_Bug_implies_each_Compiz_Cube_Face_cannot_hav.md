---
title: "Gnome Bug implies each Compiz Cube Face cannot have different image"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by BuntuFreak on 2008-01-27
Thanks to various people on this board, my Gutsy + Compiz + AWN Curves desktop is kicking Vista's behind from here to Timbucktoo. I just have one "effects" problem left to which there does not seem to be an easy solution.

I got the top and bottom faces of my rotating cube to show different images. That was simple. However, the 4 front faces of my cube will only render the image that I have currently set as my background image. While I have used the Compiz Settings Manager to setup images for the cube faces, just like I did for the Cube Caps, the latter works, but the former setting is simply getting ignored.

Other threads seem to indicate that Gnome has a limitation in that different desktops cannot have different images, something KDE does well. Now there's no way I'm switching to KDE. I love Gnome. So does that mean I have to live with not having different images for each of my 4 desktops, and therefore also my cube faces?

---

### Post by DaymItzJack on 2008-01-27
There are ways to get your cube like that, they just require a lot of work. If you search the forums, I'm pretty sure there is a how-to on the subject.

---

### Post by BuntuFreak on 2008-01-27
Well, first, I've seen all those google videos that show you it's possible. But before I go and hack my way into a solution, I wanted to ask if all those people who have accomplished it are using KDE or Gnome. That's a subtle detail that people don't always mention.

I have spent a week getting my Ubuntu installation to work like I want. Not just the "effects" aspects but various networking aspects as well. I'm only so far away from using Partimage and backing up my install and this cube problem is the last thing I wanted to try and fix before I did that.

I just don't want to waste any more time if any hack requires KDE. As per compiz settings manager, I should already have it working just by specifying the images. But clearly that's not the case.

---

### Post by Therion on 2008-01-27
There's a couple ways I've seen this done, but the easy solution (in Gnome) means losing your desktop icons.  All you really do is disable Nautilus such that it no longer draws the desktop.  Details [HERE]("http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html") under Wallpaper.

---

### Post by DaymItzJack on 2008-01-27
> **Therion said:**
> There's a couple ways I've seen this done, but the easy solution (in Gnome) means losing your desktop icons.  All you really do is disable Nautilus such that it no longer draws the desktop.  Details [HERE]("http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html") under Wallpaper.

I was starting to do that exact thing, and then I realized you couldn't right click on your desktop either, which kind of bugged me.. for some reason. I guess it doesn't really matter much though, since you can't have icons and all the right click menu does is make icons.. weird what the hell was I thinking?

So, I tried it, it worked fine. Then 5 minutes later I realized nautilus was running at 90%CPU.

---

### Post by BuntuFreak on 2008-01-28
> **DaymItzJack said:**
> I was starting to do that exact thing, and then I realized you couldn't right click on your desktop either, which kind of bugged me.. for some reason. I guess it doesn't really matter much though, since you can't have icons and all the right click menu does is make icons.. weird what the hell was I thinking?

Well Right-Click has various menu items on it. So I'm not sure I would be happy with that. Now, not having desktop icons is just fine because I'm using AWN, and would actually prefer a "clean" look to my desktop. In fact, I have "sda1" on my desktop, which is my Windows partition that has been mounted. I thought it was a shortcut but I can't get rid of it. So if that also disappears from my desktop, I would actually want that.

> **DaymItzJack said:**
> So, I tried it, it worked fine. Then 5 minutes later I realized nautilus was running at 90%CPU.

Okay, now I'm confused. Didn't the above poster say to disable Nautilus (whatever that is)? Then if you tried that, why do you say Nautilus was running at 90%? I'm sure I misunderstand what you are saying. So please do set me straight.

Thanks all.

---

### Post by Therion on 2008-01-28
> **BuntuFreak said:**
> Okay, now I'm confused. Didn't the above poster say to disable Nautilus (whatever that is)? Then if you tried that, why do you say Nautilus was running at 90%? I'm sure I misunderstand what you are saying. So please do set me straight.
Nautilus is the default file manager for Ubuntu; much like Windows Explorer is to Windows.  What I was explaining to the OP was that *certain functions* within Nautilus can be disabled in order to allow him to have (up to) four different wallpapers on his Compiz' Cube, should he wish to do so, since one of the things Nautilus does is draw the desktop (e.g. icons).  That fact was more implied, and it would be more accurate, I suppose, to say that using the solution outlined *would disable* certain functions in Nautilus, rather than making sound like you would need disable certain functions to get the solution to work.  I tried the solution outlined, but quickly confirmed how much I like having desktop icons.  

The memory useage of Nautilus, and the CPU useage-spike (90%) that the OP reports, I can't speak to as I don't know anything about that. 

Hope that helps to clarify things a little.

---

### Post by DaymItzJack on 2008-01-28
> **BuntuFreak said:**
> 
Okay, now I'm confused. Didn't the above poster say to disable Nautilus (whatever that is)? Then if you tried that, why do you say Nautilus was running at 90%? I'm sure I misunderstand what you are saying. So please do set me straight.

Thanks all.

You don't disable Nautilus, you disable "show_desktop" which is a preference in Nautilus.

---

### Post by BuntuFreak on 2008-01-29
That's it. I disabled "show desktop" on Nautilus. I don't particularly care to have a cluttered desktop. This solution works well for me after all.

How do I close this thread as [SOLVED]?

---

