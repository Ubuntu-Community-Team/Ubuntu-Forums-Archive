---
title: "Nautilus Toolbar"
date: 2004-12-10
forum: Desktop Environments
---

### Post by jcooper on 2004-12-10
Sorry if this has been asked before, I can't find a related post.

I like the layout of the spatial window, but I don't like the spatial behaviour (remembering layout, new windows without middle/shift clicking etc). I've set my nautilus to browser mode by default, and switched of the sidebar.

Is it possible to hide the toolbar (as I rarely use the icons). I've looked (albeit quickly) through GConf to no avail.

Any pointers gratefully accepted  :)

---

### Post by jcooper on 2004-12-15
*bump*

Any ideas? Or should I submit a bug/feature request to nautilus?

---

### Post by mula on 2004-12-15
I just would like to add:
[QUOTE=jcooper]Is it possible to hide the toolbar (as I rarely use the icons)?[/QUOTE] And maybe is there any way to make it a bit smaller?

---

### Post by t.rei on 2005-02-27
I would like to see this, too.

I tend to know exactly where I'm going - no need for the icons.

So - since no reply was postet I guess this means nothing short of editing and recompiling nautilus would do?

as for "making it smaller": I tried several themes and settings in them. But didn't get it any smaller. (Except a few pixels) :(

---

### Post by pt123 on 2005-07-08
[QUOTE=t.rei]I would like to see this, too.

I tend to know exactly where I'm going - no need for the icons.

So - since no reply was postet I guess this means nothing short of editing and recompiling nautilus would do?

as for "making it smaller": I tried several themes and settings in them. But didn't get it any smaller. (Except a few pixels) :([/QUOTE]
 I want the oposite my nauitilus doesn't have the tool bar when I open something Using Places>>Location

---

### Post by SlugO on 2005-07-17
I'd like to know how to change the toolbar icons in browser mode.
They're quite ugly :?

---

### Post by poptones on 2005-07-17
The toolbar icons are changed by icon themes. If you go to system>prefernces>themes and click "details" you will be able to change the icons for a theme. You can find many themes at art.gnome.org

---

### Post by SlugO on 2005-07-17
[QUOTE=poptones]The toolbar icons are changed by icon themes. If you go to system>prefernces>themes and click "details" you will be able to change the icons for a theme. You can find many themes at art.gnome.org[/QUOTE]

Hmm.. My current icon theme is Dropline Etiquette. It obviously has icons
for the toolbar in stock folder but they're not showing in the toolbar.
How can I get them to work?

---

### Post by doclivingston on 2005-07-18
I'm not sure if this is available in Warty (I'm using Breezy), but the gconf key "/apps/nautilus/preferences/start_with_toolbar" works for me.

---

### Post by poptones on 2005-07-18
[QUOTE=SlugO]Hmm.. My current icon theme is Dropline Etiquette. It obviously has icons
for the toolbar in stock folder but they're not showing in the toolbar.
How can I get them to work?[/QUOTE]
 Not sure what version you are using but there's some oddities I know of in hoary. I installed it a couple of times and once it was perfect, the second time I could not get any themes to work right or even install. The only way I was able to make them work right was to copy the theme folder to the /usr/share/themes folder (you'll need to use sudo for this, ie "sudo cp thistheme /usr/share/themes"

---

