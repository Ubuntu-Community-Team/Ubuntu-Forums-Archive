---
title: "Dolphin split-view problem"
date: 2007-11-24
forum: Desktop Environments
---

### Post by Sciamano on 2007-11-24
When I enable split-view in Dolphin, the screen is no split in two symmetrical parts.
Check the attachment and you'll see what I mean. 
I would like both the directory listings of the same size, but all I get is a small right-side "directory" portion, whilst the "information" portion looks enormous.

Any suggestions on how to solve this?

Thanks a lot.
Luca

---

### Post by firephoto on 2007-11-24
You can drag and resize with the divider of the split and the one between the right pane and the info panel. Just drag and move.

---

### Post by samwyse on 2007-11-24
I presume it's just broken and not fixable by any configuration. It's a very unfinished app and shouldn't have been made the default filebrowser. 

You'll get a proper split view if you disable the other panel.

---

### Post by Sciamano on 2007-11-24
> **firephoto said:**
> You can drag and resize with the divider of the split and the one between the right pane and the info panel. Just drag and move.

I know, and I've done that... the problem is that Dolphin won't remember it. 
Next time I choose the split-view, it would be the "wrong" size again.

---

### Post by Sciamano on 2007-11-24
> **samwyse said:**
> I presume it's just broken and not fixable by any configuration. It's a very unfinished app and shouldn't have been made the default filebrowser. 

I see. I'll probably switch to Krusader.

> **samwyse said:**
> You'll get a proper split view if you disable the other panel.

I don't understand what you mean. Could you explain? Thanks

---

### Post by bailout on 2007-11-24
> **Sciamano said:**
> I see. I'll probably switch to Krusader.



You can have two or more split views in konq as well.

---

### Post by Sciamano on 2007-11-24
> **bailout said:**
> You can have two or more split views in konq as well.

I know, but I need something with "shortcuts" like "edit as root", "copy/move as root"...
And I have no idea if that is possible with Konqueror... but of course I would love to learn it.

---

### Post by rand0m on 2007-11-25
If you go to View > uncheck Right Sidebar. Then split view should start symmetrically. I think the problem is the Information sidebar resizes itself depending on what file you are viewing/hovering over. I use the Info sidebar on the left with no problems. For the bookmark links I use the drop down menus next to the address bars.

As for the folder shortcuts you mentioned, you should be able to get those in Konqueror. Look in: /usr/share/apps/d3lphin/servicemenus/ or "dolphin" instead of "d3lphin". These are the service menus. Copy the ones you want to: /usr/share/apps/konqueror/servicemenus/ - you can also edit them in a text editor.

You can also search for other kde service menus on kde-apps.org or google. They are interchangeable between dolphin and konq.

---

### Post by Sciamano on 2007-11-25
Thanks rand0m!
I'll try that :-) I have nothing against Konqueror, I think it's a very good program and if it can do the things I need, I have no need to look for any other app! :-)

---

### Post by Fatboy Snarky on 2007-12-14
Hi,


there is a bug description on launchpad.net.

> [https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/137809](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/137809)

Unfortunately, noone seems to care...
I'm going to ask the maintainer via e-mail, after checking the bugreports on kde.org.
I admit, it's more like a minor bug, but you'd suppose it is a rather easy fixable one.

Would be interesting to know if this bug is only specific to Kubuntu. Somehow I can't imagine KDE releasing Dolphin with this palpable bug. 

Maybe they are all too occupied with the impending release of KDE4?

---

### Post by Sciamano on 2007-12-15
I have no idea if it is a Kubuntu-specific problem, but the upcoming release of KDE4 and D4lphin might be the reason for the fact that no one cares.

As you say, it doesn't look like a giant bug to be solved, but still...

---

### Post by lodp on 2008-02-03
any news on this? this really is annoying.. having to resize that side-bar every time you switch to split-screen. and it's even worse if you're not on a wide-screen..

---

### Post by Sciamano on 2008-02-04
Not that I know of... :(

---

