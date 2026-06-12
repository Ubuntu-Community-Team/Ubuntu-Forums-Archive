---
title: "lost gnome desktop- 6.06LTS"
date: 2007-02-16
forum: Desktop Environments
---

### Post by propadog on 2007-02-16
Hi,

I've totally lost my gnome desktop. I'm running an up to date 6.06LTS, Gateway 5300 laptop, up to now hasn't missed a beat.

On load, I get the gnome splash which gets to loading metacity (i.e. first operation), and that's it. Splash disappears, background colour, that's it. No wallpaper, no taskbars, etc.

Loading failsafe gnome works perfectly, except for a dialog advisig that it's not runing the startup scripts. I end up with my desktop but no power management (which is no great drama. Everything appears to be working fine.

OK, where do I look or how do I create a log so I can see where it's falling over? Alternately, are there a set of files I can overwrite my gnome setups with?

Thnx.

---

### Post by shareMenaPeace on 2007-02-16
Try open a terminal and run
```

killall gnome-panel
```

---

### Post by propadog on 2007-02-16
> **shareMenaPeace said:**
> Try open a terminal and run
```

killall gnome-panel
```

```

gnome-panel: no process killed

```
while the offending X session was active.

It ain't loading by the look of it.

:confused:

---

### Post by Touch.Code on 2007-02-16
You may need to install gnome again. Or KDE, so that you can move around in the real mode.

---

### Post by propadog on 2007-02-16
> **Touch.Code said:**
> You may need to install gnome again. Or KDE, so that you can move around in the real mode.

](*,)

Let's see. Let's work through this logically.

Gnome works in failsafe gnome mode perfectly well. It also works for the other user on the laptop (i.e. root- I've been using linux since the pre 1.x days) perfectly well. I've never seen this problem before.

So, based on the information we already have, gnome works very well. There appears to be no problem with the gnome binaries. 

Do we agree? Good. 

So why would I want to reinistall it? Oh, to fix a screwed up setting in a text file for one user. But when I reinstall gnome, it's going to keep my settings because it's not going to overwrite the .gnome* files and directories in my home directory. So reinstalling gnome is actually not going to fix a damn thing.

Oh, unless I delete my home directory and the .gnome* files, which is something we all aspire to doing.

Hmmm.... Now I think of it, I don't think that what you have said is going to help at all. Think about this information logically. Do you think that it's a good idea?

And based on this, I don't think I trust your recomendation to move to kde either. Need I explain why? Apart from that if I wanted to use KDE I would be using KUbuntu, and I'm not. Or that I'm really not too sure what "Or KDE, so that you can move around in the real mode" means in english.

I suspect it is something to do with the startup programs because gnome in failsafe mode doesn't run them. So, please go back and revisit the question, which was which log covers gnome startups so I can see what is failing so I can fix its conf file (or equiv.) and we'll all pretend you didn't say any of that. OK?

---

### Post by propadog on 2007-02-16
bump

---

### Post by cblanquer on 2007-02-18
Same kind of problem under 6.10, 
Failsafe mode runs ok, other users run ok but my default access is messed up with no upper- down- panel bars and no windows controls nor ability to move them.

Just after setting up "ati" driver, installing "compiz" which worked fine.
Then I tired to ensure the 2nd user could use also "compiz" stuff and coming back to my userid everything got unusable.
Up till now I have not found any solution, and I do not want to give up as and reinstall, there should be an easy solution.

---

