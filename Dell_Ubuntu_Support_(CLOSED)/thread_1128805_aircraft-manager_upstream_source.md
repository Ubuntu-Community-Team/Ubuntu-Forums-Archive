---
title: "aircraft-manager upstream source?"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Brandon Williams on 2009-04-18
I recently installed Jaunty on my dell mini 9, and I wanted to have aircraft-manager. The version from the dell-mini repo doesn't work on Jaunty for a few different reasons, so I updated it to make it install and function correctly.

I've been looking around trying to figure out where the upstream source is hosted and where bug reports should go. I can't find it anywhere. I expected there to be a luanchpad project, considering the fact that the maintainer has a canonical e-mail address, but it's not there. I can't find any reference to it with Google, either.

For now, I've got updated packages in my PPA repository, but I did not intend to fork this code. Does anyone know what I can do to push my changes back upstream?

---

### Post by rmjb on 2009-10-12
Hey Brandon, I got your repack from your ppa. Is there a way to map the command to the Fn+2 key combo?

---

### Post by Brandon Williams on 2009-10-13
In Dell's ubuntu, it's mapped in hal or something (I've never bothered to track it down). In jaunty, you should be able to create a gnome keyboard shortcut mapped to that key. You might have to use xmodmap to assign a symbol to the key first, though.

---

