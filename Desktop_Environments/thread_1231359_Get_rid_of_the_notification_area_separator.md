---
title: "Get rid of the notification area separator"
date: 2009-08-04
forum: Desktop Environments
---

### Post by wayne_cat on 2009-08-04
Does anybody knows the name of the notification area separator icon. I want to remove
it (use a transparent image)


.

---

### Post by wayne_cat on 2009-08-04
Does anybody knows the name of the notification area separator icon. I want to remove
it (use a transparent image)


.

---

### Post by mcduck on 2009-08-04
You can replace the handles on Window List- and Notification Area-applets with a transparent image simply with a piece of code in your .gtkrc-2.0-file:

Just put this code in ~/.gtkrc-2.0 (create the file if it doesn't exist) and put a empty transparent .png image called ".pixel.png" in your home directory. Log out & back again and the applet handles are now invisible.

```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

(as far as I know replacing the actual handles or disabling them isn't as easy as simply finding some image file and replacing it, the images come from your GTK theme so you'd have to edit a lot more stuff than just a single image.. But doing it this way works great..)

---

### Post by mcduck on 2009-08-04
I already answered this in your other thread. And please no double posting. :)

---

### Post by Subban on 2009-08-04
Deleted post, thread merge left it redundant, and my own original reply was inferior /cry :P

---

### Post by drs305 on 2009-08-04
Reason for post no longer exists.

---

### Post by wayne_cat on 2009-08-04
mcduck, thank you for the solution ... works like a charm.

I posted the thread in the Art&Design forum ... and (silly me) looked for it in the Desktop Environment 
forum ... what ... why is it not there? ... deleted? ... server error? ...ok ... I have to post again.

mcduck & Subban ... thank you for merging/deleting/kicking my butt :redface:

---

### Post by mcduck on 2009-08-04
> **drs305 said:**
> Nice tip, but I believe the filename in post #3 should be **~/.gtkrc-2.0**. It will work with the file name change. 

Also, it appears that if you don't create .pixel.png, the separator disappears. Of course, internally that probably generates an error but it seems (pardon the pun) transparent to the user.

sorry, my typo. I'll fix that. :)

Letting the handle disappear completely (as in if you don't have the picture) would be a problem if you ever need to move your panel applets around or access settings for these two applets. So I recommend just using the transparent image.. 1-pixel empty PNG file isn't eating that much disk space or your other system resources and you'll still maintain all normal functionality.. :)

---

### Post by andrek on 2009-12-06
Sorry for a big bump but I've got to say that this tip works wonderfully. Thanks a lot, mcduck!

---

