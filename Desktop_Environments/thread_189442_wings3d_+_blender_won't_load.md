---
title: "wings3d + blender won't load"
date: 2006-06-05
forum: Desktop Environments
---

### Post by MKR. on 2006-06-05
I installed wings3d and blender using synaptic and tried to load them. With wings, some output can be seen in the erlang console, but it closes too fast for me to see it.

Blender doesn't seem to do anything. I've tried them in gnome and KDE, and it happens in both, so I don't think it's the WM.

I know this is a bit vague, but I'm not sure of what information would be needed to fix this. ](*,)

Edit: The same thing happens with the graphical traceroute client.

It might also be useful to mention that I have an ATI Radeon 9250; could that be having some effect?

---

### Post by grigpi on 2006-06-05
If you start from the terminal, what's the output ?

---

### Post by MKR. on 2006-06-05
[QUOTE=wings3d]mkr@Ninjamatic:~$ wings3d
Erlang (BEAM) emulator version 5.4.9 [source] [threads:0]

Eshell V5.4.9  (abort with ^G)
1> Trying OpenGL modes
  [{buffer_size,32},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,8},{accum_size,16}]
Actual: RGBA: 8 8 8 8 Depth: 24 Stencil: 8 Accum: 16 16 16 16
drmCommandWrite: -22
                    drmRadeonCmdBuffer: -22 (exiting)
                                                     mkr@Ninjamatic:~$
[/QUOTE]

[QUOTE=blender]
mkr@Ninjamatic:~$ blender
Using Python version 2.4
drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)
mkr@Ninjamatic:~$

[/QUOTE]

This might have something to do with it:
[QUOTE=dmesg output]
mkr@Ninjamatic:~$ dmesg | grep radeon
[4294710.502000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4296999.389000] [drm:radeon_check_and_fixup_packets] *ERROR* Invalid depth buffer offset
[4296999.389000] [drm:radeon_emit_packets] *ERROR* Packet verification failed
[4296999.389000] [drm:radeon_cp_cmdbuf] *ERROR* radeon_emit_packets failed
[4297011.568000] [drm:radeon_cp_dispatch_texture] *ERROR* Invalid destination offset
[4327287.866000] [drm:radeon_check_and_fixup_packets] *ERROR* Invalid depth buffer offset
[4327287.866000] [drm:radeon_emit_packets] *ERROR* Packet verification failed
[4327287.866000] [drm:radeon_cp_cmdbuf] *ERROR* radeon_emit_packets failed
[4327436.278000] [drm:radeon_check_and_fixup_packets] *ERROR* Invalid depth buffer offset
[4327436.279000] [drm:radeon_emit_packets] *ERROR* Packet verification failed
[4327436.279000] [drm:radeon_cp_cmdbuf] *ERROR* radeon_emit_packets failed

[/QUOTE]

---

### Post by MKR. on 2006-06-05
It seems removing ATI's broken binary driver fixed the problem.
Edit: ...which wrecked my xconf, forcing me to restore it by stealing a copy from the livecd's ramdisk; now the problem is back.

---

