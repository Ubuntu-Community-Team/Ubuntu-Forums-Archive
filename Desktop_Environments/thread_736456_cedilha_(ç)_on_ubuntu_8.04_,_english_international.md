---
title: "cedilha (ç) on ubuntu 8.04 , english international (en) keyboard"
date: 2008-03-26
forum: Desktop Environments
---

### Post by gdjaime on 2008-03-26
"sudo vi /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules"

change from

"/usr/lib/gtk-2.0/2.10.0/immodules/im-cedilla.so"
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa"

to

"/usr/lib/gtk-2.0/2.10.0/immodules/im-cedilla.so"
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en"

restart X

---

