---
title: "Patching wine"
date: 2014-02-22
forum: Gaming &amp; Leisure
---

### Post by cybuss on 2014-02-22
Hello im trying to patch wine to play napoleon total war using this guide. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19292&iTestingId=46961](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19292&iTestingId=46961) 
 with the context downloaded from mark strout towards the bottom and i get this error 
context.c:1397:9: warning: implicit declaration of function ‘pwglShareLists’ [-Wimplicit-function-declaration]
         if (!pwglShareLists(device->contexts[0]->glCtx, ctx))
         ^
context.c:1577:11: error: ‘struct wined3d_device’ has no member named ‘frag_pipe’
     device->frag_pipe->enable_extension(gl_info, TRUE);
           ^
context.c: In function ‘SetupForBlit’:
context.c:1873:11: error: ‘const struct wined3d_device’ has no member named ‘frag_pipe’
     device->frag_pipe->enable_extension(gl_info, FALSE);
           ^
context.c: In function ‘context_apply_clear_state’:
context.c:2233:15: error: ‘const struct wined3d_device’ has no member named ‘frag_pipe’
         device->frag_pipe->enable_extension(gl_info, TRUE);
               ^
context.c: In function ‘context_apply_draw_state’:
context.c:2352:38: error: ‘const struct wined3d_state’ has no member named ‘user_stream’
     if (state->index_buffer && !state->user_stream)
                                      ^
context.c:2362:15: error: ‘struct wined3d_device’ has no member named ‘frag_pipe’
         device->frag_pipe->enable_extension(context->gl_info, TRUE);
               ^
context.c: In function ‘context_acquire’:
context.c:2502:19: error: ‘const struct wined3d_device’ has no member named ‘frag_pipe’
             device->frag_pipe->enable_extension(context->gl_info, !context->last_was_blit);
                   ^
make[1]: *** [context.o] Error 1
make[1]: Leaving directory `/home/basil/Desktop/wine-1.5.22/dlls/wined3d'
make: *** [dlls/wined3d] Error 2
is this a error that could break wine if i make install? any insight would be helpful xD

---

