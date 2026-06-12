---
title: "Image preview/thumbnail"
date: 2009-12-14
forum: Desktop Environments
---

### Post by mtbeedee on 2009-12-14
I am running a hardy desktop and for some reason it decided to stop showing previews of anything new.  It still will show a thumbnail of older images that I have had, but any new ones, it just has the generic file icon there instead of the preview of the image.  I checked the nautilus preferences > preview stuff and it seems like it should be working.

Any ideas what might have caused it to stop previewing new images?

---

### Post by mtbeedee on 2009-12-15
Nothing?

---

### Post by mtbeedee on 2010-03-11
This was annoying me again so I took a screenshot that illustrates the problem.

You can see there are 2 jpegs.  They look exactly the same from a properties point of view but for some reason nautilus generates a preview of one but not the other.  Is there any way I can get error logs from this or does anyone know why it might do this?

---

### Post by mcduck on 2010-03-11
Try emptying the ~/.thumbnails -directory..

---

### Post by mtbeedee on 2010-03-11
Well, that made all of the thumbnails go away.  Any idea how to make it "refresh" and readd them?

---

### Post by mtbeedee on 2010-03-15
This thing isn't generating any thumbnails and I don't see anywhere that it is logging.

---

### Post by asmoore82 on 2010-03-15
> **mcduck said:**
> Try emptying the ~/.thumbnails -directory..
Ouch

I would have advised only deleting "~/.thumbnails/fail"

---

### Post by asmoore82 on 2010-03-15
Well, I guess there's nothing to lose...

```
gconf-editor
```
Browse down to "/desktop/gnome/thumbnailers" and poke around in there.
Sorry I can't be more specific, but I'm not sure what we're looking for ;).

---

### Post by mtbeedee on 2010-03-18
> **asmoore82 said:**
> Well, I guess there's nothing to lose...

```
gconf-editor
```
Browse down to "/desktop/gnome/thumbnailers" and poke around in there.
Sorry I can't be more specific, but I'm not sure what we're looking for ;).

Thanks.

There's no entry there for like image@jpg or image@png or anything like that.  Can someone let me know what the correct "command" is to put there?

Also, how to add a new "directory" or whatever it's called?

---

### Post by asmoore82 on 2010-03-19
> **mtbeedee said:**
> There's no entry there for like image@jpg or image@png or anything like that.

I think this is normal; I don't have one either(screenshot) but my jpeg thumbnails still work.

Hopefully some kind stranger out there knows what's going on...

---

### Post by mtbeedee on 2010-03-24
oh well. I wonder what it could be

---

### Post by mtbeedee on 2010-04-01
bump

---

