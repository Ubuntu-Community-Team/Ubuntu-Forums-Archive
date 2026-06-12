---
title: "Headphone Jack works, Speakers don't?"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by MrSootentai on 2007-08-27
I'm running on a Dell 1420 and using Gutsy Tribe 5 and I have the problem that my sound card doesn't exactly work properly. I mean the sound works but only when I plug it into the front heapdhone jack. But once it's unplugged my speakers don't work at all.

Does anyone have any idea how to fix this? I had this same situation when I ran Fiesty.

---

### Post by ddrichardson on 2007-08-27
Is this perchance a Realtek HDA codec? If it is then search for it on ALSA's bugtracker - there's a patch for it. You would need to download the source and patch and compile, but it's relatively painless and people with Dells are reporting success.

---

