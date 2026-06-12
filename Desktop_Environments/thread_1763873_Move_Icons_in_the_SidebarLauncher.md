---
title: "Move Icons in the Sidebar/Launcher"
date: 2011-05-21
forum: Desktop Environments
---

### Post by novafluxx on 2011-05-21
How can I do this. I'm trying to get my feet wet here with Unity and just seem to stumble at every turn.

I got rid of all of those pointless LibreOffice Icons and replaced it with the main LibreOffice.

Now I'd like to know how to move them around, rearrange them I mean.

---

### Post by NormanFLinux on 2011-05-21
You can tug on them in the launcher to move the icons to desired positions but if you have a lot of icons to rearrange, its time to fire up gconf-editor, go to desktop, unity laucher, favorites, click on the favorite key and then move the icons in the menu to where you want them. When you are done, logout and login to see your final launcher configuration take effect.

---

### Post by novafluxx on 2011-05-22
I've tried clicking and dragging on them, it pulls the entire list of icon's down/up, not just that single icon.

I can check out gconf I guess.

---

### Post by novafluxx on 2011-05-22
> **NormanFLinux said:**
> You can tug on them in the launcher to move the icons to desired positions but if you have a lot of icons to rearrange, its time to fire up gconf-editor, go to desktop, unity laucher, favorites, click on the favorite key and then move the icons in the menu to where you want them. When you are done, logout and login to see your final launcher configuration take effect.

I don't see unity launcher under desktop in gconf-editor.

---

### Post by Frogs Hair on 2011-05-22
There is a another configuration tool for Unity if you would like to add it .```
sudo apt-get install dconf-tools
```

---

### Post by Krytarik on 2011-05-24
To reposition a launcher icon, you need to drag it to the right, out of the Launcher, and then back in again, to the position where you want to have it.

Greetings.

---

### Post by novafluxx on 2011-05-24
> **Krytarik said:**
> To reposition a launcher icon, you need to drag it to the right, out of the Launcher, and then back in again, to the position where you want to have it.

Greetings.

This! Thank you! Everyone's telling me to install some tool and edit something!

How hard is it to tell what you just told me! lol

Kudos to you, I appreciate it.

---

### Post by Krytarik on 2011-05-24
> **novafluxx said:**
> This! Thank you! Everyone's telling me to install some tool and edit something!

How hard is it to tell what you just told me! lol

LOL:D That's what I thought, too.

---

### Post by shakma on 2011-07-01
> **NormanFLinux said:**
> it's time to fire up gconf-editor, go to desktop, unity laucher, favorites, click on the favorite key and then move the icons in the menu to where you want them. When you are done, logout and login to see your final launcher configuration take effect.

Just wanted to give a big thanks for this!  This seems to be the only way to rearrange the 2d Unity launcher.  It works beautifully, btw! :guitar:

Peace.

---

### Post by cheryljosie on 2012-10-01
:confused: I had a different experience than you did. I came here looking for help but your suggestion to drag to the right did not work for me. However it did give me incentive to experiment until I discovered the true behaviour.

If I just click on an icon in the launcher and immediately tug on it up and down with the mouse pointer, I drag the whole rack of icons in the launcher up and down, auto-scroll fashion (I have more icons than will show on one screen height and need to move them up and down to access all of them). It responds the same way as if I move the mouse wheel up and down with the pointer over the launcher.

If I try do drag the icon 'out' of the launcher (to the right), then as soon as the mouse pointer crosses the boundary and leaves the launcher bar it lets go entirely and drops the icon back into place.

However, if I click on an icon in the launcher and keep the mouse pointer steady, holding the left button down on the mouse, and wait half a second (if the processor is not busy, that is, because if the processor is busy it can take several seconds to respond), the icon I am clicked on will 'pop out' of the launcher all by itself, or in other words it drops downward slightly to indicate it has come loose from its prior position from the 'pressure' of the mouse button pushing on it. :)

Once the icon is loose, then when I drag the mouse up and down, I also drag just the one icon up and down to change the ordering of the icons, instead of dragging the whole rack of icons as a group. Now the one icon will move to the relative position I want within the launcher.

The launcher lets me move the mouse pointer a little side to side after clicking and holding, as long as I do not move the pointer out of the launcher entirely. The launcher lets me move the mouse pointer very slightly up and down  after clicking and holding, as long as I do not move the pointer more than a tiny bit up and down.

I presume that you clicked on the launcher icon, waited half a second while 'dragging it to the right' slightly (but not out of the launcher, and not very far up and down). That gives the same result as clicking on the launcher icon and waiting.

It is not necessary to move the mouse pointer at all in order to pop the icon loose. In fact it is much easier to just click and wait because the vertical axis is highly sensitive to movement and even the horizontal axis will not tolerate moving the mouse pointer out of the launcher.

You probably just got lucky and managed to drag exactly horizontally a little bit, with almost no vertical movement, and without leaving the launcher.

It is much easier to just click and wait, plus it does not have a quirky frustrating 'intermittent failure' feel to it when you accidentally drag too far up or down while waiting for the icon to pop free and cause the whole rack of icons to shift up and down with the pointer, or when you lose hold of the icon entirely because you accidentally drag the mouse pointer all the way out of the launcher.

I am sure this launcher behaviour is documented somewhere. It only took me a whole year plus in order to figure it out by trial and error. If only it were this easy to configure NFS!

:lolflag:

---

### Post by sffvba[e0rt on 2012-10-01
***Old** thread closed.*


404

---

