---
title: "Permissions issue: 'X' not working"
date: 2009-03-28
forum: General Help
---

### Post by shaggy999 on 2009-03-28
So I am running into a strange issue. I have a hierarchical set of directories and folders that I want to set permissions on. For all the files permissions should be set to 644 (read-write for root, read-only for everyone else) and for directories it should be 755 because I need the execute bit set in order to browse the directories. I thought my solution was this:

chmod -R u=rwX,g=rX,o=rX *

But it didn't work. Permissions on files were set to 755. Note the capital X. In the man page for chmod it says about X: "execute/search only if the file is a directory or already has execute permission for some user"

So I figured maybe the files already had the execute bit so it just left it on there. So I tried:

chmod -R 000 * && chmod -R u=rwX,g=rX,o=rX *

This came with the same result. Ultimately what did work was this:

find . -type d -exec chmod 755 {} \;
find . -type f -exec chmod 644 {} \;

The problem with this solution is that (1) it's two seperate commands and (2) it's SLOOOOOW (there's ~ 100,000 files and 20,000 folders, so this takes on the order of minutes instead of chmod's seconds). Does anybody know what I'm doing wrong with the chmod command? Or is the two find commands my only option?

---

