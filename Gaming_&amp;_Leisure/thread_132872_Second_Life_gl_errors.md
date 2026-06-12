---
title: "Second Life gl errors"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by aljones15 on 2006-02-19
I got a never ending problems with games.
here are the latest:

2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glVertexAttribPointerARB' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glNewObjectBufferATI' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glUpdateObjectBufferATI' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glFreeObjectBufferATI' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glArrayObjectATI' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glVertexAttribArrayObjectATI' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Loaded OpenGL symbol 'glXGetCurrentDisplay'.
2006-02-19T11:05:06Z INFO: Loaded OpenGL symbol 'glXQueryExtensionsString'.
2006-02-19T11:05:06Z INFO: Loaded OpenGL symbol 'glXGetProcAddressARB'.
2006-02-19T11:05:06Z INFO: Couldn't initialize mipmap generation
2006-02-19T11:05:06Z INFO: Couldn't initialize GL_EXT_paletted_texture
2006-02-19T11:05:06Z INFO: Couldn't initialize GL_NV_vertex_array_range
2006-02-19T11:05:06Z INFO: Couldn't initialize GL_NV_fence
2006-02-19T11:05:06Z INFO: Couldn't initialize separate specular color
2006-02-19T11:05:06Z INFO: Couldn't initialize anisotropic filtering
2006-02-19T11:05:06Z WARNING: Invalid control RenderUserFarClip
2006-02-19T11:05:06Z INFO: remove_marker_file()


and a few others
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glEnableVertexAttribArrayARB' in '(default OpenGL library)
2006-02-19T11:05:06Z INFO: Failed to find OpenGL symbol 'glDisableVertexAttribArrayARB' in '(default OpenGL library)

and finally:
andrew@ubuntu:~/SecondLife-linux-02072006$ ./secondlife
LLErrorStream::crashOnError() failed to get mutex for log
LLErrorStream::crashOnError() failed to get mutex for log
LLErrorStream::crashOnError() failed to get mutex for log
2006-02-19T11:05:05Z WARNING: LLDir_Linux not fully implemented!

---

### Post by cronholio on 2006-02-19
Seems like your OpenGL version should be updated in order to play the game.

---

### Post by aljones15 on 2006-02-19
how? does update manager not handle opengl?

-
A

---

