---
title: "No support for swedish characters via SCP?"
date: 2009-05-20
forum: General Help
---

### Post by .gurkburk on 2009-05-20
Before I even start I would just like to point out that this is not a _pure_ ubuntu installation, its ebox-platform which is basically an ubuntu-installation, with ebox installing alot of programs on it pre-configured with a web-interface.

Now, onwards to the problem at hand:
I dont have support for swedish special characters, I think what I need is UTF-8?

I discovered it after copying over a large (8.5GB) folder with documents via scp from another linux-server, and pretty much everything went fubar (letters renamed with _ and such).

If I manually try to create folder/files with åäö in them, this works perfectly (on both servers).
For example:
mkdir /åäö
and then
vim åäö.ööääåå
This works perfectly.

Command I run with SCP is: 
scp -r user@myotherserver:/the/directory /dir/on/new/server
Nothing fancy, but it does fail misserably.

If it makes any difference, I run the command via putty, but that shouldnt affect it afaik?

Edit/update:
Even if I try to copy between 2 explorers on a windows XP machine, I get the same result. åäö-letters are replaced with _
This is what, the samba-engine doing the copying or?

I wonder what's causing this?

---

