---
title: "Blinking cursor appearing in web pages"
date: 2005-12-16
forum: General Help
---

### Post by magnusbb on 2005-12-16
In firefox 1.5 I encounter a blinking cursor, like the one seen in word processing documents, while looking through web pages. I feel this cursor makes the page scrolling jerky since it doesn't move uniformly over text and images.

Is there anyway to fix this? I don't want to delete my profile.

---

### Post by magnusbb on 2005-12-16
I got it fixed. Did a deep search into the magic world of Google, and found that the setting is hidden under the hood of Firefox.

It's simply:
accessibility.browsewithcaret and it should be **false.** Mine was true.

---

