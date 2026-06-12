---
title: "Easy Way to Create New Docklet in Natty Narwhal?"
date: 2011-05-31
forum: Desktop Environments
---

### Post by GreenRaccoon on 2011-05-31
I've got Natty Narwhal and I just installed Docky.  I want to be able to create new docklets other than the default ones (like one for Firefox, Chrome, Banshee, etc.).

I guess before Ubuntu switched to Unity, you could just drag and drop icons into Docky.  Unfortunately, with the application bar gone in Natty, you can't do this anymore, and you can't drag icons from Unity into Docky either.  I've been searching the Internet and the only way I've figured out how to work around this is to create a new launcher on the Desktop and then drag it into Docky.

Am I missing something?  There's got to be an easier way to do this.

---

### Post by Copper Bezel on 2011-05-31
You could just go to the source and open /usr/share/applications, and drag and drop the .desktop file you'd like onto Docky, I think.

---

### Post by GreenRaccoon on 2011-05-31
Yeah, that worked; thanks Copper Bezel.  I don't know why I didn't try that in the first place.

In case someone reads this and wants to know how to remove the Docky Anchor icon, type this in Terminal:
```
gconftool-2 --type Boolean --set /apps/docky-2/Docky/Items/DockyItem/ShowDockyItem False
```

---

### Post by isbiyanto on 2012-02-17
> **Copper Bezel said:**
> You could just go to the source and open /usr/share/applications, and drag and drop the .desktop file you'd like onto Docky, I think.

thanks you :P

---

