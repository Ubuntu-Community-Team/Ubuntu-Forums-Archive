---
title: "Gnome: Single click in file chooser dialog"
date: 2009-08-11
forum: Desktop Environments
---

### Post by emakarov on 2009-08-11
Hello,

Nautilus obviously has a way of choosing whether folders and files are opened using a double or a single click (Edit | Preferences | Behavior). I find it strange, though, that the file chooser dialog (Open, Save, etc.) uses (or can use) a single click to open a bookmarked folder on the left (under Places), but requires a double click on the right (under Name).

There was a [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=511269") opened for Gnome, but the developer "decided not to implement this bug." Personally, I don't fully understand the reason given there. Do you think this issue should be reconsidered?

Thank you,
Evgeny

---

### Post by AliTabuger7 on 2009-08-11
Interesting observation.

I didn't find it any more confusing than icons on the gnome-panel being single click, while desktop icons are double click.

There are a couple advantages I see to making the bookmarks and media double click:
[LIST]
[*]The ability to rename bookmarks.
[*]Reduce accidental clicks.
[/LIST]

Of course, double clicks are slower.

Perhaps if you find this confusing, you should instead change the navigation at the right to single click?

I think it would at least be fine to include it as an option in the preferences dialogue.

---

### Post by emakarov on 2009-08-11
> **AliTabuger7 said:**
> I didn't find it any more confusing than icons on the gnome-panel being single click, while desktop icons are double click.
Fortunately, desktop icons obey the preference of the Nautilus, so they can be made single-click as well.

There is a problem with just selecting a desktop icon when single clicks are on. I can draw a region with the mouse, or I can right-click on the icon and then click away. It would make sense to adopt the Windows behavior where an icon is selected if the mouse hovers over it for some time. Or whatever KDE behavior is, I don't have it right now.

> **AliTabuger7 said:**
> Perhaps if you find this confusing, you should instead change the navigation at the right to single click?
Yes, that's what I would like to do but currently can't.

> **AliTabuger7 said:**
> I think it would at least be fine to include it as an option in the preferences dialogue.Of the global Gnome preferences, not just Nautilus.

Since KDE has this option, it's not unreasonable.

---

### Post by AliTabuger7 on 2009-08-11
Simply because it is an option in KDE, that is really not a good indicator of whether the option will be available in gnome.

KDE is designed to be very configurable, where gnome sometimes prefers to hide things in favor of simplicity. Many people disagree with this, and the line is always being refined between simplicity and flexibility.

I don't disagree with your idea, but perhaps you should use KDE if this option you want is in KDE. Why wait?

I tend to like more flexibility and configuration available for my system, so I would like this feature, but I have my doubts that it would ever make it into gnome.

---

### Post by AliTabuger7 on 2009-08-11
I forgot to mention that, in Ubuntu gnome, the desktop is actually nautlius.

---

