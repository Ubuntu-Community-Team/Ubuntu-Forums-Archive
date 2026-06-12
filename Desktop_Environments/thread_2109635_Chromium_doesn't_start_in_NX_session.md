---
title: "Chromium doesn't start in NX session"
date: 2013-01-28
forum: Desktop Environments
---

### Post by lz1dsb on 2013-01-28
So here's my setup. Pretty simple, I'm accessing my laptop at home over an SSH session, which is also used by NOMachine's NX server. This works fine and there's no issue there. I just noticed in the last couple of days that while I'm logged in over this NX session, I can't use Chromium. When I click over the icon, it starts the animation like it's loading... and than... nothing. 
Where should I search for logging information to give me a clue what is going on? I checked /var/log/syslog, but I couldn't find anything related to Chromium. Any ideas?

---

### Post by lz1dsb on 2013-01-28
All right... so I did start the Chromium browser from terminal. Here's the error I get:
[15987:15987:0128/115613:ERROR:gl_surface_linux.cc(58)] GLSurfaceGLX::InitializeOneOff failed.

---

### Post by lz1dsb on 2013-02-03
It turned out that this is because I had another X session left open where there was already an instance of Chromium. For both sessions (the NX session and the X session) I was using the same user name. So actually when I was starting Chromium from the NX session, it was opening in the normal X session. Solved.

---

