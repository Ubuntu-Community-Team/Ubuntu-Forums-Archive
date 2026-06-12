---
title: "Can aptitude upgrade only certain packages?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Steveire on 2006-07-12
I tried this:
```

sudo aptitude upgrade open*

```
Which if it worked would upgrade only my openoffice files, and not the rest. It doesn't work. Is there any way to do this?

---

### Post by aysiu on 2006-07-12
I know it can work if you list out the files. I don't think a * wildcard works with *aptitude*.

Why not just do this? ```
sudo aptitude update
sudo aptitude install openoffice.org
```

---

### Post by Steveire on 2006-07-12
Because I don't want to install it, but upgrade some packages and not others. 

I think Adept has a tick the box function for this kind of thing.
I was hoping there would be some command line candy. I'll list the files. 

Thanks for your help.

---

### Post by aysiu on 2006-07-12
If you tell Ubuntu to "install" a package with *aptitude* or *apt-get* it will also upgrade that package if it's already installed.

You are essentially "tick[ing] the box" by listing out the packages. I'm not aware of any kind of wildcard feature in Adept or Synaptic.

---

### Post by Steveire on 2006-07-12
Thanks for that install tip. The upgrade command wasn't working.

I meant command line magic in that it would be a feature not available in Adept.

---

