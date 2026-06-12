---
title: "Cant play neverwinter nights ubuntu 10.10 64 bits"
date: 2010-11-24
forum: Gaming &amp; Leisure
---

### Post by Lancro on 2010-11-24
I have searched in google, I have searched in forums, I have tried almost everything, so I ask a genius fix, lets start with the issue... (The game is the spanish version)

I execute ./fixinstall, It tells me everything is ok, I execute ./nwn and it tells me that 

```
./nwmain: error while loading shared libraries: ./miles/libmss.so.6: file too short 
```

So I do the following, I go to /miles directory, I delete libmss.so.6, I copy libmss.so.6.5.2 to the same folder as a copy, I rename it to libmss.so.6, and then I execute ./nwn, and we go to the next error, the same as before but with libSDL-1.2.so.0, so I delete it and substitute it with libSDL-1.2.so.0.0.5, and execute ./nwn, then it opens, no sound, I press new, create a new character, and it goes out with the message

```
Segmentation fault 
```

If I execute it with double click in nautilus, It sounds, but same, at creating new character, it terminates.

I have looked the opengl with glxinfo | grep render, the output is:

```
direct rendering: Yes
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```

I have made all directories and archives executable, all 777, I have modified the nwn.ini to take out the ./lib, and I dont know what to try now, Im desesperated, anyone can help me?.

Thanks.

---

### Post by oldrocker99 on 2010-11-24
You do have the ia32 libs installed, right?

---

### Post by Lancro on 2010-11-24
I have just looked into synaptic and ia32-libs are installed yes.

---

### Post by Lancro on 2010-11-25
Solved patching.

Thanks.

---

### Post by jethro1138 on 2010-11-29
> **Lancro said:**
> Solved patching.

Thanks.

Care to share how you solved this? (:

---

