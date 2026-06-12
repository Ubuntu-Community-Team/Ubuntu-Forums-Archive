---
title: "Who can solve this? [BIG PROBLEM]"
date: 2005-12-21
forum: General Help
---

### Post by Prudentissimus on 2005-12-21
> arts'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. arts.c audio.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/winearts'
cd `dirname winmm/wineaudioio/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/wineaudioio'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c audioio.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/wineaudioio'
cd `dirname winmm/winejack/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/winejack'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c jack.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/winejack'
cd `dirname winmm/winenas/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/winenas'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c nas.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/winenas'
cd `dirname winmm/wineoss/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/wineoss'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c midi.c midipatch.c mixer.c mmaux.c oss.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winmm/wineoss'
cd `dirname winnls/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winnls'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winnls.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winnls'
cd `dirname winsock/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winsock'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winsock/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. sock.c      testlist.c
make[3]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winsock/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. async.c socket.c socket16.c version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winsock'
cd `dirname winspool/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winspool'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/winspool/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. info.c      testlist.c
make[3]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winspool/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. info.c wspool.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/winspool'
cd `dirname wintab32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/wintab32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. context.c manager.c wintab32.c wintab16.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/wintab32'
cd `dirname wintrust/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/wintrust'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wintrust_main.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/wintrust'
cd `dirname wow32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/wow32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wow_main.c 
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/wow32'
cd `dirname wsock32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/wsock32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. protocol.c service.c socket.c  version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/wsock32'
cd `dirname d3d8/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/d3d8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. basetexture.c cubetexture.c d3d8_main.c device.c directx.c drawprim.c indexbuffer.c resource.c shader.c stateblock.c surface.c swapchain.c texture.c utils.c vertexbuffer.c volume.c volumetexture.c vshaderdeclaration.c  version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/d3d8'
cd `dirname d3d9/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/d3d9'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. basetexture.c cubetexture.c d3d9_main.c device.c directx.c indexbuffer.c pixelshader.c query.c resource.c stateblock.c surface.c swapchain.c texture.c vertexbuffer.c vertexdeclaration.c vertexshader.c volume.c volumetexture.c  version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/d3d9'
cd `dirname d3dx8/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/d3dx8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. d3dx8_main.c d3dxbuffer.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/d3dx8'
cd `dirname ddraw/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/ddraw'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/ddraw/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. ddrawmodes.c      testlist.c
make[3]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/ddraw/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. convert.c dclipper/main.c ddraw/hal.c ddraw/main.c ddraw/thunks.c ddraw/user.c dpalette/hal.c dpalette/main.c dsurface/dib.c dsurface/fakezbuffer.c dsurface/gamma.c dsurface/hal.c dsurface/main.c dsurface/thunks.c dsurface/user.c dsurface/wndproc.c helper.c main.c regsvr.c struct_convert.c  version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/ddraw'
cd `dirname dxerr8/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/dxerr8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dxerr8.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/dxerr8'
cd `dirname dxerr9/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/dxerr9'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dxerr9.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/dxerr9'
cd `dirname dxguid/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/dxguid'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dx8guid.c dx9guid.c dxguid.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/dxguid'
cd `dirname glu32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/glu32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. glu.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/glu32'
cd `dirname glut32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/glut32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. glut.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/glut32'
cd `dirname opengl32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/opengl32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. opengl_ext.c opengl_norm.c wgl.c wgl_ext.c  version.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/opengl32'
cd `dirname uuid/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/uuid'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. uuid.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/uuid'
cd `dirname wined3d/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/wined3d'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. vertexshader.c wined3d_main.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/wined3d'
cd `dirname x11drv/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/dlls/x11drv'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. bitblt.c bitmap.c brush.c clipboard.c clipping.c codepage.c desktop.c dga2.c dib.c dib_convert.c dib_dst_swap.c dib_src_swap.c event.c graphics.c init.c keyboard.c mouse.c opengl.c palette.c pen.c scroll.c settings.c text.c window.c winpos.c wintab.c x11ddraw.c x11drv_main.c xdnd.c xfont.c xim.c xrandr.c xrender.c xvidmode.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls/x11drv'
../tools/makedep -I. -I. -I../include -I../include  -C.
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/dlls'
cd `dirname documentation/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/documentation'
../tools/makedep -I. -I. -I../include -I../include  -C.
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/documentation'
cd `dirname include/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/include'
../tools/makedep -I. -I. -I../include -I../include  -C.      amstream.idl amvideo.idl austream.idl comcat.idl ddstream.idl docobj.idl exdisp.idl mmstream.idl oaidl.idl objidl.idl ocidl.idl oleidl.idl pstore.idl servprov.idl shldisp.idl shobjidl.idl shtypes.idl strmif.idl unknwn.idl urlmon.idl wtypes.idl
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/include'
cd `dirname libs/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/libs'
cd `dirname port/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/port'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. fstatvfs.c getopt.c getopt1.c getpagesize.c gettid.c interlocked.c lstat.c memcpy_unaligned.c memmove.c mkstemps.c pread.c pwrite.c readlink.c sigsetjmp.c spawn.c statvfs.c strcasecmp.c strerror.c strncasecmp.c usleep.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/port'
cd `dirname unicode/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/unicode'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. casemap.c collation.c compose.c cptable.c fold.c mbtowc.c sortkey.c string.c utf8.c wctomb.c wctype.c c_037.c c_424.c c_437.c c_500.c c_737.c c_775.c c_850.c c_852.c c_855.c c_856.c c_857.c c_860.c c_861.c c_862.c c_863.c c_864.c c_865.c c_866.c c_869.c c_874.c c_875.c c_878.c c_932.c c_936.c c_949.c c_950.c c_1006.c c_1026.c c_1250.c c_1251.c c_1252.c c_1253.c c_1254.c c_1255.c c_1256.c c_1257.c c_1258.c c_10000.c c_10006.c c_10007.c c_10029.c c_10079.c c_10081.c c_20866.c c_20932.c c_28591.c c_28592.c c_28593.c c_28594.c c_28595.c c_28596.c c_28597.c c_28598.c c_28599.c c_28600.c c_28603.c c_28604.c c_28605.c c_28606.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/unicode'
cd `dirname wine/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/wine'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. config.c debug.c ldt.c loader.c mmap.c port.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/wine'
cd `dirname wpp/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/wpp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. preproc.c wpp.c      ppy.y ppl.l
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/wpp'
../tools/makedep -I. -I. -I../include -I../include  -C.
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs'
cd `dirname loader/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/loader'
../tools/makedep -I. -I. -I../include -I../include  -C. glibc.c kthread.c main.c preloader.c pthread.c
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/loader'
cd `dirname programs/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/programs'
cd `dirname avitools/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/avitools'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. aviinfo.c aviplay.c icinfo.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/avitools'
cd `dirname clock/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/clock'../../tools/makedep -I. -I. -I../../include -I../../include  -C. license.c main.c winclock.c License_En.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/clock'
cd `dirname cmdlgtst/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/cmdlgtst'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cmdlgtst.c  cmdlgr.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/cmdlgtst'
cd `dirname control/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/control'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. control.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/control'
cd `dirname expand/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/expand'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. expand.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/expand'cd `dirname notepad/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/notepad'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. License_En.c dialog.c license.c main.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/notepad'
cd `dirname progman/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/progman'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dialog.c group.c grpfile.c license.c main.c program.c string.c License_En.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/progman'
cd `dirname regedit/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/regedit'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. about.c childwnd.c edit.c framewnd.c listview.c main.c regedit.c regproc.c treeview.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/regedit'
cd `dirname regsvr32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/regsvr32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. regsvr32.c  regsvr32.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/regsvr32'
cd `dirname rpcss/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/rpcss'../../tools/makedep -I. -I. -I../../include -I../../include  -C. epmap_server.c np_server.c rpcss_main.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/rpcss'
cd `dirname rundll32/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/rundll32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. rundll32.c 
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/rundll32'
cd `dirname start/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/start'../../tools/makedep -I. -I. -I../../include -I../../include  -C. start.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/start'
cd `dirname taskmgr/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/taskmgr'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. about.c affinity.c applpage.c column.c dbgchnl.c debug.c endproc.c graph.c graphctl.c optnmenu.c perfdata.c perfpage.c priority.c proclist.c procpage.c run.c taskmgr.c trayicon.c  taskmgr.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/taskmgr'
cd `dirname uninstaller/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/uninstaller'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/uninstaller'
cd `dirname view/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/view'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. init.c view.c winmain.c  viewrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/view'
cd `dirname wcmd/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/wcmd'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. batch.c builtins.c directory.c wcmdmain.c  wcmdrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/wcmd'
cd `dirname wineboot/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/wineboot'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wineboot.c 
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/wineboot'
cd `dirname winebrowser/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winebrowser'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winebrowser'
cd `dirname winecfg/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winecfg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. appdefaults.c audio.c drive.c libraries.c main.c properties.c winecfg.c x11drvdlg.c  winecfg.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winecfg'
cd `dirname wineconsole/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/wineconsole'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. curses.c dialog.c registry.c user.c wineconsole.c  wineconsole_res.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/wineconsole'
cd `dirname winedbg/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winedbg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. be_i386.c be_ppc.c break.c db_disasm.c display.c expr.c gdbproxy.c info.c memory.c source.c symbol.c stack.c types.c winedbg.c      dbg.y debug.l
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winedbg'
cd `dirname winefile/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winefile'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. license.c splitpath.c winefile.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winefile'
cd `dirname winemenubuilder/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winemenubuilder'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winemenubuilder.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winemenubuilder'
cd `dirname winemine/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winemine'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dialog.c main.c  rsrc.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winemine'
cd `dirname winepath/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winepath'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winepath.c 
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winepath'
cd `dirname winetest/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winetest'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. gui.c main.c send.c util.c  winetest.rc
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winetest'
cd `dirname winevdm/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winevdm'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winevdm.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winevdm'
cd `dirname winhelp/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winhelp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winhelp.c hlpfile.c macro.c string.c  rsrc.rc    macro.lex.l
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winhelp'
cd `dirname winver/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/programs/winver'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winver.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs/winver'../tools/makedep -I. -I. -I../include -I../include  -C.
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/programs'
cd `dirname server/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/server'
../tools/makedep -I. -I. -I../include -I../include  -C. async.c atom.c change.c class.c clipboard.c console.c context_i386.c context_powerpc.c context_sparc.c debugger.c event.c fd.c file.c handle.c hook.c main.c mapping.c mutex.c named_pipe.c object.c process.c ptrace.c queue.c registry.c request.c semaphore.c serial.c signal.c snapshot.c sock.c thread.c timer.c token.c trace.c unicode.c user.c window.c
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/server'
cd `dirname tools/__depend__` && make depend
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/tools'
cd `dirname widl/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/widl'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. header.c proxy.c typelib.c utils.c widl.c      parser.y parser.l
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/widl'
cd `dirname winebuild/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winebuild'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. import.c main.c parser.c relay.c res16.c res32.c spec16.c spec32.c utils.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winebuild'cd `dirname winedump/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winedump'../../tools/makedep -I. -I. -I../../include -I../../include  -C. debug.c main.c misc.c msmangle.c ne.c output.c pe.c search.c symbol.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winedump'
cd `dirname winegcc/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winegcc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. utils.c winegcc.c
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winegcc'
cd `dirname wmc/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/wmc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. lang.c mcl.c utils.c wmc.c write.c      mcy.y
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/wmc'
cd `dirname wrc/__depend__` && make depend
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/wrc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dumpres.c genres.c newstruc.c readres.c translation.c utils.c wrc.c writeres.c      parser.y parser.l
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/wrc'
../tools/makedep -I. -I. -I../include -I../include  -C. bin2res.c fnt2bdf.c makedep.c
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools'
./tools/makedep -I. -I. -I./include -I./include  -C.
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/libs'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/port'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/unicode'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/unicode'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/wine'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs/wpp'
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/libs'
make[1]: Entering directory `/home/prudens/Desktop/wine-20040615/tools'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/widl'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winebuild'make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winedump'make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winedump'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/winegcc'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/wmc'
make[2]: Entering directory `/home/prudens/Desktop/wine-20040615/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:805: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:916: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/prudens/Desktop/wine-20040615/tools'
make: *** [tools] Error 2

Compilation failed, aborting install.




Trying to install Wine 20040615 ( I heard this is the only version that would run ConquerOnline )


Please help.

---

### Post by newuser111 on 2005-12-21
i was able to install old wine versions from this site [http://prdownloads.sourceforge.net/wine](http://prdownloads.sourceforge.net/wine)

use alien to convert the rpm and install with dpkg -i, it worked quite well, but i prefer the newer wine version

btw i recommend 20041019 rather than 20040615, but you can try either one

---

