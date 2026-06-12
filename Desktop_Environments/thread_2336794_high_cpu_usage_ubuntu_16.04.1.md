---
title: "high cpu usage ubuntu 16.04.1"
date: 2016-09-11
forum: Desktop Environments
---

### Post by ppito2 on 2016-09-11
Hello,

  since i installed this version i have a slow computer. When i use  firefox sometimes cpu usage exceeds 100%, but when i use totem or vlc  with 1080p videos exceeds 300%. My computer is a  intel core i5 2430m 2.4ghz , 4gb ram and a 2gb  dedicated nvidia graphic card.

  I have deactivated compiz special effects. But i don't know what to do now. :confused:

  top example:

```
 10101 ppito     20   0 2196704 164884  63072 S 313,6  4,2   1:45.42 totem
 3523 root      20   0  383012  12792   8044 S   7,0  0,3   0:01.46 udisksd
 3520 ppito     20   0 1614172 268484  60164 S   5,6  6,8   7:41.96 compiz
 2648 root      20   0  509284  78140  64672 S   4,7  2,0  14:56.02 Xorg
 3431 ppito      9 -11  442532  13216  10100 S   1,7  0,3   2:20.65 pulseaudio
 8662 ppito     20   0 1198868 375380 109908 S   1,7  9,5   2:54.29 firefox   

```
Thank you a lot.

---

### Post by ajgreeny on 2016-09-11
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by DuckHook on 2016-09-11
Please post output of:```
lspci -vk | grep -iA13 vga
``````
cat /etc/default/grub
``````
glxinfo | grep render
```…if the last command returns something like "app not installed", then first do:```
sudo apt install mesa-utils
```…and run the command again.

I'm suspecting that your CPU is being used to render graphics.

---

### Post by ppito2 on 2016-09-12
Good morning, thank you for your help.:P

lspci -vk | grep -iA13 vga
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at dc400000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

--
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GF108M [GeForce GT 540M]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
```

cat /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

glxinfo | grep render
```
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 


```

---

### Post by DuckHook on 2016-09-12
You may have a nVidia GPU but your OS is not using it. It is instead using an Intel graphics chip that is much less powerful than your nVidia. My guess is that you have a laptop with one of those hybrid graphics systems where the OS is supposed to use the low powered graphics for standard work but kick in the nVidia for graphically intensive work (like gaming or video). These systems were built to run smoothly on Windows. Linux is known to have problems effectively using such hybrid graphics. Your driver does not indicate software rendering, but for all I know, your CPU could be doing most of the rendering work anyway because I really have no idea how much power your Intel GPU has.

To be frank, I'm out of my depth on such systems (my newest laptop is 8 years old) and know only what I've gleaned from similar issues on these forums. Hopefully, others here will be of better help.

---

### Post by ppito2 on 2016-09-12
Thank you for your help. I have installed another driver (nvidia-364.19). Now nvidia gpu seems to be working but the computer i think is not using the better perfomance for videos.

(new)  
glxinfo | grep render

```
direct rendering: Yes
OpenGL renderer string: GeForce GT 540M/PCIe/SSE2
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_KTX_buffer_region, GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_ARB_compute_variable_group_size, GL_ARB_conditional_render_inverted, 
    GL_KTX_buffer_region, GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_EXT_primitive_bounding_box, GL_EXT_render_snorm, GL_EXT_robustness, 
    GL_NV_blend_equation_advanced, GL_NV_conditional_render, 
    GL_NV_packed_float_linear, GL_NV_path_rendering, 
    GL_OES_fbo_render_mipmap, GL_OES_geometry_point_size,
```


Thanks!

---

### Post by DuckHook on 2016-09-12
You are, indeed, now using the nVidia. Just keep an eye on your system temperature. Some people have reported high temps and bad battery life after they've switched over to the high-end graphics chip. Your video should be really powerful at this point. If your CPU usage is still high, then my initial guess is incorrect and something else is wrong rather than the video subsystem. Does *top* still show 300% CPU usage while running Totem? If so, please take a snapshot and post back to this thread.

---

### Post by ppito2 on 2016-09-13
Good morning, 
top indicates  better perfomance, but nvidia-settings shows graphic card is not used completely . Now i have problems of flikering
top:
```
 4071 ppito     20   0 2244288 214016  94284 S 151,8  5,4   0:33.25 totem       
 3405 ppito 20   0 1221404 137984  77412 S   9,0  3,5   0:14.93 compiz      
 2667 root      20   0  276132  64064  37364 S   6,0  1,6   0:24.67 Xorg        
 3322 ppito 9 -11  507944  11976   8972 S   0,7  0,3   0:00.47 pulseaudio  
 2175 root     -51   0       0      0      0 S   0,3  0,0   0:02.92 irq/34-iwl+ 
 3125 ppito 20   0  439300   8788   7408 S   0,3  0,2   0:00.36 ibus-daemon 
 3897 ppito 20   0  662988  36400  29104 S   0,3  0,9   0:01.80 gnome-term+
 3915 ppito 20   0   49072   3956   3220 R   0,3  0,1   0:02.09 top         
    1 root      20   0  119652   5896   4068 S   0,0  0,1   0:01.59 systemd     
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.02 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+ 
    6 root      20   0       0      0      0 S   0,0  0,0   0:00.61 kworker/u3+ 
    7 root      20   0       0      0      0 S   0,0  0,0   0:01.07 rcu_sched   
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0 
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0
```
pics of nvidia-settings

[https://s10.postimg.io/5s6wmsebt/nvidia.png](https://s10.postimg.io/5s6wmsebt/nvidia.png)

[https://s22.postimg.io/ytyef4o29/nvidia2.png](https://s22.postimg.io/ytyef4o29/nvidia2.png)

---

### Post by DuckHook on 2016-09-14
Your CPU usage is about half what it was, but still too high. Try invoking *totem* from the command line. This will give you a running output for feedback on what is happening.

The fact that your nVidia chip is not being utilized fully is a good thing and normal operations. Video should not tax a GPU such as your fully. It's really light duty for something as powerful as yours.

---

### Post by ppito2 on 2016-09-14
Nothing with totem. I have tried your tip with openshot that is another program i use.  I see a lot of lines with this error...i don't think there is a relationship..
```
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x46e0d20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47ef420] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x46f16c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47606c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x473cbe0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x473b3a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x476f9a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x479f9e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47e7ea0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47766e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47df2e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x477e740] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x47a8a40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4c2c0e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4931f20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f2f160] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f358a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4924fa0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4916a60] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4bf1700] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4925000] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f51380] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b8b980] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4bef700] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4c15220] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4c16c00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4c6c7a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b7c940] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f2a5a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4bcd680] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b424a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b6c320] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x539e620] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b98bc0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4bc0200] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4b9eda0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4e7e340] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4eb1d80] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4e95e40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a89960] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a79540] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a77560] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4ea2c00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4eac780] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x536efc0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5394380] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5368c60] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a32f40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a3e120] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5364280] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x592c1e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x535db40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x57b0940] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f052c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f063e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59a8aa0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4f1b100] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x57d3fc0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4eff300] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4efe700] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59dc000] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59af3e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x4efb800] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5a1ece0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59eb840] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x61148c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5fd4f20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59a6c80] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62822c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59f8700] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x60eb540] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x596b740] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5fb7080] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5fb7e00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62ffea0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5957cc0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59620a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59a51e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x5999120] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x59a02a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x627d740] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x680c620] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6830160] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62fe920] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6247560] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6e27d60] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6ddf0e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6e212c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62f4f00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6230940] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6967e00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6dea940] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6e023e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6ddf9c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6de6880] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6bb9d80] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6ce1400] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6ce4500] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62f2200] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6dddee0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6cf0500] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6dc8e80] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6dcb6e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d0fb20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62f1620] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d07b40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d45da0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d08b40] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d37380] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62eea20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62ed8e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6d722c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x629f9c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62a1c60] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x62a92e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x74e6b20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x74cfc20] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x628dec0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x74cb960] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x74cfce0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x74cab60] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x73880c0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x78a2680] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x6290660] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x78530e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7859120] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x784f760] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7851ae0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x78998e0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7fb2c8007d00] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7fb2c800f7a0] unsupported color_parameter_type aclc
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7fb2c8064560] unsupported color_parameter_type aclc


```

now, using the gpu, i have flikering problems, with all windows and programs :(

---

### Post by DuckHook on 2016-09-15
I'm running out of suggestions for you (I'm not a video guru). The only thing I could find was this following link: [http://robert.penz.name/916/solution-for-high-cpu-load-when-using-the-flash-player-in-the-browser-on-linux/](http://robert.penz.name/916/solution-for-high-cpu-load-when-using-the-flash-player-in-the-browser-on-linux/)

Please try the linked solution. If it doesn't work, you can always back out the changes.

---

### Post by DuckHook on 2016-09-15
Please also do:```
lspci -vk | grep -iA18 vga
```Let's see what driver is installed for your nVidia.

---

### Post by ppito2 on 2016-09-15
you are giving me a lot of help!
 im going to try the linked solution.
Thank you!


***lspci -vk | grep -iA13 vga***
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at dc400000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family MEI Controller
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GF108M [GeForce GT 540M]
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at db000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    [virtual] Expansion ROM at dc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
    Subsystem: Intel Corporation Centrino Wireless-N 100 BGN
```

---

### Post by ppito2 on 2016-09-18
ouch, i have tried 361,364,367 and 370 driver, same problem. please if you know anybody with more ideas is welcomed :)

---

### Post by _duncan_ on 2016-09-18
This is more than just a graphics card driver problem. My desktop PC has the following lower specs:

- 4th gen i3 processor.
- built-in graphics with the same specs as your on-board graphics.
- no other graphics card.
- only 2 GB memory.

For comparison purposes, I played a video using vlc and cpu usage for vlc is only about 7%.

Anyway, I'm not knowledgeable enough to help you troubleshoot the problem, but I don't think this is a graphics card problem.

---

### Post by DuckHook on 2016-09-18
I agree with _duncan_. Did not think it was GPU-related, but had to start somewhere. I found this: [https://ubuntuforums.org/showthread.php?t=2319043](https://ubuntuforums.org/showthread.php?t=2319043)

It involves some surgery to your system and may not even be the problem. I direct your attention to post #9 where OP says:> **tbzep said:**
> &#8230;I removed all mpeg related libraries, then let totem search for and install.This has some similarities to your issue, where the problem may be mpeg and Totem related.

---

### Post by ppito2 on 2016-09-25
i have reinstalled plugins, same problems. Im thinking to downgrade to ubuntu 14.04[ATTACH=CONFIG]271345[/ATTACH]

pic of htop+openshot.

Thank you to all of you

---

### Post by nlann on 2017-02-07
Hello
Please tell me, after downgrading to 14.04 the problem is solved?
Thank you

---

