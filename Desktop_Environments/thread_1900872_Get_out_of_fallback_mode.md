---
title: "Get out of fallback mode"
date: 2011-12-27
forum: Desktop Environments
---

### Post by mhsy on 2011-12-27
Hello,

A few days ago, I installed an update for a font renderizer, and ever since then, I have been unable to use the normal mode on my machine. Unity does not work, and Gnome 3 is stuck in fallback mode. I have tried reinstalling the display drivers, but that didn't work.

```
glxinfo | grep render
```, and other outputs give me an error:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

While my computer is still usable, I want to get it back to normal if possible. This has happened once before, but I am not sure how it got fixed...

Thanks,
Jean

---

### Post by Frogs Hair on 2011-12-27
You can get the name of the updated package name from history in the software center and attempt to reinstall it. 

Install the synaptic package manager if not already , search for the package , right click on the line where the package is located , mark for re-installation  , and select apply.

There is no direct rendering being detected for some reason . Below is the output for the computer I'm using .  ```
direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer,
```

---

### Post by mhsy on 2011-12-27
> **Frogs Hair said:**
> You can get the name of the updated package name from history in the software center and attempt to reinstall it. 

Install the synaptic package manager if not already , search for the package , right click on the line where the package is located , mark for re-installation  , and select apply.

Frogs Hair,

Thanks for the reply. I reinstalled everything that was installed over the past two weeks, but no results unfortunately. Everything is exactly the same as before.

> **Frogs Hair said:**
> There is no direct rendering being detected for some reason . Below is the output for the computer I'm using .  ```
direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer,
```
I should also add that Gnome 3 and Unity used to work perfectly before, and it did have direct rendering (I verified that previously).

I am still looking for ideas on what to do to fix it.

Thanks again!

---

### Post by mhsy on 2011-12-29
Bump?

---

### Post by mhsy on 2011-12-31
Hey,

I managed to fix the issue. It turns out that fglrx was not uninstalling properly. What I ended up doing was downloading the driver from the  ([AMD site]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")), and installing it using ```
sudo sh ./ati-driver-installer-11-12-x86.x86_64.run --force
```After that, I ran the uninstall script, and everything worked properly.

Marking as solved.

---

