---
title: "FTP Scripting without 2nd file"
date: 2009-03-03
forum: General Help
---

### Post by N04h on 2009-03-03
Can anyone provide me a template for an FTP script that doesn't pull from another file.  My current solution looks like this:

```
#!/bin/bash
ftp <<EOD
open ftp.domain.com
user@domain.com

```

I get a username(none): Password prompt in return.

Any ideas of how to do this?

My apologizes in advance if this is the wrong forum.  It didn't quite fit right in programming, nor did it apply to the server in my mind.

---

### Post by dcstar on 2009-03-03
> **N04h said:**
> Can anyone provide me a template for an FTP script that doesn't pull from another file.  My current solution looks like this:

```
#!/bin/bash
ftp <<EOD
open ftp.domain.com
user@domain.com

```

I get a username(none): Password prompt in return.

Any ideas of how to do this?

My apologizes in advance if this is the wrong forum.  It didn't quite fit right in programming, nor did it apply to the server in my mind.

```
man ftp
``` will show you all the command line options, including server and login credentials.

---

### Post by N04h on 2009-03-03
That isn't the issue. The issue is with the scripting part.  It won't run the lines that follow the ftp line in a shell script.


Thanks for trying to help though.

---

### Post by dcstar on 2009-03-03
> **N04h said:**
> That isn't the issue. The issue is with the scripting part.  It won't run the lines that follow the ftp line in a shell script.


Thanks for trying to help though.

Of course not, all ftp commands have to be in the file you are piping into ftp or as command line options. As I said, read the man page.

---

### Post by N04h on 2009-03-04
> **dcstar said:**
> Of course not, all ftp commands have to be in the file you are piping into ftp or as command line options. As I said, read the man page.

So I can't do it any other way?  I have to pipe those in?  I can't keep it in only in one file.  Can I create the file on the fly?

---

