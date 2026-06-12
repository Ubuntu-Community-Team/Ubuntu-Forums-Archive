---
title: "Dash search gives no result for files (the rest is OK)"
date: 2012-09-01
forum: Desktop Environments
---

### Post by Iceberg76 on 2012-09-01
So far I tried:

-rm -rf ~/.local/share/zeitgeist

-installing  unity-place-applications, unity-place-files 

-logout/login

There is no privacy setting blocking zeitgeist recording any file.

In .xsession-errors:

** (zeitgeist-datahub:13996): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

---

### Post by Iceberg76 on 2012-09-04
Got the answer from another forum, and I'm posting it here for the record.

Ubuntu 12.04 uses unity-lens-*, instead of unity-place-*, where * can be music, applications, files, or video. Just substitute it for whatever is not working.

Run:

sudo apt-get purge unity-lens-files && sudo apt-get install unity-lens-files

(subtitute files for music, applciations, or video, if that's the case)

---

