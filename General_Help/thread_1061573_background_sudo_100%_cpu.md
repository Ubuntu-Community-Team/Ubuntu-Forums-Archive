---
title: "background sudo 100% cpu"
date: 2009-02-05
forum: General Help
---

### Post by lavinog on 2009-02-05
Today I wanted to change something in grub really quick. I had the terminal already open and out of habbit I attempted to background gedit:
```
sudo gedit /boot/menu.lst&
```
This of course backgrounded sudo instead which was waiting for my password.
I then noticed that my cpu load was at 100%.
Closing the terminal restored the load back to normal.

Yes, this was user error, but should sudo be using 100% cpu just because an ampersand was on the line?
Is there an infinite loop if there is no stdin?

I have at times forgot what was in the clipboard and accidentally pasted the wrong stuff into the command line (something about ctrl-c vs ctrl-shift-c). At one time i pasted a weblink that contained ampersands in it, and all sorts of craziness happened.

---

### Post by mb_webguy on 2009-02-06
I just tried it myself, and I can verify that the process does indeed use 100% of a CPU.  (Fortunately I have a dual-core processor, so I didn't even notice the increased processor load...)

And I have no idea why sudo would use that much processor time when it should just be waiting for input.

---

### Post by lavinog on 2009-02-06
An easy test would be to:
```

sudo -k
sudo -v&

```
after observing the cpu load, closing the terminal should return it to normal.

It seems very much like an inf loop.

---

