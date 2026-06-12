---
title: "Compiled WineD3D for Windows fails"
date: 2009-06-05
forum: General Help
---

### Post by matchu on 2009-06-05
Hi,

Following the instructions [here]("http://wiki.winehq.org/WineD3DOnWindows") I attempt to build the WineD3D dlls from source. The source code is present, and mingw32 is installed. Each attempted dll build, however, has an output similar to this:

```
make: Entering directory `/home/matchu/wine-win32/dlls/wined3d'
../../../wine-tools/tools/winegcc/winegcc -b i586-mingw32msvc  -B../../../wine-tools/tools/winebuild --sysroot=../.. -shared ../../../wine-git/dlls/wined3d/wined3d.spec arb_program_shader.o ati_fragment_shader.o baseshader.o basetexture.o buffer.o clipper.o context.o cubetexture.o device.o directx.o drawprim.o gl_compat.o glsl_shader.o nvidia_texture_shader.o palette.o pixelshader.o query.o resource.o shader_sm1.o shader_sm4.o state.o stateblock.o surface_base.o surface.o surface_gdi.o swapchain.o swapchain_gdi.o swapchain_base.o texture.o utils.o vertexdeclaration.o vertexshader.o view.o volume.o volumetexture.o wined3d_main.o       -o wined3d.dll  -luuid -luser32 -lgdi32 -ladvapi32 -lkernel32  ../../libs/port/libwine_port.a   
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lwinecrt0
collect2: ld returned 1 exit status
i586-mingw32msvc-dllwrap: i586-mingw32msvc-gcc exited with status 1
winegcc: i586-mingw32msvc-dllwrap failed
make: *** [wined3d.dll] Error 2
make: Leaving directory `/home/matchu/wine-win32/dlls/wined3d'
```

I can't even begin to figure out what that is supposed to mean. Any thoughts? --Matchu

EDIT: Reached a resolution of sorts. My issue was that I couldn't make the auto-installer ([http://www.nongnu.org/wined3d/](http://www.nongnu.org/wined3d/)) run on Windows 7 correctly. Instead I tried an XP VM, and it worked.

...wow, I feel silly.

---

