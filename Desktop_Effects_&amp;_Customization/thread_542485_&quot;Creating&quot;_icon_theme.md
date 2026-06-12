---
title: "&quot;Creating&quot; icon theme"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by PurposeOfReason on 2007-09-04
I was browsing gnomelook today and came across the monoblack icon theme. I've actually been looking for something like it for a while, real minimal and would look good with the window list screenlet. The only thing that gets me about it, there is no swiftweasel icon. I'd be more than happy to use the firefox icon so I tried to copy that icon, rename it swiftweasel.svg, and the put it in the icon folder where it would be (had it existed). Problem is, it's not recognized so if I'm running the windows list screenlet, all the icons are black minus that one, which is open most. So how would I go about adding an icon to an icon set?

---

### Post by Inxsible on 2007-09-04
> **PurposeOfReason said:**
> I was browsing gnomelook today and came across the monoblack icon theme. I've actually been looking for something like it for a while, real minimal and would look good with the window list screenlet. The only thing that gets me about it, there is no swiftweasel icon. I'd be more than happy to use the firefox icon so I tried to copy that icon, rename it swiftweasel.svg, and the put it in the icon folder where it would be (had it existed). Problem is, it's not recognized so if I'm running the windows list screenlet, all the icons are black minus that one, which is open most. So how would I go about adding an icon to an icon set?
Since the icon didn't exist at all, the theme file probably does not have any reference to that particular icon. what you might want to do is remove the swiftweasel.svg icon....then load that theme....then see what icon it uses for swiftweasel.

Then go back into the icon theme, locate the said icon(that was used) and replace that -- but keep the name as it is --(dont change it to swiftweasel.svg)

then repackage the theme and install the new theme (remove the old theme if you like)


Hope that is clear enough to understand !!

---

### Post by PurposeOfReason on 2007-09-04
I understand what you're saying and I've done that in the past for trash icons. The problem is there is no swiftweasel icon so it just used the default.

---

### Post by Inxsible on 2007-09-04
> **PurposeOfReason said:**
> I understand what you're saying and I've done that in the past for trash icons. The problem is there is no swiftweasel icon so it just used the default.
So replace whatever it used as "default" but do not change the name of the file.

For example if it used firefox.png as the icon for swiftweasel, then take your swiftweasel icon, rename it to firefox.png and then paste it in the theme folders...that will over write your current firefox.png and you will have a new icon

Of course if you also want to use the "default" icon for something else, this would not work since it will now use the swiftweasel icon that you replaced it with

---

### Post by PurposeOfReason on 2007-09-04
Well I replaced every swiftweasel icon. Made sure they were the right size and file type. It changed all of them but the window list. :/ You know, it wasn't that cool anyways. :)

---

### Post by Inxsible on 2007-09-04
> **PurposeOfReason said:**
> Well I replaced every swiftweasel icon. Made sure they were the right size and file type. It changed all of them but the window list. :/ You know, it wasn't that cool anyways. :)

Oh darn !!

Well we tried :)

---

### Post by Jouke74 on 2007-09-04
You need to edit the index file as well, otherwise it won't show up. :)

---

### Post by PurposeOfReason on 2007-09-04
How would I go about doing that?

EDIT - did it, didn't work. I dug around a bit and this screenlet doesn't like icon themes that much.

---

