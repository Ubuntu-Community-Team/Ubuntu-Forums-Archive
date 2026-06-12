---
title: "Why no warning or error from ln -s when target does not exist?"
date: 2009-06-17
forum: General Help
---

### Post by svamppi on 2009-06-17
Hello, not sure if the General Help forum was the right category for this question.

I hadn't really had a need for creating symbolic links with ln until today. And being a bit tired in the morning I used it in the wrong way a couple of times and only noticed it after a while.

I was specifying a target that didn't exist by mistake. But somehow I did not get a warning or error message. Now I figured ln should have such a long history that anything that seems odd is probably still the right behavior. So I was wondering if anyone had any suggestions why ln -s badtarget does not show errors or warnings.

---

### Post by dcstar on 2009-06-17
> **svamppi said:**
> Hello, not sure if the General Help forum was the right category for this question.

I hadn't really had a need for creating symbolic links with ln until today. And being a bit tired in the morning I used it in the wrong way a couple of times and only noticed it after a while.

I was specifying a target that didn't exist by mistake. But somehow I did not get a warning or error message. Now I figured ln should have such a long history that anything that seems odd is probably still the right behavior. So I was wondering if anyone had any suggestions why ln -s badtarget does not show errors or warnings.

Because it does exactly what it is supposed to do:

```
man ln
```

---

### Post by cariboo on 2009-06-17
On my system, using mc a proper symlink is colored green, and a improper symlink is colored red.

---

### Post by lloyd_b on 2009-06-17
> **svamppi said:**
> Hello, not sure if the General Help forum was the right category for this question.

I hadn't really had a need for creating symbolic links with ln until today. And being a bit tired in the morning I used it in the wrong way a couple of times and only noticed it after a while.

I was specifying a target that didn't exist by mistake. But somehow I did not get a warning or error message. Now I figured ln should have such a long history that anything that seems odd is probably still the right behavior. So I was wondering if anyone had any suggestions why ln -s badtarget does not show errors or warnings.

At a guess, because "badtarget" may not exist at the time the link is created, but may be created later.  Or someone may want to create a symlink to something on a network drive that isn't accessible at the moment.  Or to a "\dev" entry that won't exist until the associated device is connected.

Logically, since it's possible for broken symlinks to exist, there must exist some mechanism for creating them (other than creating valid symlinks, and then deleting the target, that is).
 
Lloyd B.

---

### Post by svamppi on 2009-06-17
Ah it was actually me just being stupid and not noticing that I had actually created a few symlinks that pointed to non-existing files.

---

