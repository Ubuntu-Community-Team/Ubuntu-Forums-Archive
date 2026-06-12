---
title: "icon's size in desktop"
date: 2005-10-13
forum: Desktop Environments
---

### Post by tokland on 2005-10-13
does anyone know a way to have all the icons in the desktop with the same size? the destkop is usually a completely mess if you don't stretch them manually... it there an automatic way to to this??

thanks very much!
tokland

---

### Post by karuptdata on 2005-10-13
hmm try this go to Preferences--->File Management and you can change the default desktop icon view in there..hope this help!

---

### Post by tokland on 2005-10-13
[QUOTE=karuptdata]hmm try this go to Preferences--->File Management and you can change the default desktop icon view in there..hope this help![/QUOTE]

Nops, that changes the size of some of the icons (My computer, the thrash, and many other) but some remain the same. XMMS, for example, has by default an awfully little icon. And firefox a big one...

thanks

---

### Post by KingBahamut on 2005-10-13
You can rclick on the icon and select stretch to change the size of a single icon.

---

### Post by taavi on 2005-10-13
[QUOTE=KingBahamut]You can rclick on the icon and select stretch to change the size of a single icon.[/QUOTE]He meant how could he apply one size to all of the icons on the desktop. Like in MS Windows (Icon Size) or something like that.

---

### Post by tokland on 2005-10-13
[QUOTE=taavi]He meant how could he apply one size to all of the icons on the desktop. Like in MS Windows (Icon Size) or something like that.[/QUOTE]

Yes, I didn't want to say it that way, but something similar to Window$'s icons is what I am looking for. Stretching them is a hack, since a visual and individual adjustment can never be a useful option.

In fact, I could do a script to do this task (get desktop icons, copy them to a  new directory, change the size and modify the launcher to link to the new icon), but I think there SHOULD be an automatic way... perhaps this a question for a Gnome forum, that's not specifically an Ubuntu issue... 

thanks

---

### Post by eko291 on 2005-10-13
I would love to know the answer to this.  I run at a fairly high resolution and like things small.  The large desktop icons are just out of place on my desktop.

---

### Post by tokland on 2005-10-13
[QUOTE=eko291]I would love to know the answer to this.  I run at a fairly high resolution and like things small.  The large desktop icons are just out of place on my desktop.[/QUOTE]

Oh, thanks, I thought that I was the only one that wanted this feature!

If someone is interested I have made a script that automatically resizes all icons (keeping a copy of the original ones). A terribly ugly hack, but works! 

tokland

---

### Post by Joe Jarvis on 2005-10-14
[QUOTE=tokland]does anyone know a way to have all the icons in the desktop with the same size?[/QUOTE]

System Tools > Configuration Editor
apps > nautilus > icon_view
Change default_zoom_level from "standard" to "large" or "larger"

Let us know if this accomplishes what you want.

---

### Post by davmac on 2005-10-16
I think rather than "large" or "larger", it might be "smaller" he is after.

You can also fire up Nautilus, Edit -> Preferences. Click the "preview" tab set the previews to Never, Click the "views" tab and for icons view set the default zoom level to 50%.

I don't think it is the total answer, but, like you I like to run a "compact" desktop and it should get you someway there.

HTH,

Dave Mac

---

### Post by tokland on 2005-10-16
[QUOTE=Joe Jarvis]System Tools > Configuration Editor
apps > nautilus > icon_view
Change default_zoom_level from "standard" to "large" or "larger"

Let us know if this accomplishes what you want.[/QUOTE]

Not really, nautilus configuration through "Configuration Editor" does exactly the same that changing it in the "Preferences -> File administration -> Icon view", the only difference is the way you write it:

100% = normal
75% = small
50% = smaller 
...

the thing is that this option works perfectly, it scales the icon the selected percentatge, but the problem is that not every icon has the same original size! some are 48x48 (which is the normal), but other 64x64, or 16x16. The scale applies to the original icon size, that's why the final icons are not the same size.

I think it should be a entry (at least on the desktop) to indicate if you want to normalize icon's size before displaying...

---

### Post by bvc on 2005-10-16
Yes, well, this is what you call a bad icon themer. If an icon is made or included, and there is more than one size for one icon (for instance ...apps) then that must be specified in the index.theme file, which means all app icons included must be available in all the represented sizes. If not, you end up with an inconsistant Desktop.

---

