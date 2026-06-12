---
title: "Command to &quot;Allow executing file as program&quot;"
date: 2009-12-20
forum: Development CD/DVD Image Testing
---

### Post by lexen on 2009-12-20
Hello, I was wondering if there was a command to change the permissions of a file to "Allow executing file as program."  I understand that you can do this with the gui, the reason I want to do it through a command is so I can incorporate it into a .sh file.


Thanks,
Lexen

---

### Post by lloyd_b on 2009-12-20
> **lexen said:**
> Hello, I was wondering if there was a command to change the permissions of a file to "Allow executing file as program."  I understand that you can do this with the gui, the reason I want to do it through a command is so I can incorporate it into a .sh file.


Thanks,
Lexen

Use the "chmod" command - "man chmod" in a terminal window for the full syntax, but "chmod +x {file}" will give you execute permission.

Lloyd B.

---

