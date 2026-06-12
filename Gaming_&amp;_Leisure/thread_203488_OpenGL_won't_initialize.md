---
title: "OpenGL won't initialize"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by voiceofxile on 2006-06-25
I try to run doom3 and it begins it's loading sequence. It stops with a message that openGL could not initialize. What are some ways/commands I could use to figure out why it cannot initialize openGL?

---

### Post by strattonbrazil on 2006-06-26
I had that problem.  I ran into this thread which kind of explained why.  In my case, I typed glxinfo and in the second column, it has the depth bits displayed.  I had '16'.  The DOOM engine needs 24.  So, I went into /etc/X11/xorg.conf and changed my default depth to 24.  Kind of a vague error though.  

Here is the original thread:

[http://www.ubuntuforums.org/showthread.php?t=203443&highlight=opengl+initialize](http://www.ubuntuforums.org/showthread.php?t=203443&highlight=opengl+initialize)

---

