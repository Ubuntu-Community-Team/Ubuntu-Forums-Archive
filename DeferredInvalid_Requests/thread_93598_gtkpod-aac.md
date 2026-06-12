---
title: "gtkpod-aac"
date: 2005-11-22
forum: Deferred/Invalid Requests
---

### Post by gk_jam on 2005-11-22
gtkpod-aac is available in the hoary extras restricted section. Can it be put in the breezy extras restricted section?  Right now if using breezy it can't be found in any repository.

---

### Post by themindlessmatt on 2005-11-22
Does anyone know why gtkpod isn't compiled by default with aac? As far as I know it doesn't play AAC, only tags them, are there any issues with this? Any more than with mp3?

Matt

---

### Post by jdong on 2005-11-22
AAC licensing... :-/

---

### Post by gk_jam on 2005-11-22
Is this request deferred or invalid? I understand why gtkpod doesn't support aac by default, which is why the request was for the aac version in the breezy extras restricted area.

---

### Post by jdong on 2005-11-23
Ubuntu doesn't do it because of licensing restrictions associated with AAC, and I won't either for the same legal liability issues.

---

### Post by gk_jam on 2005-11-23
Ok, I was just asking because I'd seen that it had been done before for Hoary, in this thread:

[http://www.ubuntuforums.org/showthread.php?p=158899#post158899]("http://www.ubuntuforums.org/showthread.php?p=158899#post158899")

Has the situation changed since then, or can it be incorporated for breezy the same way it was earlier? Forgive me, I'm quite new to this, but if there are liability issues I understand.

---

### Post by Dr Gonzo on 2006-01-17
IMO, this is a load of crap, since there are libraries all over the place in Breezy that allow playback of AAC files -- like gstreamer0.8-faac, libmp4v2, etc.  So, why can't gtkpod be compiled against these?

As far s I can tell, it's gtkpod's fault that it doesn't compile against the new libmp4v2-dev library in the Breezy repository.  There are also AAC *encoders* in the repository, and the licensing issues on encoders are even more restrictive than for decoders.  Why would we have access to free-software AAC encoders, but not AAC support for a program that just moves files to an iPod?  It makes *no sense whatsoever that this would be the case.*

So, the licensing issue must be a red herring.  If a program can deal with mp3 licensing issues, it can deal with mp4 issues, which are similar.

---

