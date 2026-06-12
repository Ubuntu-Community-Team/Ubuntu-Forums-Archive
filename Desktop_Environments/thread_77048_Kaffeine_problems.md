---
title: "Kaffeine problems"
date: 2005-10-16
forum: Desktop Environments
---

### Post by eMuNiX on 2005-10-16
I have a small problem with Kaffeine, in will only play files with Kaboodle, it crashes with any other engine.  Having looked through a few threads on here I tried to uninstall kaffeine-gstreamer but this wants to uninstall the kubuntu desktop, which can't be right :confused:  Noatun, RealPlayer and Xine all seem to play files fine.

---

### Post by Knome_fan on 2005-10-16
Did you try to install kaffeine-xine?
You don't have to uninstall kaffeine-gstreamer to use, just select it as the engine kaffeine uses (I think it's simply called kaffeine, for whatever reason).

---

### Post by CAE on 2005-10-16
[QUOTE=eMuNiX]I tried to uninstall kaffeine-gstreamer but this wants to uninstall the kubuntu desktop, which can't be right :confused:[/QUOTE]

Does anyone know what the deal with this is? Because this happened to me when I wasn't really paying too much attention to what was being removed and it completely stuffed my install. Is it a bug because surely we should be able to remove things like kaffeine-gstreamer on its own?

---

### Post by Knome_fan on 2005-10-16
Uhm, uninstalling kubuntu-desktop is absolutely no problem. It's just a meta package that depends on the things that constitute a default kubuntu install, so again, removing it won't cause any problem.

---

### Post by CAE on 2005-10-16
[QUOTE=Knome_fan]Uhm, uninstalling kubuntu-desktop is absolutely no problem. It's just a meta package that depends on the things that constitute a default kubuntu install, so again, removing it won't cause any problem.[/QUOTE]

Query: Have *you* actually *tried* yourself, with 5.10? Because, from what I recall, when I removed some completely unrelated package and kubuntu-desktop was removed as well, it also uninstalled the whole base system. In short, it was screwed. Yes, I know how the meta packages worked in Hoary. I know they were pretty much meaningless. But I'm sure there's something different in Breezy.

If you try it, don't blame me if it smokes your system, but that'll still prove my point.

---

### Post by Knome_fan on 2005-10-16
[QUOTE=CAE]Query: Have *you* actually *tried* yourself, with 5.10? Because, from what I recall, when I removed some completely unrelated package and kubuntu-desktop was removed as well, it also uninstalled the whole base system. In short, it was screwed. Yes, I know how the meta packages worked in Hoary. I know they were pretty much meaningless. But I'm sure there's something different in Breezy.

If you try it, don't blame me if it smokes your system, but that'll still prove my point.[/QUOTE]

I'm not in Kubuntu right now, but removing Ubuntu-desktop worked like a char--------------------





Just joking, it did only remove the meta package here and I'm sure it's the same with kubuntu-desktop. I'd guess that you also removed some vital package a lot of other packages depended on and that in turn kubuntu-desktop depended on these packages and was also removed.

---

### Post by CAE on 2005-10-16
[QUOTE=Knome_fan]I'm not in Kubuntu right now, but removing Ubuntu-desktop worked like a char--------------------





Just joking, it did only remove the meta package here and I'm sure it's the same with kubuntu-desktop. I'd guess that you also removed some vital package a lot of other packages depended on and that in turn kubuntu-desktop depended on these packages and was also removed.[/QUOTE]

I won't deny that's not a possibility. I can't actually, for the life of me, remember what it was that I attempted to remove, but I never previewed the changes. All I remember was I applied and watched in shock as things like 'Removing Konqueror...' scrolled past. I had to hard reset the machine because _everything_ was messed.

I'm really tempted to try again, but I just got comfortable with my setup. I wonder if anyone's feeling brave?

---

### Post by greatshape on 2005-10-16
[QUOTE=CAE]
I'm really tempted to try again, but I just got comfortable with my setup. I wonder if anyone's feeling brave?[/QUOTE]

Try this:

# dpkg -P --force-depends kaffeine-gstreamer

# apt-get install kaffeine-gstreamer

That'll do what you want ;-)
Regards, Steve

---

