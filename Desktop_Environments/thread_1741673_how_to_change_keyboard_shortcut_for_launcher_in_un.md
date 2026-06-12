---
title: "how to change keyboard shortcut for launcher in unity"
date: 2011-04-28
forum: Desktop Environments
---

### Post by LonelyStar on 2011-04-28
Hey,

Just upgraded to ubuntu 11.04. Yeah.

Do not know yet if unity is something for me, but I will find out :).

I tried to change the keyboard shortcut for the launcher (default Alt-F2).
I did this by changing it in ccsm, under "unity plugin"-"Key to execute a command". Did not help.

How can I change it?
Thanks!
Nathan

---

### Post by KegHead on 2011-04-28
Hi!

sytem...preferences...keyboard

KegHead

---

### Post by vanadium on 2011-04-28
It is under "keyboard Shortcuts" (Windows key, search "Key")

---

### Post by LonelyStar on 2011-04-28
Hey,

Thanks for the replies. Unfortantly I can not find it.
Under "keyboard Shortcuts" in the system preferences, Nothing is bound to Alt+F2. And I can not find an action that starts the launcher.

What would the name of that action be?

Thanks!
Nathan

---

### Post by vanadium on 2011-04-28
For me, there is an action "Show the panel's "Run Application" dialog box" bound to Alt+F2 and an action "Show the panel's main menu" under Alt+F1 in the "Keyboard Shortcuts" dialog, under the "Desktop" category.

---

### Post by LonelyStar on 2011-04-28
> **vanadium said:**
> For me, there is an action "Show the panel's "Run Application" dialog box" bound to Alt+F2 and an action "Show the panel's main menu" under Alt+F1 in the "Keyboard Shortcuts" dialog, under the "Desktop" category.

Hey,

Yes I have those too, they are set to disabled. If I set them to something else (for example Mod4-x), the set keyboard shortcut (Mod4-x) has no effect, but Alt-F2 still triggers the run dialog.

---

### Post by LonelyStar on 2011-04-30
> **LonelyStar said:**
> Hey,

Yes I have those too, they are set to disabled. If I set them to something else (for example Mod4-x), the set keyboard shortcut (Mod4-x) has no effect, but Alt-F2 still triggers the run dialog.

I tried it on a different computer, same problem. Can anyone confirm this or is it just me?

---

### Post by vanadium on 2011-05-01
Indeed, it is not as simple as I thought. I can change the keys in "Desktop - Shortcuts" but the change has no effect.

Probably it are the settings in Compiz that determine this. In CompizConfig Settings manager (not installed by default - you may need to install it first), look for the Compiz plugin. The shortcuts are configured on the "Behaviour" tab.

---

### Post by LonelyStar on 2011-05-02
> **vanadium said:**
> Indeed, it is not as simple as I thought. I can change the keys in "Desktop - Shortcuts" but the change has no effect.

Probably it are the settings in Compiz that determine this. In CompizConfig Settings manager (not installed by default - you may need to install it first), look for the Compiz plugin. The shortcuts are configured on the "Behaviour" tab.

You mean the "unity" plugin? I changed the keys "Key to put keyboard-focus on launcher" and "Key to execute a command" to something else, but I still get the launcher when I press Alt-F2 :(.

---

### Post by vanadium on 2011-05-02
Did you try it? I did and I am about to reset my Compiz settings. There is also the Gnome compatibility plugin where this key is set.

---

### Post by LonelyStar on 2011-05-02
> **vanadium said:**
> Did you try it? I did and I am about to reset my Compiz settings. There is also the Gnome compatibility plugin where this key is set.

Did I try what?
I changed the key settings every where I could find, that is:
- in System Settings -> Keyboard Shortcut
- in the Ubuntu Unity plugin of compiz
- In the gnome-compatibility plugin of compiz

And still, when I press Alt-F2, I get the launcher of unity.

It is extremely annoying, because I am used to have my workspaces in Alt-[F1-F9].

---

### Post by vanadium on 2011-05-02
My attempt in changing these shortcuts resulted in a borked Unity (the only wallpaper phenomenon). Strange this does not work in any of these places for you.

---

### Post by Tony512 on 2011-12-20
Is this post too old to revive? Is there an answer in the forums? I was unable to find an answer as to how to change the keyboard shortcut than launches unity. Is there an open ticket for this?
My Keyboard Shortcuts does not show any way for changing the command to open the unity launcher.

Thanks in advance
Tony

---

### Post by youssef.barhomi on 2012-09-08
Actually, it is pretty easy to fix this:

[http://www.howtogeek.com/101006/how-to-tweak-unity-on-ubuntu-with-the-compizconfig-settings-manager/](http://www.howtogeek.com/101006/how-to-tweak-unity-on-ubuntu-with-the-compizconfig-settings-manager/)

Hope it helps!

---

