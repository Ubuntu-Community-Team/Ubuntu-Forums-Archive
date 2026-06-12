---
title: "Coldwar demo crashing after starting a new game."
date: 2005-11-15
forum: Gaming &amp; Leisure
---

### Post by fragmental on 2005-11-15
When I get to the screen where the game is loaded and it tells me to press enter to play I get this message:
```
check: OpenGL error 1285 detected: out of memory (GLuint meng::renderer::Stream::create_vbo_memory_block(const meng::renderer::stream_meta_data::StreamMetaData&, const meng::byte*)) (stream_memory_opengl.cpp:70)
```

Same thing happens if I run as root, so it's probably not a privilege issue.

I'm kind of wondering if it's because I'm running an ATI Radeon.  I have a 9600xt and I'm running the breezy driver from the repositories.  Every other 3d game seems to run fine. I play ut2004 often.

---

### Post by fragmental on 2005-11-15
apparently I wear the Fool's Cap that proclaims "RTFM!" today.  I forgot to read the README.

It wasn't helpful but it did have a link to the proper forums(not Dreamcatcher's the publisher, mindware's, the developer).  In that forum they had a post stickied.  [http://coldwar.mysteria.cz/viewtopic.php?t=65](http://coldwar.mysteria.cz/viewtopic.php?t=65)

Directly from the horses mouth:
[quote="Patrik Rak"]Several people have already reported this one and it has been responded to before, but I'll do that once again and make this thread sticky.

This seems to be a problem with ATI drivers in general. For some reason they fail to allocate the VBO memory. We have seen this happen on Windows with some older ATI drivers in the past as well. Until ATI drivers support VBO correctly, adding this line to your config.txt will fix it:
```

compatibility_fix_disable_vertex_buffer_objects true

```[/quote]

Now to decide whether to simply add that line to config.txt or update to the latest drivers in hope that it has been fixed.  I probably would have seen it in the release notes but I can't seem to find the release notes for the 18 release.  I probably would not have noticed something like that though.  Easier to just copy the fix into config.txt probably.

Stupid ATI.

---

### Post by JurB on 2005-11-15
It works for me ... tnx!

---

