---
title: "Trouble with ssh known_hosts"
date: 2006-05-29
forum: Desktop Environments
---

### Post by mbailey on 2006-05-29
I recently re-installed ssh on one of my ubunbtu boxes & found that I could not ssh to it any more from the other and got a long error regarding RSA keys changing an possible man in the middle attacks which ended with this:

Add correct host key in /root/.ssh/known_hosts to get rid of this message.

I searched for the message on-line and found suggestions regarding removing the offending line so that ssh would accept the new host key. Trouble is, the known_hosts file has several entries (I think) none of which are human readable, so deciding which to delete is rather tricky. I solved it by deleting known_hosts and a subsequent use of ssh recreated it after I accepted the new key.

Question is - how should I really have solved this & where could I have found the appropriate entry on the remote server to copy into known_hosts?

Thanks,
Martin

---

### Post by art on 2006-05-29
The file does contain human-readable line, which are at the end of the file. You should have done a simple find on the file. I encounter the same problem some times, and what I do is I search for the server name which has been reconfigured, and remove that line...

---

### Post by mbailey on 2006-09-04
I got the answer from ArsTechnica & forgot to post it here. It turns out that the file is now encrypted by default, though old entries will still appear in plain text. However, you can remove an entry for a single host using:

ssh-keygen -R hostname

---

### Post by Xitron on 2008-03-06
The way I handle these is with 'vi'.  When you see the error, it tells you what line in known_hosts is causing the problem.

vi .ssh/known_hosts
## - Shift-G
dd
:wq

...where...
vi .ssh/known_hosts opens the file for editing
## is typing in the line number you saw in the error message
Shift-G will take you to the line number you just typed in
dd will delete the offending line
:wq will write the file out and quit

Hope this helps,

Unca Xitron

---

