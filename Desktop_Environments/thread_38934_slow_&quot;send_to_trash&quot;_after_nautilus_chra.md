---
title: "slow &quot;send to trash&quot; after nautilus chrash"
date: 2005-06-02
forum: Desktop Environments
---

### Post by tulinius on 2005-06-02
Hi,

i got this problem (subject).

This happends everytime nautilus needs to restart because of a crash of some art, fx if the program to create tar-archives direktly from nautilus crashes. nautilus restart fine and so on, but if i try to send a file to the trashbin nautilus freezes for some seconds. if i choose to delete the file directly this doesn't happend.

i'm using hoary :)

---

### Post by Joeb on 2005-06-03
Not sure of the cause, but chances are that nautilus hasn't fully unloaded after the crash.  If it crashes again, try doing a killall nautilus from the command line and then restarting it and see if it works like you expect it should.

---

