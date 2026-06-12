---
title: "[SOLVED] How do I purge tasks/files out of gpilot-install-file queue?"
date: 2007-09-30
forum: Desktop Environments
---

### Post by perryrt on 2007-09-30
Folks - 

For various reasons that kinda involve the todo bug already documented, I'm having trouble with moving data to my Treo 700p.

The key question for the moment is that I've got a file (ToDoDB.pdb) that causes a sync to crash. However, I stupidly tried to manually install the same file using gpilot-file-install.....and of course it didn't work. My problem is that I used the --later switch on the gpilot-file-install routine and now the offending file keeps trying to install every time I sync (and crashes every time).

How do I clear this entry out of the gpilot-file-install queue? Where can I find this queue? The only thing I've tried so far is restarting and running a systemwide search for the term...but restarting didn't seem to help, and the search is ongoing about three hours now with no luck.

Any help would be appreciated.

---

### Post by perryrt on 2007-10-01
Bump - any body have any ideas? Or a suggestion where I should better put this inquiry?

---

### Post by perryrt on 2007-10-04
Bump - any suggestions would be appreciated.

---

### Post by perryrt on 2007-10-09
Still stuck on this one, folks. Any ideas?

The summary of the problem is that there is a file (ToDoDB.prc) that won't sync, and as a result, is "stuck in the queue" of gpilot-install-file....hangs every time I try to sync with "file" conduit enabled.

Any idea of how to fix this would be appreciated.

---

### Post by Adresomoradu on 2007-10-13
I have the same problem, please send me a message if you solve that

---

### Post by Adresomoradu on 2007-10-14
I got the answer...!!!:)

Just erase all the files into home/user/.gpilotd

Where user is the current user... or just search .gpilotd and there erase all the files...Sorry for my bad english... i is not my language

---

### Post by perryrt on 2007-10-14
Worked like a charm! I should have thought of that, actually. I was looking in other places, but I forgot to look in my home directory - plus, the system renamed the file prepping it for install, so a search didn't turn it up.

Thanks very much - and your English is just fine!

---

