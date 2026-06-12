---
title: "BOM in BE/LE files created in gEdit"
date: 2009-08-13
forum: Desktop Environments
---

### Post by ProgramErgoSum on 2009-08-13
Is it true that, BOM will not be placed when using gEdit ? If yes, what would you suggest ?

For some testing, I required files to be created in UTF-16BE and UTF-16LE. When created in Windows and viewed in a hex editor, I could see the [BOM]("http://en.wikipedia.org/wiki/Byte-order_mark") (x'FEFF' or X'FFFE') correctly placed. But, with gEdit, while two bytes are indeed being used for UTF-16, I could not locate the BOM.

---

### Post by ronaldprettyman on 2009-08-13
> **ProgramErgoSum said:**
> Is it true that, BOM will not be placed when using gEdit ? If yes, what would you suggest ?

For some testing, I required files to be created in UTF-16BE and UTF-16LE. When created in Windows and viewed in a hex editor, I could see the [BOM]("http://en.wikipedia.org/wiki/Byte-order_mark") (x'FEFF' or X'FFFE') correctly placed. But, with gEdit, while two bytes are indeed being used for UTF-16, I could not locate the BOM.

vim

---

### Post by ProgramErgoSum on 2009-08-19
Thanks ! I will check it out.

---

