---
title: "Classic gnome new &quot;features&quot; in 11.04"
date: 2011-05-02
forum: Desktop Environments
---

### Post by jnik1313 on 2011-05-02
There are some changes in the new gnome in 11.04 (I'm not talking about the "Unity" but about the "Ubuntu Classic" gnome).

While moving a window, if you touch the upper boundary of the screen, the window is maximized. Since there is already a shortcut for maximizing (double-click title), not to mention the button, why do we need this? I hope there is a way to disable this "feature".

Another useful feature is gone: In the task bar, in the window list, one used to be able to drag and move windows to change their order. This is something that was very useful and now it's gone.

---

### Post by ingeva on 2011-05-02
> **jnik1313 said:**
> While moving a window, if you touch the upper boundary of the screen, the window is maximized. Since there is already a shortcut for maximizing (double-click title), not to mention the button, why do we need this? I hope there is a way to disable this "feature".If you use the mouse to move the window, the mouse pointer is on the top window bar, and you can't touch the top of the screen at the same time. But I must have misunderstood.... 
However, if your window is maximized when you touch the top window bar, your mouse or other hardware must generate extra clicks. That happens to me sometimes, and it's very annoying but I don't know the cause. It happens even if I change mouse, but only on this computer (Dell Vostro 400).

> **jnik1313 said:**
> Another useful feature is gone: In the task bar, in the window list, one used to be able to drag and move windows to change their order. This is something that was very useful and now it's gone.I'm running 9.10 (going over to 11.04 soon now that the classic Gnome is available), but I have never seen this, and when trying I couldn't make it work. Besides, I don't see the need for that function.

---

### Post by jnik1313 on 2011-05-02
> **ingeva said:**
> If you use the mouse to move the window, the mouse pointer is on the top window bar, and you can't touch the top of the screen at the same time.

I mean touch the top with the window, not with the mouse cursor. It actually happens when you're nearing the top. It's definitely a feature, because when it activates, a "shadow" appears around the window and the more you close to the top, the more it grows. You can even move the mouse cursor a little bit after the window has reached the top, until the shadow grows to cover the whole screen. In all cases though, whether you're near or exactly at the top, the effect is the same - the window is maximized when you release the mouse button. To me personally it's very annoying.

> **ingeva said:**
> I'm running 9.10 (going over to 11.04 soon now that the classic Gnome is available), but I have never seen this, and when trying I couldn't make it work. Besides, I don't see the need for that function.

Not sure about 9, but it definitely was there in 10, I used it a lot.

---

### Post by Krytarik on 2011-05-02
> **jnik1313 said:**
> 
While moving a window, if you touch the upper boundary of the screen, the window is maximized. Since there is already a shortcut for maximizing (double-click title), not to mention the button, why do we need this? I hope there is a way to disable this "feature".

Disable Compiz' "Grid" plugin in "CompizConfig Settings Manager".
If you don't have CCSM already installed, "compizconfig-settings-manager" is in the official repos.

Greetings.

---

### Post by jnik1313 on 2011-05-02
> **Krytarik said:**
> Disable Compiz' "Grid" plugin in "CompizConfig Settings Manager".

Thank you, that worked!

I wonder if there is a gnome or compiz setting to enable dragging windows buttons in the window list.

---

### Post by ingeva on 2011-05-02
> **jnik1313 said:**
> I mean touch the top with the window,
Not sure about 9, but it definitely was there in 10, I used it a lot.

I see. Yes, I definitely misunderstood!
I hated the new interface of 11.04, so I wouldn't have used it enough to even notice. But I tried Kubuntu and Xubuntu and didn't like them better. Now I have re-installed 11.04 and checked out the classic menu (without effects) and it's the same as I've gotten used to, so I'll probably upgrade my primary system very soon.
Being able to change the UI by just logging in and out offers a better opportunity to check out and learn the new interface, and I will do so because some people are speaking highly of it, and I guess it's a question of being willing to try new things - which I am, unless it conflicts with my regular work plan.

I'm running 9.10 because I didn't get the 10.xx to work properly.

---

### Post by Krytarik on 2011-05-02
> **jnik1313 said:**
> 
I wonder if there is a gnome or compiz setting to enable dragging windows buttons in the window list.
Sorry that I didn't drop a note before, there is another thread where we noticed that those feature doesn't work anymore
[http://ubuntuforums.org/showthread.php?t=1743185](http://ubuntuforums.org/showthread.php?t=1743185)

So, it's either disabled or removed, fire up "gconf-editor" and check the available options in "/apps/panel/applets/window_list_screen0/prefs", most of the options will also be available in the applets "Properties" dialog, right-click left of the first task item therefore, usually the left edge.

But it's definitely not a Compiz setting.

---

### Post by jnik1313 on 2011-05-02
> **Krytarik said:**
> So, it's either disabled or removed, fire up "gconf-editor" and check the available options in "/apps/panel/applets/window_list_screen0/prefs"

There seems to be no setting for this in there. Well, since it's reported as a bug let's hope it will be fixed eventually. Thanks again!

---

### Post by Krytarik on 2011-05-02
> **jnik1313 said:**
> Well, since it's reported as a bug let's hope it will be fixed eventually.
Ah, I didn't check the bug report before, it's marked as a duplicate of this one:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/697358](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/697358)

There seems to be a conflict between Gnome-Panel and Compiz.

---

### Post by Krytarik on 2011-05-03
As a follow up about the "Grid" plugin, see here on how to disable just the 'Aero Snap' feature:
[http://ubuntuforums.org/showthread.php?p=10760518#post10760518](http://ubuntuforums.org/showthread.php?p=10760518#post10760518)

Greetings.

---

