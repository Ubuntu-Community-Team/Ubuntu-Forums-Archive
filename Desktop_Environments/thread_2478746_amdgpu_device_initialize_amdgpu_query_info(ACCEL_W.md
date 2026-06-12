---
title: "amdgpu_device_initialize: amdgpu_query_info(ACCEL_WORKING) failed (-13)"
date: 2022-09-04
forum: Desktop Environments
---

### Post by pchaffey on 2022-09-04
Hi, 
I'm using Kubuntu 22:04 and I'm using the KDE backports so:
KDE Plasma 5.25.4

My desktop is using AMD Radeon RX 580.

when I run eglinfo I get the following:

```
GBM platform:
amdgpu_device_initialize: amdgpu_query_info(ACCEL_WORKING) failed (-13)
amdgpu: amdgpu_device_initialize failed.
EGL API version: 1.4
EGL vendor string: Mesa Project
EGL version string: 1.4
EGL client APIs: OpenGL OpenGL_ES 
EGL extensions string:
...
```

But when running as root, eglinfo reports:

```
GBM platform:
EGL API version: 1.5
EGL vendor string: Mesa Project
EGL version string: 1.5
EGL client APIs: OpenGL OpenGL_ES 
EGL extensions string:
    EGL_ANDROID_blob_cache EGL_ANDROID_native_fence_sync
    EGL_EXT_buffer_age EGL_EXT_create_context_robustness
    EGL_EXT_image_dma_buf_import EGL_EXT_image_dma_buf_import_modifiers
    EGL_KHR_cl_event2 EGL_KHR_config_attribs EGL_KHR_create_context

Note:sudo eglinfo uses a different version of EGL
```

so, I believe this seems to be a permissions issue and also I have made sure my user is in the video group.

I think that I am not getting HW acceleration currently, Does anyone have an idea where to proceed to track this down ?

---

### Post by webjester2 on 2023-02-12
Running into this same behavior.

GPU: 7900 XTX
kubuntu 22.04
Kernel: 6.1.11-x64v3-xanmod1 (also tested with linux-oem-22.04c)
Additional PPA: oibaf (MESA 23.1-git)

In my case, the issue occurs when removing [FONT=courier new]libgl1-amber-dri[/FONT] in favor of [FONT=courier new]libgl1-mesa-dri[/FONT]. [FONT=courier new]libgl1-amber-dri[/FONT] is no longer maintained by MESA.

Running as standard user (even with video and render group membership) I am getting initilization failures:

$ eglinfo

```
EGL client extensions string:
    EGL_EXT_device_base EGL_EXT_device_enumeration EGL_EXT_device_query
    EGL_EXT_platform_base EGL_KHR_client_get_all_proc_addresses
    EGL_EXT_client_extensions EGL_KHR_debug EGL_EXT_platform_device
    EGL_EXT_platform_wayland EGL_KHR_platform_wayland
    EGL_EXT_platform_x11 EGL_KHR_platform_x11 EGL_EXT_platform_xcb
    EGL_MESA_platform_gbm EGL_KHR_platform_gbm
    EGL_MESA_platform_surfaceless

GBM platform:
amdgpu_device_initialize: amdgpu_query_info(ACCEL_WORKING) failed (-13)
amdgpu: amdgpu_device_initialize failed.
amdgpu_device_initialize: amdgpu_query_info(ACCEL_WORKING) failed (-13)
amdgpu: amdgpu_device_initialize failed.
EGL API version: 1.5
EGL vendor string: Mesa Project
EGL version string: 1.5
EGL client APIs: OpenGL OpenGL_ES  
EGL extensions string:
    EGL_ANDROID_blob_cache EGL_EXT_buffer_age
    EGL_EXT_create_context_robustness EGL_EXT_image_dma_buf_import
    EGL_EXT_image_dma_buf_import_modifiers EGL_KHR_cl_event2
    EGL_KHR_config_attribs EGL_KHR_context_flush_control
    EGL_KHR_create_context EGL_KHR_create_context_no_error
    EGL_KHR_fence_sync EGL_KHR_get_all_proc_addresses
    EGL_KHR_gl_colorspace EGL_KHR_gl_renderbuffer_image
    EGL_KHR_gl_texture_2D_image EGL_KHR_gl_texture_3D_image
    EGL_KHR_gl_texture_cubemap_image EGL_KHR_image EGL_KHR_image_base
    EGL_KHR_image_pixmap EGL_KHR_no_config_context EGL_KHR_reusable_sync
    EGL_KHR_surfaceless_context EGL_EXT_pixel_format_float
    EGL_KHR_wait_sync EGL_MESA_configless_context
    EGL_MESA_image_dma_buf_export EGL_MESA_query_driver
```


Which do not occur when running with elevated permissions:

$ sudo eglinfo

```
EGL client extensions string:
    EGL_EXT_device_base EGL_EXT_device_enumeration EGL_EXT_device_query
    EGL_EXT_platform_base EGL_KHR_client_get_all_proc_addresses
    EGL_EXT_client_extensions EGL_KHR_debug EGL_EXT_platform_device
    EGL_EXT_platform_wayland EGL_KHR_platform_wayland
    EGL_EXT_platform_x11 EGL_KHR_platform_x11 EGL_EXT_platform_xcb
    EGL_MESA_platform_gbm EGL_KHR_platform_gbm
    EGL_MESA_platform_surfaceless

GBM platform:
EGL API version: 1.5
EGL vendor string: Mesa Project
EGL version string: 1.5
EGL client APIs: OpenGL OpenGL_ES  
EGL extensions string:
    EGL_ANDROID_blob_cache EGL_ANDROID_native_fence_sync
    EGL_EXT_buffer_age EGL_EXT_create_context_robustness
    EGL_EXT_image_dma_buf_import EGL_EXT_image_dma_buf_import_modifiers
    EGL_IMG_context_priority EGL_KHR_cl_event2 EGL_KHR_config_attribs
    EGL_KHR_context_flush_control EGL_KHR_create_context
    EGL_KHR_create_context_no_error EGL_KHR_fence_sync
    EGL_KHR_get_all_proc_addresses EGL_KHR_gl_colorspace
    EGL_KHR_gl_renderbuffer_image EGL_KHR_gl_texture_2D_image
    EGL_KHR_gl_texture_3D_image EGL_KHR_gl_texture_cubemap_image
    EGL_KHR_image EGL_KHR_image_base EGL_KHR_image_pixmap
    EGL_KHR_no_config_context EGL_KHR_reusable_sync
    EGL_KHR_surfaceless_context EGL_EXT_pixel_format_float
    EGL_KHR_wait_sync EGL_MESA_configless_context EGL_MESA_drm_image
    EGL_MESA_image_dma_buf_export EGL_MESA_query_driver
    EGL_WL_bind_wayland_display

```

---

