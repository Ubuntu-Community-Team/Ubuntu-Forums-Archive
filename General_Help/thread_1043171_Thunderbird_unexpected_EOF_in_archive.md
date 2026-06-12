---
title: "Thunderbird unexpected EOF in archive"
date: 2009-01-18
forum: General Help
---

### Post by jonnybbb on 2009-01-18
Hi, I just installed Linux for the first time ever (Ubuntu) and the first thing was to install Thunderbird. Downloaded fresh from the main site, then tried to open the tar.gz file.

Both double-clicking (opens Archive Manager) and typing the command 'tar xvf [filename]', and this one: 'gunzip < [filename] | tar xvf' into the terminal yielded this message:

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I'm a bit discouraged now! Can anyone explain how to open the main thunderbird download file? And is it normal that it won't work by default with the built-in archive manager? Many thanks.

---

### Post by snova on 2009-01-18
For one, Thunderbird is in the repos. Why install from source?

For another, try verifying the integrity of the archive:

```
gzip -t <archive>.tar.gz
```

---

