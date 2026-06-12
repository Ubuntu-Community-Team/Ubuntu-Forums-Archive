---
title: "nautilus file browser: how to remove item from 'places' pane above separator?"
date: 2007-04-26
forum: Desktop Environments
---

### Post by nullcore on 2007-04-26
in the "places" side pane of the file browser, how do i edit the contents above the horizontal separator?  somehow i got a folder stuck up there, and it won't come out.  it's annoying me... taunting me.  is there somewhere to manually edit what appears in there?

i'm new to this.

</noob.q>

thanks in advance.

---

### Post by MRiGnS on 2007-04-26
i searched the gconf and found nothing. You should file a bug if no one comes up with a solution.

---

### Post by tonic on 2007-04-26
I've been looking for some way to do this. It seems nautilus decides what to do with your partitions based on fstab and some other things. There is no easy way to fiddle with nautilus in this area. Putting the partition into fstab _should_ remove the entry from the places menu.

---

### Post by castironpants on 2007-05-17
I'm having the same problem. Even though I use Thunar, Nautilus is still responsible for my "Places" menu. It insists on putting a separate "Documents" folder there, so now I have two and I don't know how to remove one.

---

### Post by toasterofirony on 2007-05-17
> **castironpants said:**
> I'm having the same problem. Even though I use Thunar, Nautilus is still responsible for my "Places" menu. It insists on putting a separate "Documents" folder there, so now I have two and I don't know how to remove one.

Are you sure it isn't the "Documents" folder in your home directory? 'Cause my sidebar looks much the same as you describe, except that when I double-click on the "Documents" folder on my side bar, it takes me to the folder in my home directory of the same name.

---

### Post by castironpants on 2007-05-20
It did it even when I deleted that folder. I can give it another try, though. 

There is one more question I have. I've been toying around with myGtkMenu, and I think that could be a good replacement to the main menu bar, but is there any way to replicate how discs appear in the places menu only when they've been mounted, and with the proper name?

---

### Post by Cresho on 2007-05-20
try this...

open up nautilus and in the bookmark, remove the documents.  I had 2 documents till I removed it from that location.  I added a few folders and now it appears in my "places".  I don't think it is a bug.  I had the same issues.

---

### Post by castironpants on 2007-05-20
Here's the problem: I use Thunar mostly, and I DO want Documents to come up with the rest of my folders on the side panel. It's just that the Places menu seems to have a mind of it's own

---

### Post by tonic on 2007-05-20
It does, and it is a real pain.

---

