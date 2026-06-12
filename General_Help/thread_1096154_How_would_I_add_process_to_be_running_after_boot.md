---
title: "How would I add process to be running after boot"
date: 2009-03-14
forum: General Help
---

### Post by NuNn DaDdY on 2009-03-14
I have a server which I would like to be running after the system boots.  What do I need to do in order to do this [the name of my process is 'server'].  Thanks!

---

### Post by RD1 on 2009-03-14
Add an entry to "Startup Programs" in System > Preferences > Sessions

---

### Post by NuNn DaDdY on 2009-03-14
I tried what you recommended but it doesn't appear to work correctly.  The server which I am trying to run is a simple executable which I created.

---

### Post by sgosnell on 2009-03-14
You need to give the session manager the full path to your executable.  I'm not sure how things work in Dapper, so I can't give you detailed instructions, but it shouldn't be that hard.  You might also consider renaming the executable to something other than 'server', but that should work anyway.

---

### Post by NuNn DaDdY on 2009-03-14
Oh I'm sorry I haven't updated my details in some time.  I am running the newest distribution of Ubuntu so I'm open for suggestions on how to do it :)

---

### Post by RD1 on 2009-03-14
Can you launch the executable from the terminal? What is the exact command line used?

---

### Post by NuNn DaDdY on 2009-03-14
the file itself is in  ~/Desktop/Operating_Systems/Assignments/three/p3/

to run the file I use '/server  5'

---

### Post by quonsar on 2009-03-14
> **RD1 said:**
> Add an entry to "Startup Programs" in System > Preferences > Sessions

This will only run the program at login. He wants it running after bootup, whether anyone is logged in or not, I would assume. It's some kind of server.

---

### Post by RD1 on 2009-03-14
> This will only run the program at login. He wants it running after bootup, whether anyone is logged in or not, I would assume. It's some kind of server.

My mistake. :confused:

Try adding script to /etc/rc.local

---

