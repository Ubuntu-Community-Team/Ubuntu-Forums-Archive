---
title: "downloaded file"
date: 2008-02-05
forum: Desktop Environments
---

### Post by junaid.kollam on 2008-02-05
where does the downloaded file stored?suppose i install mplayer through synaptic.Where does mplayer file store?is it possible to editing this file?

---

### Post by PeterJS on 2008-02-05
Mplayer it self goes in to the standard file heirarchy, since it's a non-essential prgram it will end up in /usr/bin. The deb package itself is stored in /var/cache/apt/archives/ if you want to re-install it. See the link in my sig for more information on the FHS and where things go. It's not possible to change the location that apt installs to, but you really don't want to anyway you'd break stuff.

---

