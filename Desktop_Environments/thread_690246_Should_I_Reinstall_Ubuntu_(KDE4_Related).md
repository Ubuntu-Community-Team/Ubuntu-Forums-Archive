---
title: "Should I Reinstall Ubuntu? (KDE4 Related)"
date: 2008-02-07
forum: Desktop Environments
---

### Post by jlacroix on 2008-02-07
I seem to be having a problem with KDE 4.0.1 installed on Ubuntu 7.10 that I don't think anyone else is having that I know of. I've tried alot of different things and I think reinstalling may be the only solution.

Let me explain. On my laptop I have Ubuntu and KDE 4.0.1 installed. Not Kubuntu, but KDE 4.0.1 by itself. On my Desktop, I have Kubuntu and Ubuntu installed with KDE 4.0.1 added to it. My Desktop does not have this problem, but my Laptop does. Both are Ubuntu 7.10.

The problem I experience is that on my laptop, the KDE4 applications menu has almost all question mark icons for almost everything. Even non-KDE apps like Thunderbird and Firefox. Almost everything is a question mark icon. I made sure I had all the necessary KDE4 packages installed. If I try to update an icon by myself using kmenuedit, the icon for a particular program won't be found anywhere. However, when I use Gnome, all the icons are there and are perfect. If I use the search feature in the KDE4 menu, the application will show up with the correct icon, but not in the list itself.

And again, on my Desktop PC, KDE4's menu is perfect. 

Is it because I didn't install kubuntu-desktop on my laptop? I really don't want to install that, I think it would be lame if Kubuntu's KDE4 packages depended on KDE3. Or, perhaps there is a KDE3 library I'm missing?

I even tried restoring the menu and reinstalling KDE4. Nothing fixes this. I was considering just reinstalling Ubuntu on my laptop as a last resort. If no one knows why I'm having this problem (which I'd understand, because I think I'm probably the only one) reinstalling may be the only solution.

Any attempts to end my frustration will be greatly appreciated.

---

### Post by TornadoWarning40422 on 2008-02-07
Try going into Synaptic Package Manager, and search for kde4, and see if there are a bunch of packages that aren't installed. If some imporant ones are missing, just install them. (since space doesn't appear to be a problem ;) I was having a similiar problem, and this fixed it. A few packages that may have major importance: (I don't know, since i'm pretty much a noob) :(
kde4-devel
all the kdebase-something packages
kwin :)
there are alot of kde4 packages so if you can, just take some time going through them
I hope my advice can be of some assistance.

---

### Post by jlacroix on 2008-02-07
Thank you, but I seem to have all of those installed already. Any other ideas?

---

