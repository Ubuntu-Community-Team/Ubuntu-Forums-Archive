---
title: "remote desktop bank screen - PLEASE DON'T IGNORE"
date: 2009-05-01
forum: General Help
---

### Post by alien5p5g on 2009-05-01
It seems as though all my threads here get ignored...

Hopefully someone can help me this time.

I'm having trouble using the remote desktop viewer. Everytime I try to open it, this shows up. (attached image)

What can I do to fix this? And what does it mean?

I'm using Ubuntu 8.10, if that helps. It just stopped working, and I don't know why.

Please reply, Alien.

---

### Post by doas777 on 2009-05-01
if you click in the window and wiggle the mouse, does the display come up?

---

### Post by alien5p5g on 2009-05-01
> **doas777 said:**
> if you click in the window and wiggle the mouse, does the display come up?

No, it doesn't. :(

---

### Post by doas777 on 2009-05-01
if you install vncviewer
```
sudo apt-get install vncviewer
```

and connect to your remote host with:
```
vncviewer <targetIP>
```

does it come up?

---

### Post by alien5p5g on 2009-05-01
No.

---

### Post by alien5p5g on 2009-05-01
I installed java recently....could that be the problem? I don't think I had this before that.

---

### Post by doas777 on 2009-05-01
the target box is running ubuntu right? if so, do you have desktop effects enabled? I have to turn them off entirely (RClick Desktop -> Change Background -> Visual Effects), or else it will always freeze output exactly as it was when the session started, showing windows I've closed, and not showing new ones i've opened (though they are visible on the host session).

---

### Post by alien5p5g on 2009-05-01
Wow. Thank you, all I had to do was disable some effects. Boy do I feel stupid. Sorry for wasting your time, guys.

---

### Post by doas777 on 2009-05-01
not a prob man. thats what we're hangin' arround for.
cheers

---

