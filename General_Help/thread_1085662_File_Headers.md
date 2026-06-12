---
title: "File Headers"
date: 2009-03-03
forum: General Help
---

### Post by ult_avatar on 2009-03-03
Hi,

I was wondering if there is some (command line)tool that can read out file headers ?

I would need it for the tool "foremost", which is a tool that can extract files from corrupted volumes based on their headers. Luckily almost all the common file types are already standard or in the .conf file. But I would like to add some more.

foremost wants the header in the following fashion:
```

              case    size    header                  footer
extension   sensitive
```

that means for Outlook for example:

```
Outlook files
        pst     y       400000000 \x21\x42\x4e\xa5\x6f\xb5\xa6
        ost     y       400000000 \x21\x42\x44\x4e
```

Any help would be appreciated !

---

