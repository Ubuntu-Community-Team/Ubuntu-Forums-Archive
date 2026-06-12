---
title: "Cant copy files to remote mahcine"
date: 2009-04-18
forum: General Help
---

### Post by lightnb on 2009-04-18
I have a remote computer mounted to my local filesystem via sshfs.

When trying to drag a file from my local desktop to the remote computer I get the error:

```
There is not enough space on the destination. Try to remove files to make space.
```

There is more than enough space on the destination. The error message is wrong. How do I fix this.

I tried chmoding the destination folder to 777, and mounting the remote computer as root (root on the remote machine). I can delete files, create new files, and rename files, But I can't COPY files from my local computer to the remote one.

---

### Post by aaronp on 2009-04-18
Can you copy via a terminal command instead of drag-and-drop?

---

### Post by lightnb on 2009-04-19
Yeah, CP via the terminal works fine (that's what I ended up doing in the meantime...)

Is this a known bug with the file browser? I'm not afraid of the CLI, it just takes longer and tends to be more error-prone....

---

### Post by aaronp on 2009-04-19
> **lightnb said:**
> Yeah, CP via the terminal works fine (that's what I ended up doing in the meantime...)

Is this a known bug with the file browser? I'm not afraid of the CLI, it just takes longer and tends to be more error-prone....

Not sure about any bug, just checking if there was some hidden permissions or ownership issue to narrow it down. Obviously there is not so it is something to do with the app you are using to drag and drop.

Do you need to use sudo in the CLI to copy the files? If so, maybe because the file browser (I assume we are talking about Nautilus?) is started as a non-root user?

---

