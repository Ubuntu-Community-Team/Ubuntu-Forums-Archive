---
title: "Security language updates"
date: 2014-07-28
forum: Desktop Environments
---

### Post by Pengwyn44 on 2014-07-28
Ubuntu 14.04 on a desktop computer. The update icon tells me that an update 
is available in the normal way. The problem is that security language updates
are offered every day for a list of unwanted languages. I only have English (GB)
on the computer. I have tried "localepurge", but to no avail.
How can I stop this update being offered?

Pengwyn44

---

### Post by Frogs Hair on 2014-07-28
I see an update for language selector common from July 18 and this includes no language packs. Are you using a program that requires or includes different languages ?

---

### Post by Pengwyn44 on 2014-07-29
The only word processing programs that I use are LibreOffice Writer, Lyx and Scribus. I don't think that they automatically
include languages. When installing Ubuntu language packs seem to be installed by default.
I certainly do not use any language other than English (GB).

---

### Post by Frogs Hair on 2014-07-29
I wouldn't know about Srcibus and when I check synaptic I see numerous language packs, but only US English and related packages installed. Synaptic will display whether packages are simply new in the repository or actual updates.

---

### Post by Pengwyn44 on 2014-08-01
I have found the language packs, they are in Firefox Extensions. I deleted them with "root@PCS:/usr/lib/firefox-addons/extensions# rm *.xpi".

---

