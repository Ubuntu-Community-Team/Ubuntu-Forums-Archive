---
title: "OpenOffice.org writer crashes right after startup"
date: 2006-11-16
forum: Desktop Environments
---

### Post by vmalloc on 2006-11-16
Hi all,

I'm new to Ubuntu, and recently installed a fresh system on my computer (6.10 Edgy)

Without any prior configuration or attempts to run oo.o, I fired up the Writer application. First of all, the font used in the dialog boxes is not antialiased, and is rendered poorly. 

Second, when I typed into the application, the backspace, arrow and delete keys had no effect whatsoever. I encountered this only in the oo.o applications, and not in any other application.

Third, when I try closing Writer, any response to the save/discard/cancel dialog causes the app to freeze up completely.

Has anyone encountered this behavior? This sounds like extremely poor quality on Ubuntu's behalf.

Any help will be appreciated very much.

Thanks,

Rotem

---

### Post by vmalloc on 2006-11-20
Ok - I found the problem.

Turns out nfs wasn't properly configured, and for some reason that's the set of symptoms it triggers ](*,)

---

### Post by Muppy on 2007-03-20
Hi vmalloc,

I have the exact same symptoms as you have described in your first post, I also have the user directories mounted from a server through NFS, but I cannot find where I have misconfigured the NFS server or client... Can you help me and tell me what was wrong in your case?

Thanks a lot in advance!

Manfred

---

### Post by ilmw on 2007-03-22
OpenOffice worked great for me several days ago, but now the application crashes my system (Ubuntu Dapper). Once I start up OpenOffice Writer, the system will logout and re-login. Did anybody else have the same problem or just me? Anybody knows how to fix it? Thanks!

---

