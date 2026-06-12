---
title: "extracting file error"
date: 2009-01-11
forum: General Help
---

### Post by newbux on 2009-01-11
im extracting a file in the terminal and i keep getting this error do you know what i should do.

command:

tar zxvf ../snortrules-snapshot-CURRENT.tar.gz


error:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

thanks

---

### Post by logos34 on 2009-01-11
what does

**file** ../snortrules-snapshot-CURRENT.tar.gz

show?

---

### Post by newbux on 2009-01-11
it's like virus definitions (or rules) and stuff like that for snort the intrusion prevention and detection system

---

### Post by logos34 on 2009-01-12
what I meant was to run this command:
> 
file ../snortrules-snapshot-CURRENT.tar.gz

the error message says its not a gzip archive despite suffix, so check it with the file command (maybe its just an uncompressed tar)

---

