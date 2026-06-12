---
title: "Compiz vs. GTK vs. Emerald"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by Therion on 2008-03-12
Can someone explain to me why I can't have Compiz running as my Window Manager AND have a fully implemented GTK theme when I have Emerald installed?

Emerald is NOT my chosen Window Decorator, yet it prevents GTK themes from decorating my window borders when I install one.  The ONLY way I can get the window borders from an installed GTK theme to apply, is to shut down Compiz.  As soon as Compiz is restarted, Emerald takes over window decoration *even though GTK is my chosen Window Decorator*.

It's driving me nuts.  I'm going to uninstall Emerald, which I am convinced will solve the problem, but WHY is this happening?  Why can't I have Compiz as my Window Manager and GTK for theme-ing and window decoration at the same time??

---

### Post by Zorael on 2008-03-12
Is gtk-window-decorator even Compiz compatible? I'm not sure.

What happens if you load Compiz, then load gtk-window-decorator afterwards, from a terminal?

```
$ compiz --replace &
$ gtk-window-decorator --replace &
```

---

### Post by FuturePilot on 2008-03-12
It's because the Compiz wrapper script is set to use Emerald by default if it is installed. However there is an easy way to override that.
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
and restart Compiz.

---

### Post by 6205 on 2008-03-12
> **Therion said:**
> Can someone explain to me why I can't have Compiz running as my Window Manager AND have a fully implemented GTK theme when I have Emerald installed?

Emerald is NOT my chosen Window Decorator, yet it prevents GTK themes from decorating my window borders when I install one.  The ONLY way I can get the window borders from an installed GTK theme to apply, is to shut down Compiz.  As soon as Compiz is restarted, Emerald takes over window decoration *even though GTK is my chosen Window Decorator*.

It's driving me nuts.  I'm going to uninstall Emerald, which I am convinced will solve the problem, but WHY is this happening?  Why can't I have Compiz as my Window Manager and GTK for theme-ing and window decoration at the same time??

Why why why....because of  Emerald.....uhmm.....Emerald is obsolete window decorator from Beryl ages, cca 1 year in the past. It's main purpose was to skin window borders instead of using those in default GTK theme. On other side, Compiz don't skin windows and instead of that is using default GTK Metacity skin/theme as always had...

I don't know why are you even installed old Emerald. Default Ubuntu Compiz is nice example of great, clean implementation of composite desktop, using default gtk theme and default gtk windows borders and everything without old, obsolete Xgl server...

My advice >>> Remove Emerald related packages and use default Ubuntu Compiz packages, nothing else. And without some xorg.conf hacks and other nonsense. Simply enable Visual Effects and you will have fully working Compiz with default gnome window theme. [http://www.thelinuxnewbie.com/images/appearance.jpg](http://www.thelinuxnewbie.com/images/appearance.jpg)

---

### Post by FuturePilot on 2008-03-12
> **6205 said:**
> Why why why....because of  Emerald.....uhmm.....Emerald is obsolete window decorator from Beryl ages, cca 1 year in the past. It's main purpose was to skin window borders instead of using those in default GTK theme. On other side, Compiz don't skin windows and instead of that is usig default GTK Metacity skin/theme as always had...

I don't know why are you even installed old Emerald. Default Ubuntu Compiz is nice example of great, clean implementation of composite desktop, using default gtk theme and default gtk windows borders and everything without old, obsolete Xgl server...

My advice >>> Remove Emerald related packages and use default Ubuntu Compiz packages, nothing else. And without some xorg.conf hacks and other nonsense. Simply enable Visual Effects and you will have fully working Compiz with default gnome window theme. [http://www.thelinuxnewbie.com/images/appearance.jpg](http://www.thelinuxnewbie.com/images/appearance.jpg)

Emerald is not obsolete. It's part of Compiz Fusion. If it was obsolete I don't think it would be in the repos anymore.

---

### Post by sloggerkhan on 2008-03-12
no offense, but even if emerald is 'obsolete' it's ages better than gtk, at least from an aesthetic and customization standpoint.

---

### Post by 6205 on 2008-03-12
Okay, if you like Emerald no problem, and same for Compiz Fusion. I don't need that extra candy like fire, water or other useless stuff. I like default simple ubuntu effects without Fusion extra plugins. I have even more desktops disabled, don't use cube or zoom, negative and other plugins...Just keep it simple, like in Vista, or it will be contra-productive.

---

### Post by Zorael on 2008-03-12
> **6205 said:**
> Okay, if you like Emerald no problem, and same for Compiz Fusion. I don't need that extra candy like fire, water or other useless stuff. I like default simple ubuntu effects without Fusion extra plugins. I have even more desktops disabled, don't use cube or zoom, negative and other plugins...Just keep it simple, like in Vista, or it will be contra-productive.
Obviously everyone doesn't share your opinion.

I find that multiple desktops are a great way of organizing your windows. The Expo plugin makes it very easy and intuitive to get an overview of those, as does the cube. Grouping and tabbing windows is something I do constantly. Et cetera.

So I don't see how they make things counter-productive.

---

### Post by 6205 on 2008-03-12
those are exceptions :)

---

### Post by Zorael on 2008-03-12
Indeed?

Granted, fire and water are more eyecandy than production boosts; fun to toy around with, and nice to look at, perhaps. Showing off Linux to l0sedows friends.

Consider, however, that the zoom and negative plugin can be of great use to people with impaired sight.


This is straying from the topic.

Yes, try either ways to start the decorator you want *after* Compiz has been evoked.

---

### Post by Therion on 2008-03-12
> **FuturePilot said:**
> It's because the Compiz wrapper script is set to use Emerald by default if it is installed. However there is an easy way to override that.
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
and restart Compiz.
Most excellent.  Thank you.  Quick question though... Would I need to stop Compiz before issuing that command in the Terminal, or does it matter?  You say in your post to REstart Compiz, so I'm assuming it doesn't matter.  Guess I'll find out!  Thanks again.

> **sloggerkhan said:**
> no offense, but even if emerald is 'obsolete' it's ages better than gtk, at least from an aesthetic and customization standpoint.
Agreed.  I appreciate the flexibility that Emerald adds, I'm just not using it, and it's interfering with what I want to do.  Can't argue having with more choices though!

> **6205 said:**
> I have even more desktops disabled, don't use cube or zoom, negative and other plugins...Just keep it simple, like in Vista, or it will be contra-productive.
Options, in my opinon, are always nice to have.  Even if I don't exercise them all, I still like having them.

Thanks for the input everyone.  I'm sure this little "cli" will get me where I want to go.

---

### Post by FuturePilot on 2008-03-12
> **Therion said:**
> Most excellent.  Thank you.  Quick question though... Would I need to stop Compiz before issuing that command in the Terminal, or does it matter?  You say in your post to REstart Compiz, so I'm assuming it doesn't matter.  Guess I'll find out!  Thanks again.


No it doesn't matter. ;)

---

