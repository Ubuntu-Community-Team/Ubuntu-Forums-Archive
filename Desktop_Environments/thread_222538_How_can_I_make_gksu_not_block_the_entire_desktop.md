---
title: "How can I make gksu not block the entire desktop?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by t0maz on 2006-07-25
Dear fellow Ubuntu users,

When I open an Administration item, gksu is started and blocks the whole screen asking for a password. In the previous Ubuntu version it was just a little box. I find this new approach pretty annoying but haven't found a way yet to revert it back to the old situation.

Does anyone know I could change this?

---

### Post by ardchoille on 2006-07-25
I don't think you can block it from doing that.. it looks like gksu is system modal now.

---

### Post by LORD_PoLvO on 2006-07-25
na u cantchange it dude soz its part of the new gnome for dapper drake yeah its a bit anoying but youll learn to live with it aye ??? its for security reasons i guess :) i mean u cant use gksu that much that its that anoying aye??

---

### Post by t0maz on 2006-07-25
Thanks for the replies. I had hoped it was configurable via a config file or gconf or something like that. You think it would be possible (well, at least not too hard) to install the gksu from the previous Ubuntu?

---

### Post by Rmantingh on 2008-02-22
Apparently you can use gksu with --disable-grab or -g option (see man gksu).
This prevents the screen being locked.

---

