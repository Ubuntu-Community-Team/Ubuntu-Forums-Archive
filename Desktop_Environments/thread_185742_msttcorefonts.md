---
title: "msttcorefonts"
date: 2006-06-01
forum: Desktop Environments
---

### Post by johnwards on 2006-06-01
Morning,

I have enabled all the available sources in Synaptic and searching for msttcorefonts only returns the OpenOffice package which says it comes with msttcorefonts but it doesn't.

I searched the old archives and I read about enabling multiverse but how do I do that ? I have enabled all the possible options within syamptic and I'm not sure where multiverse is for dapper.

Cheers
John

---

### Post by Rackerz on 2006-06-01
Do you have Automatix? That will install msttcorefonts for you.

---

### Post by bjc on 2006-06-02
[QUOTE=johnwards]Morning,

I have enabled all the available sources in Synaptic and searching for msttcorefonts only returns the OpenOffice package which says it comes with msttcorefonts but it doesn't.

I searched the old archives and I read about enabling multiverse but how do I do that ? I have enabled all the possible options within syamptic and I'm not sure where multiverse is for dapper.

Cheers
John[/QUOTE]

Yep, multiverse is what you want. If you chose Edit Channel on the binary channels there should be a Multiverse checkbox. Is this checked? If it's still not working, could you show me the output of the following:
```

cat /etc/apt/sources.list

```

---

