---
title: "I lost Documents"
date: 2009-02-20
forum: Desktop Environments
---

### Post by wide-load on 2009-02-20
I have a 3 day old installation of Intrepid.  This morning I was editing a document and attempted to save it in my Documents directory.  Documents didn't appear in the choices of where to store it.  PLACES in the panel doesn't have it as an option when I Open that.  The folder is still there, it contents are still there, I can drill down from my home folder and find it and it's contents.  How do I restore it back to PLACES?

---

### Post by ugm6hr on 2009-02-20
1. Open nautilus (file browser in standard Gnome Ubuntu).
2. Find Documents (/home/username/Documents)
3. Drag and drop *Documents* to bottom left pane (Shortcuts)

---

### Post by wide-load on 2009-02-20
> **ugm6hr said:**
> 1. Open nautilus (file browser in standard Gnome Ubuntu).
2. Find Documents (/home/username/Documents)
3. Drag and drop *Documents* to bottom left pane (Shortcuts)

This is going to sound very novice but I can't figure out how to open Nautilis.   I've opened up some files but the there is no bottom left pane that I can drag documents into.

---

### Post by ugm6hr on 2009-02-20
Places -> Home Folder
Press F9
The Side Pane will appear / disappear
At top of side pane: another menu selection:
Select "Places"

If this doesn't make sense, go to Places -> Home Folder and post a screenshot of that.  We can work out what the problem is from there (and put arrows on screenshot to solve).

---

### Post by wide-load on 2009-02-20
> **ugm6hr said:**
> Places -> Home Folder
Press F9
The Side Pane will appear / disappear
At top of side pane: another menu selection:
Select "Places"

If this doesn't make sense, go to Places -> Home Folder and post a screenshot of that.  We can work out what the problem is from there (and put arrows on screenshot to solve).

When I press F9 the window "jumps" just slightly.  No pane appears.

I took screenshots and uploaded them.  If you can see them there is only a slight difference between them, if they uploaded.  I can't seem them in my preview, so I don't know if they uploaded.

---

### Post by ugm6hr on 2009-02-20
You didn't upload any screenshot.

Look at this: [http://projects.gnome.org/nautilus/images/screenshot2.png](http://projects.gnome.org/nautilus/images/screenshot2.png)

On the left (Sidebar), where it has "Tree" - click and select "Places" to enable the "Shortcuts" in bottom left.

EDIT: See screenshots.
Go to View -> Side Pane (make sure it is ticked)

---

### Post by wide-load on 2009-02-20
I don't like the screen shots.  I going to redo them.  Here are 2, one with F9 depressed and with without.  As you can see they look virtually the same.

---

### Post by wide-load on 2009-02-20
On the left (Sidebar), where it has "Tree" - click and select "Places" to enable the "Shortcuts" in bottom left.

I couldn't find Tree.

EDIT: See screenshots.
Go to View -> Side Pane (make sure it is ticked)

Side Pane was Ticked
__________________

---

### Post by wide-load on 2009-02-20
I've got an old backup system.  I just tried it.  F9 does work on it.  On this one it doesn't. Something is wrong on the system.

---

### Post by wide-load on 2009-02-20
As an additional piece of information.  I logged into my wife's account on this machine.  F9 works on her account.  It's just this account that's having the problem.

---

### Post by ugm6hr on 2009-02-21
I'm not sure what has happened.

All I can suggest is renaming / removing the ~/.nautilus file (where your settings are stored) and trying again.

```
mv ~/.nautilus ~/.nautilusbkp
```

Then log out and log back in again.

If it makes things worse:
```
rm ~/.nautilus
mv ~/.nautilusbkp ~/.nautilus
```

---

### Post by wide-load on 2009-02-21
> **ugm6hr said:**
> I'm not sure what has happened.

All I can suggest is renaming / removing the ~/.nautilus file (where your settings are stored) and trying again.

```
mv ~/.nautilus ~/.nautilusbkp
```

Then log out and log back in again.

If it makes things worse:
```
rm ~/.nautilus
mv ~/.nautilusbkp ~/.nautilus
```

Thanks for the advice.  It's a busy weekend and I'll probably not get a chance to try it until first of next week.  I'll probably try it on my old backup system first to make sure there are no unexpected "surprises".

---

### Post by wide-load on 2009-02-21
**Case Closed (**  And is my face [COLOR="Red"]RED[/COLOR].)  I'm feeling like the Ubuntu IDIOT.  Just now I had my cursor on the extreme left hand side of Nautlis and I discovered that the cursor changed to a double ended arrow.  The window had been shrunk on the left hand side, collapsing the pane.

Thanks for all your help on this.

---

