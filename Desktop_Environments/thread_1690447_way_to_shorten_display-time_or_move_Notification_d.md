---
title: "way to shorten display-time or move Notification dialog box?"
date: 2011-02-18
forum: Desktop Environments
---

### Post by nrundy on 2011-02-18
Notifications that popup in Ubuntu (e.g., for downloading items in firefox or Network configuration stuff) display a rectangular black box in the upper right corner of my Desktop. It often covers up items I need to access like logout items or links to my Account etc in a webpage I'm in. I often find myself having to wait for the Ubuntu dialog box to disappear before I can access whatever it is covering up.

Is there a way to make these dialog boxes appear in the LOWER right corner instead? Also is there a way to shorten the amount of time that these notifications display before disappearing?

---

### Post by mikewhatever on 2011-02-18
Did you know that if you move the cursor over the notification rectangle, it disappears?

---

### Post by nrundy on 2011-02-18
I did this several times. I've never had it disappear. One time I positioned the cursor directly over the rectangle so that when it disappeared the cursor was where I needed it to click the link I needed. I still had to wait several seconds.

---

### Post by Krytarik on 2011-02-18
> **nrundy said:**
> I did this several times. I've never had it disappear. One time I positioned the cursor directly over the rectangle so that when it disappeared the cursor was where I needed it to click the link I needed. I still had to wait several seconds.
That's curious. It also "dimms" at my machine, and I can click through it.

However, if you want to generally change its settings and position, see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10115367](http://ubuntuforums.org/showthread.php?p=10115367)

It refers to this article: [http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

Greetings.

---

### Post by nrundy on 2011-02-20
Hey, thanks Krytarik :)

didn't know you were so talented :)

---

### Post by Krytarik on 2011-02-20
> **nrundy said:**
> Hey, thanks Krytarik :)

didn't know you were so talented :)
Heeyh!! ;) 
Did you manage to install the script, and have the launcher in your menu?

You will need to update the menu item cache with those commands, I have a launcher for them too ;):
```
sudo rm /usr/share/applications/desktop.*.cache
sudo sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"

```

---

### Post by nrundy on 2011-02-25
The notification alerts in Gnome-shell (gnome 3) are really cool. They come up at the bottom middle of the screen. Apparently Gnome did research on where these notifications would be best placed. I think they did their homework well. I prefer it over the Ubuntu right-corner method.

---

### Post by Krytarik on 2011-02-25
Middle-bottom is a bit too disturbing for me. Actually I keep on switching between right-bottom and right-upper (usually right-bottom). Depends also on if I run Smplayer or Vagalume in right-upper. ;-)

---

### Post by nrundy on 2011-02-25
> **Krytarik said:**
> Middle-bottom is a bit too disturbing for me. 

You mean it disturbs your focus on what you're working on?

I'm really excited to try out Unity and Gnome-shell. I think it's neat that we can try different desktops and see the advantages of each :)

---

### Post by Krytarik on 2011-02-25
> **nrundy said:**
> You mean it disturbs your focus on what you're working on?
Yeah, of course.
> **nrundy said:**
> I'm really excited to try out Unity and Gnome-shell. I think it's neat that we can try different desktops and see the advantages of each :)
Did you try both of each then? I'm somehow keen to install/try Unity. Are there major advantages in Gnome3 compared to the current version (I mean in user terms, not in promo terms)?

---

### Post by nrundy on 2011-02-26
> **Krytarik said:**
> 
Did you try both of each then? I'm somehow keen to install/try Unity.

I'm real excited to try Unity too. I have tried to install or run UNE off Live CD on four computers. It would not run on any of them. I got it sort of working on one of them but it was glitchy and I couldn't try it out for all intensive purposes. To be frank this kinda concerns me for the eventual release. Compiz is not as hardware friendly as Mutter as I understand it. I'm not really expecting much from Unity until it matures somewhat. I don't think this will happen until the 12.04 release. I think we'll have to wait until then to get a no-bs assessment of Unity's potential.

> **Krytarik said:**
> 
Are there major advantages in Gnome3 compared to the current version (I  mean in user terms, not in promo terms)?

Yes, there are major advantages in user terms. I will drop Gnome 2x. Gnome 3x is more in tune with how I would design a desktop if I was making one just for myself. It's a major improvement over 2x IMHO.

---

### Post by Krytarik on 2011-02-26
> **nrundy said:**
> I'm real excited to try Unity too. I have tried to install or run UNE off Live CD on four computers. It would not run on any of them. I got it sort of working on one of them but it was glitchy and I couldn't try it out for all intensive purposes. To be frank this kinda concerns me for the eventual release. Compiz is not as hardware friendly as Mutter as I understand it. I'm not really expecting much from Unity until it matures somewhat. I don't think this will happen until the 12.04 release. I think we'll have to wait until then to get a no-bs assessment of Unity's potential.

In fact the current releases/betas of UNE are based on Mutter, since Canonical only more recently decided to use Compiz as default window manager in future releases. But UNE depends hardware-accelerated video. So you have to install the proper driver before you log in to the Netbook Edition, or at least you only see something after doing so. ;-)
And I do also believe that the users the next one or two releases will not be the happiest ones. ;-)

---

