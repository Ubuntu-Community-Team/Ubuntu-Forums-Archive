---
title: "Gimp - unable to show transparency?"
date: 2009-02-04
forum: General Help
---

### Post by mykrob on 2009-02-04
Using gimp from the Intrepid repositories on Ubuntu 8.10.
Seems there may be a bug, but I want to check with others. I am not able to display transparency. If i start a new image, and import two images as layers, then begin erasing on the top layer, instead of seeing the second layer beneath it, I see white...

Can anyone else confirm this? I have deleted the ~/.gimp-2.6 folder just to make sure it is not a configuration error on my part, and the problem persists. Any ideas?

thanks,
-myk

---

### Post by mykrob on 2009-02-05
bump.

Thanks,
-myk

---

### Post by mykrob on 2009-02-05
Just tested using Hardy in a Virtual Machine, and this problem does not exist on the version included with Hardy. Perhaps a bug should be filed, but I'd like to see if others can duplicate the problem.

---

### Post by mcduck on 2009-02-05
Works fine for me, running 8.10 and Gimp 2.6.3

---

### Post by mykrob on 2009-02-05
I just reinstalled the version direct from the normal repositories after disabling all unsupported and pre-released update repos.. I am now running version 2.6.1, which I assume is the default version included with Ubuntu 8.10..

The problem persists.

Any ideas on this at all??

For the time being, I have Photoshop 7 running in Wine, but I would really rather use the native software.

Thanks,
-myk

---

### Post by mykrob on 2009-02-05
Just tested some more.. If i scribble on a new document using the paint brush, then make a new layer and draw on it some more, then erase a bit from the top layer, i am able to see underneath.

But if I import an image as a layer, then erase some from it using the eraser tool, it displays white instead of the layer underneath.

Can someone test using this method to see if they can duplicate it?

Thanks,
-myk

---

### Post by mcduck on 2009-02-05
I tried again, this time using the "Open as Layers" from the File-menu and indeed the eraser tool uses background color instead of editing the opacity of that layer.

IF you then go to Layer/Transparency/Add Alpha Layer the eraser starts using alpha instead of background color. Since this option is in the menu I suppose the "Open as Layers" does literally what it says, opens the image as it is into a new layer. If the image doesn't have alpha channel then it's opened without one.

If you simply copy&paste an image into new layer the eraser works correctly without any extra steps.

edit: I also tested the "Opne as Layers" with images that have alpha channels (semi-transparent PNGs) and the eraser uses alpha instead of background color. BAsed on this I'd say that this is how it's supposed to work and there is no bug.

---

### Post by mykrob on 2009-02-05
THANK YOU!
The way it used to work, apparently it automatically added alpha.

I appreciate you helping me out with this!

-myk

---

### Post by mcduck on 2009-02-05
> **mykrob said:**
> THANK YOU!
The way it used to work, apparently it automatically added alpha.

I appreciate you helping me out with this!

-myk

No problem, I learned something new about Gimp as well. I don't think I've ever even tried the "Open as Layers" option, I've been simply drag&dropping files to Gimp or copypasting them.

---

### Post by mykrob on 2009-02-05
looks like drag and drop is better anyway, since apparently it keeps alpha intact.

---

