---
title: "Need some fairly simple scp help"
date: 2009-05-28
forum: General Help
---

### Post by The Switch Blade on 2009-05-28
Hi,

One of my professors is asking me to retrieve a file on a remote machine.

The problem is that I cannot access the machine without first accessing the school server. So I ssh into [EMAIL="username@school.addres"]username@school.addres[/EMAIL]s, and then ssh into [EMAIL="username2@that.machin"]username2@that.machin[/EMAIL]e. So I can't just ```
scp username2@that.machine:/file/here .
```and I can't transfer the file to a directory on the school address (file is too big for alloted space). I don't believe I can do something like ```
scp username@school.address:username2@that.machine:/file/here .
``` How can I get around this? Thanks.

---

### Post by The Switch Blade on 2009-05-28
bump

---

### Post by unutbu on 2009-05-28
If you can run "nc" (netcat) on the university server, perhaps you could use it to create a netcat connection between your university and local machine:

See

[http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/](http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/)
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

This is a little beyond my range of experience however, so please forgive if this turns out to be nonsense :)

---

