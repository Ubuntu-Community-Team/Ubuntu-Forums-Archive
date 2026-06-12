---
title: "Tomboy problem"
date: 2005-10-28
forum: Desktop Environments
---

### Post by 23meg on 2005-10-28
In the Breezy build of Tomboy, clicking on blank space in any note window seems to create a new note. This may have been though out as a feature, but if so, it's a really bad one, since one may want to click to quickly navigate anywhere in any large text entry field. Plus, things get really messed up when creating a new note; sometimes the contents of the present note get pasted into it as if it were a WikiLink.

Can anyone else confirm this? Is it a bug or a feature?

---

### Post by LorenzoD on 2005-10-28
Never heard of, or seen, that behavior.

---

### Post by 23meg on 2005-10-28
Really? This isn't the case with your *Breezy* build of Tomboy? The behavior remains even after doing a complete reinstall.

---

### Post by mcmuffy on 2005-10-28
Never heard of this program before this thread but I installed it to check and I don't get the behaviour that you discribe. The only way I can make a new note is by selecting text and then telling it to link.

---

### Post by Wolki on 2005-10-28
[QUOTE=23meg]In the Breezy build of Tomboy, clicking on blank space in any note window seems to create a new note. This may have been though out as a feature, but if so, it's a really bad one, since one may want to click to quickly navigate anywhere in any large text entry field. Plus, things get really messed up when creating a new note; sometimes the contents of the present note get pasted into it as if it were a WikiLink.

Can anyone else confirm this? Is it a bug or a feature?  :confused:[/QUOTE]

I had similar errors with accidental new note creation... can't say for sure since I didn't really test what caused the behavior, but I often had new notes created that I didn't want and that had a title consisting of parts of the note I was working on.

[edit] ok, I can't recreate it, but I definitely know it happened...

---

### Post by maruchan on 2005-10-28
I run Tomboy in Breezy too, and nope, no problem here.

---

### Post by el toro on 2005-10-28
I can't reproduce the behavior described by the original poster either.

---

### Post by 23meg on 2005-10-28
Very weird. I'll do another complete reinstall, and try once again to compile the latest version which isn't in Breezy. 

I also get a crash when I go to preferences while a note is open. With all notes closed, preferences works. Can anyone replicate *this*?

---

### Post by LorenzoD on 2005-10-28
[QUOTE=23meg]Really? This isn't the case with your *Breezy* build of Tomboy? The behavior remains even after doing a complete reinstall.[/QUOTE]

Er.. yes:

```

tomboy (0.3.2-9ubuntu4) breezy; urgency=low

  * Get on D-BUS.

```

No dapper packages for tomboy yet..

---

### Post by 23meg on 2005-10-31
This problem seems to have disappeared in Tomboy 0.3.3 running with the same set of notes in the former version.

---

### Post by calixtine on 2005-12-17
Just to say you're not the only person in the world who has this problem with Tomboy 0.3.2, 23meg, as I do too, and boy is it annoying, looks like I'll have to upgrade ..

---

