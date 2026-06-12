---
title: "Netbook Remix 9.04 Questions"
date: 2009-04-25
forum: General Help
---

### Post by campbecf on 2009-04-25
I uninstalled Evolution via synaptic package manager but when I try to rclick then "remove" "Evolution Mail & Calendar" from the favorites section it won't go away.

I also tried to make a firefox shortcut for Gmail in the favorites section but the icon didn't seem to come with it - is there anyway to get the icon to show up?

Thanks.

---

### Post by blackened on 2009-04-25
Been a while since I've used the netbook interface, but iirc the Favorites section is the only left-pane section that is right-clickable for customization. You should be able to set the icon that way.

That said, I remember it not being persistent when icon changes were made. Don't know why that was exactly. It was especially a problem with URL shortcuts.

---

### Post by campbecf on 2009-04-25
Alright, that might resolve the issue with the Gmail icon but what is going on with not being able to remove Evolution?

---

### Post by Universal344 on 2009-04-25
Although I've never experienced this in Ubuntu, sometimes I would be unable to remove icons for uninstalled applications in Windows.  You could try finding the .desktop file for the icon and manually deleting that.  It might be in the desktop folder, but it might be different UNR.  if that doesn't work, you could try reinstalling it, removing the icon and then uninstalling.

---

### Post by blackened on 2009-04-25
Can you drag the shortcut to the trash icon (remove favorite) in the right-hand pane? It should do the same as what right-clicking and removing the shortcut would, but it's worth a shot.

I can't remember if the favorites menu is configurable via alacarte. That, or deleting the .desktop file might be the next avenue to explore

---

### Post by campbecf on 2009-04-25
Where would the .desktop be?

---

### Post by blackened on 2009-04-25
> **campbecf said:**
> Where would the .desktop be?

/usr/share/applications

I'm not sure that will fix it though, especially if the favorites menu creates a separate shortcut to that file. It's worth a shot though.

---

