---
title: "CDROM Backup Software"
date: 2006-09-26
forum: Desktop Environments
---

### Post by SonWon on 2006-09-26
I am looking for a backup program that will compress and write my data to a cdrom in one operation?

I could use archive manager and K3B but that is two steps.

Thank you for your suggestions.

---

### Post by Mr Frosti on 2006-09-26
I am not aware of any programs, Windows or Linux that has this capability. This is not to say that one does not exist out there. 

The mentality of programs in Linux seem to focus on doing on specific task and doing it well. I would think it is fairly to use an archiving program, and a CD burning program.

Of course you could always write a shell script to do this. It is probably as simple as something like the following bit of code:

```

#!/bin/bash

//Backup your home folder using tar
tar -cvf ~/* archive.tar

//Pass this file to K3b to queue it up
k3b archive.tar

exit 0

```

Of course you can change the "~/*" directory (which is your home folder) to any directory you wish.

---

