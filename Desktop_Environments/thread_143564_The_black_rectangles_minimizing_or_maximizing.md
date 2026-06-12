---
title: "The black rectangles minimizing or maximizing"
date: 2006-03-12
forum: Desktop Environments
---

### Post by glotz on 2006-03-12
When I max or min a window it kinda pops in or out leaving behind this stream of the black rectangles. Hope you understand what I mean. On Gnome on Ubuntu 5.10. I'm on an older system. Can I disable them? Also other tips on making it lighter are appreciated.

Thanks!

I just installed Breezy Badger yesterday and today I allready love it! :D It failed to detect my SB16 but got it working. Also my mouse  back button works now on Firefox 1.5.0.1 but not in file browser or help for example.

---

### Post by codejunkie on 2006-03-12
[QUOTE=glotz]When I max or min a window it kinda pops in or out leaving behind this stream of the black rectangles. Hope you understand what I mean. On Gnome on Ubuntu 5.10. I'm on an older system. Can I disable them? Also other tips on making it lighter are appreciated.

Thanks!

I just installed Breezy Badger yesterday and today I allready love it! :D It failed to detect my SB16 but got it working. Also my mouse  back button works now on Firefox 1.5.0.1 but not in file browser or help for example.[/QUOTE]
open a terminal and enter ```
gconf-editor
```then navigate to apps/metacity/general and check the box that says reduced_resources close the config editor then go to System/Preferences/Assitive Technology Support and check the box that says enable assitive technologies then close and this should fix the problem.

---

### Post by glotz on 2006-03-12
Thank you! That made it somewhat snappier. Gotta love effective forums!

---

### Post by aysiu on 2006-03-12
Except that *reduced resources* also gives you black rectangles when you *move* windows (instead of minimizing/maximizing them).

---

### Post by codejunkie on 2006-03-12
[QUOTE=aysiu]Except that *reduced resources* also gives you black rectangles when you *move* windows (instead of minimizing/maximizing them).[/QUOTE]
not when you enable assistive technologies and reduced_resources, it removes all the black rectangles. It makes metacity look a ton better, no black boxes chasing your windows around the screen.

---

### Post by matthew on 2006-03-12
[quote=codejunkie]not when you enable assistive technologies and reduced_resources, it removes all the black rectangles. It makes metacity look a ton better, no black boxes chasing your windows around the screen.[/quote]You're right! I just tried it out and I like the effect. Thanks!

---

### Post by aysiu on 2006-03-12
[QUOTE=codejunkie]not when you enable assistive technologies and reduced_resources, it removes all the black rectangles. It makes metacity look a ton better, no black boxes chasing your windows around the screen.[/QUOTE] That's a great little trick. Thanks! By the way, what *is* "assistive technology," and why does it make Metacity look better?

---

### Post by codejunkie on 2006-03-13
[QUOTE=aysiu]That's a great little trick. Thanks! By the way, what *is* "assistive technology," and why does it make Metacity look better?[/QUOTE]
i think assistive technology support provides visual aids to help disabled people not 100% sure though, and i don't really know why it makes metacity look better, i was just monkeying around with everything trying to get rid of those wire frames chasing my windows around and found that if i enable this it disables the wire frames in metacity.

---

### Post by blackant on 2006-03-13
Great, I have been search for a solution for this problem.\\:D/

---

### Post by glotz on 2006-03-14
Uhm, how do I delete posts? (this one)

---

