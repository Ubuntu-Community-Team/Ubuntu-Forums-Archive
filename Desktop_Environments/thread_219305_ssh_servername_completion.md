---
title: "ssh servername completion"
date: 2006-07-19
forum: Desktop Environments
---

### Post by mrf on 2006-07-19
In breezy I could type : ssh <username>@<half of servername> hit tab and have it attempt to lookup the servername from either my hosts file or somewhere else automagical. In dapper this doesn't work anymore. Is it possible to renable this?

tia

---

### Post by fabiand on 2006-07-20
Hey,

did you try to add the host to the ~/.ssh/known_hosts?

---

### Post by oldmanuk on 2006-11-21
seems like known_hosts is now hashed (using edgy) and so bash_completion cannot do the ssh completion properly, you can turn this off though see here

[https://launchpad.net/distros/ubuntu/+source/bash/+bug/42382](https://launchpad.net/distros/ubuntu/+source/bash/+bug/42382)

---

