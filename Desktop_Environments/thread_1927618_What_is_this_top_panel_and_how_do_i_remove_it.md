---
title: "What is this top panel and how do i remove it?"
date: 2012-02-18
forum: Desktop Environments
---

### Post by Mr Coffee on 2012-02-18
No idea what happened, but just made a recent update and restarted my computer. Now i have this on my top panel in Gnome Shell. 

[IMG][/IMG]

Although i've got a transparent panel, using any other themes, particularly dark ones just hides it rather than make it go away. No idea if it was something that updated, a setting i changed or what. Would appreciate help :)

---

### Post by Copper Bezel on 2012-02-18
I guess this is a problem again - this bug had been fixed. It's a Nautilus issue. (What you're seeing is actually the menubar of the Nautilus window that draws the background. Obviously, it's not supposed to be there.) It'll go away if you remove the appmenu packages: 

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```

Of course, that'll break Unity. The other option is to open Advanced Settings (Gnome Tweak Tool) and disable "Have file manager handle the desktop," but you'll lose support for desktop icons.

---

### Post by linfidel on 2012-02-18
I think I'm seeing that too, using gnome classic mode - it's a blank panel on my 2nd monitor.

I'm wondering if you have any idea whether this would be the cause of conky suddenly not working.  I haven't made any changes to it, but it stopped displaying today.  

Running it from a terminal, it starts up normally, then starts spewing out:  
"[FONT=Courier New]Conky: llua_do_call: function conky_main_bars execution failed: attempt to call a nil value[/FONT]"  repeatedly.

---

### Post by linfidel on 2012-02-18
Well, to answer my own question...  apparently so.  :)

I removed the appmenu as suggested, and conky worked normally.  Reinstalled it, it stopped working.  Removed again, and it works.  I think I'll quit now.

Now, if only I can remember that I did this if I ever go back to Unity, although I'm pretty happy right now using AWN with Gnome classic.

---

### Post by Mr Coffee on 2012-02-18
> **Copper Bezel said:**
> I guess this is a problem again - this bug had been fixed. It's a Nautilus issue. (What you're seeing is actually the menubar of the Nautilus window that draws the background. Obviously, it's not supposed to be there.) It'll go away if you remove the appmenu packages: 

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```

Of course, that'll break Unity. The other option is to open Advanced Settings (Gnome Tweak Tool) and disable "Have file manager handle the desktop," but you'll lose support for desktop icons.

Don't use Unity at all, but if the need does come i'll reinstall. But yes, did the command, logged out and in then voila, gone just like that.
Yer a wizard, Cooper!

Thanks. Solved.

---

### Post by Copper Bezel on 2012-02-18
Very cool! Just mark the thread as Solved, Thread Tools in the upper right. Thanks!

---

