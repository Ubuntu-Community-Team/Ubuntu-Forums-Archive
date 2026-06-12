---
title: "Problem installing games"
date: 2006-03-07
forum: Gaming &amp; Leisure
---

### Post by Supermouse on 2006-03-07
hello boys, i'm trying to install the S.C.O.U.R.G.E game, native to linux from source, but, besides my Nvidia card being correct installed, I get the following message when trying to go ./configure:

checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
*** Hmm, you don't seem to have OpenGL libraries installed in the standard
*** location (/usr/lib).  I'll check in /usr/X11R6/lib, since
*** many distributions (incorrectly) put OpenGL libs there.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library


I have the Nvidia driver from repositories, and what I found strange is the fact that I had to install libz from source, and SDL from source (repos versions didn't worked)... installing Nvidia drivers from source is a real pain in ***, specially because my current GCC is 4.0, and kernel was compiled with 3.4 (no, I don't know how to change default C compiler...).

to bypass this, I tryed to install MesaGL drivers, but I got the following error:

../common/dri_util.h:55:17: error: drm.h: Arquivo ou diretório não encontrado
../common/dri_util.h:56:23: error: drm_sarea.h: Arquivo ou diretório não encontrado
../common/dri_util.h:57:21: error: xf86drm.h: Arquivo ou diretório não encontrado
In file included from ../common/dri_util.h:59,
                 from ../common/utils.h:33,
                 from ../common/utils.c:36:
../../../../../include/GL/internal/dri_interface.h:42:17: error: drm.h: Arquivo ou diretório não encontrado
In file included from ../common/dri_util.h:59,
                 from ../common/utils.h:33,
                 from ../common/utils.c:36:
../../../../../include/GL/internal/dri_interface.h:188: error: syntax error before ‘drm_context_t’
../../../../../include/GL/internal/dri_interface.h:200: error: syntax error before ‘drm_drawable_t’
../../../../../include/GL/internal/dri_interface.h:215: error: syntax error before ‘drm_clip_rect_t’
In file included from ../common/utils.h:33,
                 from ../common/utils.c:36:
../common/dri_util.h:233: error: syntax error before ‘drm_drawable_t’
../common/dri_util.h:233: warning: no semicolon at end of struct or union
../common/dri_util.h:261: error: ‘index’ redeclared as different kind of symbol
/usr/include/string.h:304: error: previous declaration of ‘index’ was here
../common/dri_util.h:288: error: syntax error before ‘*’ token
../common/dri_util.h:288: warning: type defaults to ‘int’ in declaration of ‘pClipRects’
../common/dri_util.h:288: warning: data definition has no type or storage class
../common/dri_util.h:301: error: syntax error before ‘*’ token
../common/dri_util.h:301: warning: type defaults to ‘int’ in declaration of ‘pBackClipRects’
../common/dri_util.h:301: warning: data definition has no type or storage class
../common/dri_util.h:329: error: syntax error before ‘}’ token
../common/dri_util.h:343: error: syntax error before ‘drm_context_t’
../common/dri_util.h:343: warning: no semicolon at end of struct or union
../common/dri_util.h:364: error: syntax error before ‘}’ token
../common/dri_util.h:443: error: syntax error before ‘drm_sarea_t’
../common/dri_util.h:443: warning: no semicolon at end of struct or union
../common/dri_util.h:509: error: syntax error before ‘}’ token
../common/dri_util.h:536: error: syntax error before ‘drm_sarea_t’
make[5]: ** [../common/utils.o] Erro 1
make[5]: Saindo do diretório `/home/supermouse/Desktop/Mesa-6.4.2/src/mesa/drivers/dri/i810'
make[4]: ** [subdirs] Erro 1
make[4]: Saindo do diretório `/home/supermouse/Desktop/Mesa-6.4.2/src/mesa/drivers/dri'
make[3]: ** [drivers-dri] Erro 2
make[3]: Saindo do diretório `/home/supermouse/Desktop/Mesa-6.4.2/src/mesa'
make[2]: ** [default] Erro 2
make[2]: Saindo do diretório `/home/supermouse/Desktop/Mesa-6.4.2/src/mesa'
make[1]: ** [subdirs] Erro 1
make[1]: Saindo do diretório `/home/supermouse/Desktop/Mesa-6.4.2/src'
make: ** [default] Erro 1



the "Arquivo ou diretório não encontrado" in the beggining means "File or directory not found".

so... what can I do? anybody got an idea? is a problem with this home-made game, or I'll can't play ANY games that requires OpenGL and SDL with the Ubuntu packages? I would try NWN, but the linux sources is more than 1Gb, and I really don't want to waste my time for nothing...

if any of you became curious with this game, the homepage is 

[http://scourge.sourceforge.net/](http://scourge.sourceforge.net/)

thanks in advance...

---

