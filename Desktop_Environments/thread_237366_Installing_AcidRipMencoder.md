---
title: "Installing AcidRip/Mencoder"
date: 2006-08-16
forum: Desktop Environments
---

### Post by HelloImHowie on 2006-08-16
I'm trying to get AcidRip working, and I cant install AcidRip through the Add/Remove Programs panel so I'm trying it manually. I've gotten it running, but it won't do anything without mencoder. Where did MEncoder go? According to the forums, I can just install it with "sudo apt-get install mencoder" but it keeps telling me the package does not exist. I've tried going with Vive, but that brought up a whole mess of things that wouldn't work. Help would be awesome.

---

### Post by ardchoille on 2006-08-16
> **HelloImHowie said:**
> I'm trying to get AcidRip working, and I cant install AcidRip through the Add/Remove Programs panel so I'm trying it manually. I've gotten it running, but it won't do anything without mencoder. Where did MEncoder go? According to the forums, I can just install it with "sudo apt-get install mencoder" but it keeps telling me the package does not exist. I've tried going with Vive, but that brought up a whole mess of things that wouldn't work. Help would be awesome.

Acidrip is in the multiverse repo. Enable the multiverse repo, do sudo apt-get update and then:

```

sudo apt-get install acidrip

```

If you need help enabling the multiverse repo:

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

It is much better to install from the repos than to compile and install manually.

---

### Post by HelloImHowie on 2006-08-17
Wow. I've done that on my other computers, but apparently I forgot to do it on this one.

Thanks :D

---

