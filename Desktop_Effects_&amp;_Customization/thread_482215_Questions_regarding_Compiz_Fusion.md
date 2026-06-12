---
title: "Questions regarding Compiz Fusion"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by rishabh on 2007-06-23
I just installed the new Compiz Fusion from Trevino's repos. So far I've been a Beryl user, and I've been used to the "beryl-manager" which sits in the system tray. It's very useful, you can change back to metacity easily and quit Beryl whenever needed. I haven't yet found a way to do this in Compiz Fusion. Is there a way or is it meant to be 'unstoppable'? ;)

Also, I notice that the window thickness and the inter-window spacing is not there. Is there anyway to get them back?

Thanks.

---

### Post by jpeddicord on 2007-06-25
If you are using the default GTK+ window decorator, the borders and spacing should still be there.

I don't think there currently is a tray client to change managers. There are two commands you can use to switch between the two. Run these by the Alt+F2 dialog, not the terminal, otherwise you will need to control-c them.

To start Metacity & kill Compiz:
```
metacity --replace
```
and vice versa:
```
compiz --replace
```

Jacob

---

### Post by Depressed Man on 2007-06-25
> **rishabh said:**
> I just installed the new Compiz Fusion from Trevino's repos. So far I've been a Beryl user, and I've been used to the "beryl-manager" which sits in the system tray. It's very useful, you can change back to metacity easily and quit Beryl whenever needed. I haven't yet found a way to do this in Compiz Fusion. Is there a way or is it meant to be 'unstoppable'? ;)

Also, I notice that the window thickness and the inter-window spacing is not there. Is there anyway to get them back?

Thanks.

To change plugin preferences and the like you can go to system > preferences > CompizConfig (etc....)

However, there&#347; no way to change managers or fallbacks that I know. Though you could use replace.. like compiz --replace and metacity --replace

to switch as necessary.

---

### Post by Inxsible on 2007-08-03
oh you can surely have fallback window managers. To set these up go to 
System->Preferences->CompizConfig Setting Manager. Click on Utility and check Crash Handler. Put in the commands for the alternate window manager that you want, which can be regular metacity or beryl. 

This option was also available in Beryl. As for the tray icon for compiz fusion,
see this link

[http://ubuntuforums.org/showthread.php?t=481814](http://ubuntuforums.org/showthread.php?t=481814)

---

### Post by psyopper on 2007-08-04
3d Windows is still there, it's just not in the main plugins...

```

sudo aptitude update
sudo aptitude compiz-fusion-plugins-unsupported compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial

```

I'm not sure which of the three it's in, but it's in there. 

There is also "fusion-icon" as the Compiz-Fusion replacement for Beryl-Manager.  I didn't see it in Trevino's repository but you can try adding it to the command above to see if I just missed it, otherwise you can find it in [Vorian's repositories]("http://debs.vorian.org").

---

