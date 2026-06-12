---
title: "Beryl Plugin Help"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by Romericus on 2007-06-10
Hello all, 

I have Beryl installed and am really enjoying it.  However, I want to put a different wallpaper on each side of the cube.  I read over at the beryl forums that you have to download the beryl-unsupported-plugins-0.2.1, which I did.  When I extracted the plugin, I just created a folder in my home folder for the files.  Should I put them somewhere else?  How do I install the plugin?

I'm about a week into using linux and so I still need the training wheels, though I have used the terminal quite a few times with success.

Thanks

---

### Post by starcraft.man on 2007-06-10
No no, thats the hard way. Unsupported plugins are in the repos. Please delete what you extracted, repos are always the way to go when you can.

```
sudo aptitude install beryl-plugins-unsupported beryl-plugins-unsupported-data
```

Then, they should be installed, the version in there is up to date I believe and supports this (its a viewport option in one of the plugins). I'm not sure if you have to restart to get them to take effect, should just add themselves live I think. I always install them all...

Info on how to use [plugins is found here]("http://wiki.beryl-project.org/wiki/Main_Page"), pick a topic in the beryl plugin list on right.

---

### Post by Romericus on 2007-06-10
Starcraft.man 

That worked and it installed the plugin, but the wallpaper manager is absent from the new settings, which makes me think it is the wrong plugin.  do you (or anyone else reading this thread) know for sure which plugin contains the wallpaper manager?

---

### Post by Romericus on 2007-06-10
following the advice posted here: [http://wiki.beryl-project.org/wiki/Wallpaper_Manager](http://wiki.beryl-project.org/wiki/Wallpaper_Manager), I typed "killall nautilus" in the terminal and now I have no desktops and no skydome (all black).  

Is there a "resurrect nautilus" command for the terminal?  I'd like to undo what I did.  

I'm giving up on the 4 wallpaper idea for the time being.  From what I've read, it's difficult to get this working with gnome anyway.  I just want to get my settings back to the way they were before I started tinkering with it.  

Maybe I have to uninstall the plugin, but I dont know exactly how to do that either....

any help?

---

### Post by andrewsomething on 2007-06-11
In order to have separate wallpapers on each side of the cube, install the unsupported plug-ins as suggested above or with synaptic. Next open the Beryl manager. There will be a tab labeled desktop background under general options. Check the box that says desktop manager supports viewports.

Or at least that works for me....

-Andrew

---

### Post by andrewsomething on 2007-06-11
I should also note that results may varry depending on what other option you are using. Beryl is still beta, and the unspported plug-ins are not stable enough to package with Beryl.

-Andrew

---

### Post by Romericus on 2007-06-11
Thanks for your help andrew.  

I'm not well-versed enough in linux, ubuntu or beryl to do too much tinkering, so I'm gonna leave the whole 4-Wallpaper thing alone.  But I've got a problem now.  I can move the cube fine and I can see one desktop image and both caps along with the skydome image.  I just need to know how to get the other 3 sides of the cube to show the wallpaper (it can be the same wallpaper, I dont care). 

I think the problem stems from when I typed 'killall nautilus' into the terminal.  Does anyone know how to fix this?

---

### Post by andrewsomething on 2007-06-11
Typing 'nautilus' into the terminal should restart it if it didn't restart on its own. Chances are it's a Beryl problem. Is 'desktop manager supports viewports' still checked? If so disable that. 

I tried to recreate your problem, but it didn't happen for me. Your best bet is to go through your Beryl preferences and try to put them back to before you changed things.

If you turn off Beryl and everything works fine, then your problem isn't with Nautilus. Playing with Beryl can be a lot of trial and error. Is there any thing else you changed?

I hope it works out for you....

-Andrew

---

### Post by lyceum on 2007-06-12
> **andrewsomething said:**
> In order to have separate wallpapers on each side of the cube, install the unsupported plug-ins as suggested above or with synaptic. Next open the Beryl manager. There will be a tab labeled desktop background under general options. Check the box that says desktop manager supports viewports.

Or at least that works for me....

-Andrew

I tried this and it took away my background on the other three desktops. Only the original desktop kept a background and the others just let you see the inside of the cube. It would not let me add new wallpapers. Just FYI that it will not work for everyone. But hey, it is beta.

:popcorn:

---

