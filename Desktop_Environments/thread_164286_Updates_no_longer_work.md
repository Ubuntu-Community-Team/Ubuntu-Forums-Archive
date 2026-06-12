---
title: "Updates no longer work"
date: 2006-04-22
forum: Desktop Environments
---

### Post by MacSpoofing on 2006-04-22
I'm using Ubunut 5.10, as of late I noticed the updates-functionality no longer works.

I do get a notification that updates to various packages are available but when I press the install button they are neither downloaded (the download popup briefly  becomes visible but then goes away) nor they are installed.

What could be the problem?

---

### Post by Ramses de Norre on 2006-04-22
You can try sudo apt-get update && sudo apt-get upgrade and check for any error output.

---

### Post by MacSpoofing on 2006-04-25
[QUOTE=Ramses de Norre]You can try sudo apt-get update && sudo apt-get upgrade and check for any error output.[/QUOTE]


I tried "sudo apt-get upgrade" and it worked perfectly. I got all my packages. Is there any reason why the GUI client would act up?

---

