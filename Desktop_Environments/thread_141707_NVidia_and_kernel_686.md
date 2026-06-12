---
title: "NVidia and kernel 686"
date: 2006-03-08
forum: Desktop Environments
---

### Post by FIONEX on 2006-03-08
Hey, I installed the 686 kernel using the synaptic package manager kuz I heard it makes linux a bit faster.  I'm not sure if that's true but the problem is that it doesn't even boot.  It says that the nvidia driver cannot be found.  Funny thing is, I'm currently on the 386 kernel with no problems and the same config :S.  Any ideas?

---

### Post by andrewsawyer on 2006-03-08
Do you mean it won't boot or it won't load the graphical front end?

You might need to recompile the nVidia drivers to work correctly with the new kernel (or just download them again if you originally got them from Synaptic).

If you don't like the idea of that, you can go back to the old kernel by hitting ESC while booting at the GRUB prompt and choosing the kernel that you want to boot.

---

### Post by FIONEX on 2006-03-08
It won't load the X server because it says it can't find the nvidia drivers.  How would redownloading them help though?  I downloaded them on the 386 kernel, then I downloaded and installed the 686 kernel.  But I can't boot the 686 kernel in order to download and install the nvidia drivers from there.  So would I actually be doing anything by redownloading them?

---

### Post by FIONEX on 2006-03-08
Ok scrap that post.  I figured out that there is the 686 compilation of the drivers.  Thx for your help.

---

