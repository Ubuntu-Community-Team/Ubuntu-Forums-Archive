---
title: "GNOME 2: Alter panel behavior when screen rotated?"
date: 2011-11-15
forum: Desktop Environments
---

### Post by mrspacklecrisp on 2011-11-15
11.04 Natty Narwhal, Asus T101MT, Gnome 2 with no Unity.

I'm having an issue of icon economy when my tiny tablet netbook is rotated left. My gnome panel icons all mash up and the two menus I consider essential, the main menu and the logoff/shutdown menu, are pushed out and rendered unusable. There are lots of little gnome applets I like to use normally, but I only want maybe a couple to display when the screen is rotated. 

Is there any way I can alter the behavior of the gnome panel to prefer certain items to display when the screen is rotated?

I have considered replacement menus, unity-2d, etc, but I would prefer a simple alteration than to install something new to fix a little problem. Still, I'm open to suggestions.

---

### Post by mrspacklecrisp on 2011-11-16
Bumping once to try my luck again.

---

### Post by Copper Bezel on 2011-11-17
I'm really not sure what to suggest. I've used an Eee-Rotate type thing on my netbook in the past, but I had a wing panel and a dock at the time, no full panels. Gnome Panel isn't designed around having the screen size changing regularly, so it's really just lucky that it changes size at all. Making specific applets disappear when the screen rotated could be done, but it would mean scripting to change gconf keys and reload the panel. That's a lot more work, I'd think, than installing something else in its place.

You're right that the Unity 2D panel is smarter about it, by the way, but the global menu creates its own issues at 600 px:

[[img]http://dl.dropbox.com/u/17749392/Screenshots/20111115/menuthumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/20111115/menu.png)

---

### Post by mrspacklecrisp on 2011-11-17
> **Copper Bezel said:**
> I'm really not sure what to suggest. I've used an Eee-Rotate type thing on my netbook in the past, but I had a wing panel and a dock at the time, no full panels. Gnome Panel isn't designed around having the screen size changing regularly, so it's really just lucky that it changes size at all. Making specific applets disappear when the screen rotated could be done, but it would mean scripting to change gconf keys and reload the panel. That's a lot more work, I'd think, than installing something else in its place.

You're right that the Unity 2D panel is smarter about it, by the way, but the global menu creates its own issues at 600 px:

[[img]http://dl.dropbox.com/u/17749392/Screenshots/20111115/menuthumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/20111115/menu.png)
I think that programmers are stuck in "desktop mode" about these things. Unity and Gnome3 look like they belong on a tablet, not a desktop, but they're only supported by the desktop... Modern designs seem to lump all devices together, regardless of the varying functions computers now take.

I once had a system where a second, compact toolbar existed and I would use hide-arrows to switch them out, but that was pretty crude to me. Perhaps I'm asking too much. I was just thinking of that css "overflow" option where you could set it to simply show as much as it could before the rest ran off. If it did that, I would get my Applications, Places, and System and that would be enough (as it just occurred to me that logoff options are in System as well)

---

### Post by mrspacklecrisp on 2011-11-17
Huh, you know I may have found a couple solutions...

1. Disable "expand" and you'll see whatever can fit starting from the left.
2. Keep it as is and you'll see whatever can fit starting from the right.

Its behavior used to be a bit more erratic. Anyway, I suppose my little issue was solved.

---

### Post by Copper Bezel on 2011-11-17
[s]Yeah, I don't know, aside from removing some of those panel applets. Gnome panel isn't smart and CSSy (unlike Shell's panel); it's just an ordinary undecorated window with some specially-defined GTK widgets on, so there's very little you can control about how it handles scenarios like this.[/s]

Edit: Never mind, very cool. = ) I'm glad you found a solution.

On your other point, Unity isn't remotely ready for tablets (and Canonical at least acknowledges that it isn't) and I think they're banking on having higher resolution to work with when it is (particularly since Windows tablets will start at 768 px wide, not 600.) Part of the plan is to get an interface together that's usable either way so that it's possible to keep a consistent design across platforms when that happens, although Unity is designed, more than anything, toward conventional netbooks.

I'd be less critical of Shell in that sense - driver support might not be there yet, but the interface will be ready when it is, with lots of baked-in touch-centric features. Now that I've tried it, incidentally, Shell seems to respond really well to switching the screen orientation.  The panel bunches up appropriately, the search is rescaled, the Favorites bar is expanded and the workspace switcher is removed outright in favor of "flicking" on the background of the Overview.

---

### Post by mrspacklecrisp on 2011-11-17
> **Copper Bezel said:**
> [s]Yeah, I don't know, aside from removing some of those panel applets. Gnome panel isn't smart and CSSy (unlike Shell's panel); it's just an ordinary undecorated window with some specially-defined GTK widgets on, so there's very little you can control about how it handles scenarios like this.[/s]

Edit: Never mind, very cool. = ) I'm glad you found a solution.

On your other point, Unity isn't remotely ready for tablets (and Canonical at least acknowledges that it isn't) and I think they're banking on having higher resolution to work with when it is (particularly since Windows tablets will start at 768 px wide, not 600.) Part of the plan is to get an interface together that's usable either way so that it's possible to keep a consistent design across platforms when that happens, although Unity is designed, more than anything, toward conventional netbooks.

I'd be less critical of Shell in that sense - driver support might not be there yet, but the interface will be ready when it is, with lots of baked-in touch-centric features. Now that I've tried it, incidentally, Shell seems to respond really well to switching the screen orientation.  The panel bunches up appropriately, the search is rescaled, the Favorites bar is expanded and the workspace switcher is removed outright in favor of "flicking" on the background of the Overview.

Evidently I'm lying. Sometimes, disabling "expand" puts my top toolbar directly in the middle of my screen. I also appear to have removed my tasque and jupiter applets by accident. And I really don't prefer to put my toolbar backwards, because it just looks strange and the whole panel is meant to be left-to-right... Having the ubuntu logo in the middle of it, right next to some notifications and whatnot, and then my power icon is not at the corner but is to the right of my name and chat icon...

In any case, Gnome 3 is as you said something ripe for tablets and other smaller devices. I can't say whether or not it's more resource intensive in the long run though, and that's important. I know others with tablets and they aren't exactly packing powerful processors... and although Ubuntu is pretty awesome in the hands of an old, underpowered computer I think it needs some skimming if it will survive. That was the problem with Netbook Edition. It was just desktop Ubuntu with some *extra* stuff. I think Canonical would do well to consider an extremely baseline form of the OS and then have various forks for different purposes... Not just the desktop version with some extra packages or a different desktop environment.

Edit: You know, on second thought, I'm considering Canonical's approach in business/marketing terms and that's surely the wrong perspective.

---

### Post by Favux on 2011-11-17
When you're rotated in tablet mode you can make the panel and icons a little more touch friendly by enlarging them.
tablet
```
gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 42
```
laptop
```
gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 24
```
Not sure about the 24 default on your netvertible, but as an example.

If you like the effect you can then just integrate it into your rotation script.

---

### Post by Copper Bezel on 2011-11-17
Favux, that would actually make the problem of the panel being pushed off the edge *worse*.

But yeah, the reversed panel would be a mess. You could *maybe* use AWN, which *still* won't resize but can at least be reliably pinned to line up at at one edge or the other. It doesn't use the three-menu style, though - the closest menu to the classic Gnome one is just an icon for Applications and an icon for Places, no Settings - or many of the Gnome applets.

On your other point, Canonical certainly thinks of themselves or wants to present themselves as taking a business-marketing perspective. Someone just shared [_this article_](http://www.zdnet.com/blog/open-source/ubuntu-linux-heads-to-smartphones-tablets-and-smart-tvs/9834) in the Café today, and it explains a bit of their thinking towards the tablet market. I don't think they can really rebuild the OS from any kind of "baseline" with their resources, though. I imagine that in the longer term, they probably *are* intending to build more of the environment in-house, but right now, they're wholly dependent on Gnome, and resource consumtion is definitely an issue. 

That said, I think Ubuntu is trying to position itself to compete with Windows 8, not Android, for the kinds of hardware platforms that Windows 8 tablets will require, and the Gnome 3 suite in stack is, if you ignore the window manager, at least, not any [i]heavier[i] than Gnome 2. But as you say, the original Netbook Edition doesn't inspire confidence, in any case, to see Canonical specifically targeting low-end machines with a heavier UI.

Architecturally, though, I don't know that there would be an advantage to forking the OS as a whole. The DE and enduser applications consume most of the resoruces, and Linux is modular, after all, so the core OS doesn't really need to change between platforms beyond ARM / Intel issues; the "baseline" system is the one that already exists in the server edition.

---

### Post by Favux on 2011-11-17
Hi Copper Bezel,

You're correct of course.  But practically speaking with a tablet PC/netvertible you need to trim the number of icons to what will fit in portrait orientation.  And you need things bigger if you want to use touch.

Cairo/Glx dock now resizes on rotation.  No longer any need to kill it and restart it in your rotation script.  You may be able to move some of your stuff to it.  It can be used as a bottom or a side panel.

---

### Post by Copper Bezel on 2011-11-17
Oh, nice. That would be the best option, then. Of course, if he's on 11.04, it might not be applicable there (and as I said, under 11.10, you'd probably want to use Shell, anyway.)

Edit: In any case, good point on the touchability, but if he's using it now, it can't be too much a problem.

Not directly relevant, but with Shell, I like the abbreviated username. = ) Overview looks, admittedly, weird.

[[img]http://dl.dropbox.com/u/17749392/Screenshots/20111115/flippedthumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/20111115/flipped.png)

---

