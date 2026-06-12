---
title: "Ryujinx permanent memory mappings"
date: 2023-08-14
forum: Gaming &amp; Leisure
---

### Post by morcar1975 on 2023-08-14
When I use Ryujinx I get the error "Max amount of memory mappings is lower then the recommended" this is solved by going into the terminal and typing

```
[COLOR=#000000][FONT=ui-monospace]sudo sysctl -w vm.max_map_count=524288[/FONT][/COLOR]
```

Sadly, if I have rebooted the system I need to type this in again and wanted to know is there a permanent fix.

Thanks in advance.

---

### Post by #&amp;thj^% on 2023-08-14
> **morcar1975 said:**
> and wanted to know is there a permanent fix.

Thanks in advance.
To make it persistent, you can add this line:
```

vm.max_map_count=524288
```

in your /etc/sysctl.conf and run

```
sudo sysctl -p
```

to reload configuration with the new value.

---

### Post by morcar1975 on 2023-08-14
Thank you

---

### Post by #&amp;thj^% on 2023-08-14
Enjoy

---

