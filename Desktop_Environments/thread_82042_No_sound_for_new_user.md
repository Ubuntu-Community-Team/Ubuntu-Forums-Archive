---
title: "No sound for new user?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by dansherman on 2005-10-25
First off, ubuntu runs GREAT for my primary user, sound/video work perfectly.  I created a second user, but there is no sound.  I try to open the volume control but I get the message 

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
```

The card in my laptop is a ESS Allegro (gateway laptop).

Any ideas?

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=dansherman]First off, ubuntu runs GREAT for my primary user, sound/video work perfectly.  I created a second user, but there is no sound.  I try to open the volume control but I get the message 

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
```

The card in my laptop is a ESS Allegro (gateway laptop).

Any ideas?[/QUOTE]

When you added the new user, did you make the account a member of the audio group?  If you go back to the administrative tool you used to create the user, you should be able to add the user to this group if it is not already a member.

---

### Post by dansherman on 2005-10-26
That worked great! Thanks!

---

