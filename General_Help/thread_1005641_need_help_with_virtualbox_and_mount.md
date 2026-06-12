---
title: "need help with virtualbox and mount"
date: 2008-12-08
forum: General Help
---

### Post by 1nfern0 on 2008-12-08
hi there.
I'm new to the world of Linux.

Just installed Ubuntu to my Virtualbox. I want to use it for developing C applications using Eclipse. but I want the workspace to remain on Windows. I want the compiled files to be at once executable. Ok this is linux, you have to do this manually. I have mounted the folder using this command:
(workspacec is the folder that is mapped to my workspace on Windows)
```
sudo mount.vboxsf workspacec /home/vladimir/workspace/ -o remount,uid=1000,gid=100,fmode=755,exec

```
But still no luck. am I missing something ? Ive wasted a couple of days figuring this out and i'm stuck currently ...

Thanks in advance,
1nfern0

---

