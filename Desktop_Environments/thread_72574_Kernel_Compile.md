---
title: "Kernel Compile?"
date: 2005-10-06
forum: Desktop Environments
---

### Post by mpierce on 2005-10-06
I want to compile a new kernel as I'm using a Dell Inspiron 9300.

Is there a way to this and have it use the nice looking Kubuntu splash screen on startup?

I typically compile using make-kpkg kernel_image && make-kpkg modules_image.

Thanks!
Marvin

---

### Post by mlomker on 2005-10-06
> I typically compile using make-kpkg kernel_image && make-kpkg modules_image.


Breezy includes boot splash but the last disc that I download still had a gnomish bootup.  I suspect that it'll remain that way because the artwork has to be applied as a kernel patch.

That would put the Kubuntu team into the position of releasing every security update to the kernel on their own and having a different package.  I can't imagine them doing that.

There are some [bootsplash images]("http://www.bootsplash.de/") available that you can apply to your kernel, but I'm not aware of any Kubuntu artwork (yet).

---

### Post by mpierce on 2005-10-06
Thanks for replying.
Its a shame as they only have to supply the patch and image once whenever there is an update.

---

### Post by mlomker on 2005-10-06
> Its a shame as they only have to supply the patch and image once whenever there is an update.

They may very well do so at some point; it's just speculation on my part.  I'm just assuming that Kubuntu has fewer developers and they are doing a lot of work on making KDE easier to use.

---

