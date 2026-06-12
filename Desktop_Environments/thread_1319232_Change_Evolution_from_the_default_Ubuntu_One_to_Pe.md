---
title: "Change Evolution from the default Ubuntu One to Personal"
date: 2009-11-08
forum: Desktop Environments
---

### Post by leafw on 2009-11-08
I found it very annoying that Evolution defaults to an address book in Ubuntu One (with CouchDB) instead of the local computer.

To make Personal be the default address book instead of Ubuntu One, you have to open the gconf-editor application. Then search for:

apps > evolution > addressbook

and on the top right, where it has two columns "name" and "value",
double click on the value of the "sources" entry.
Then make the "edit key" window that opens larger, and click on the 4th row, which has the "Personal" address book in it. Then push the "Up" button until it's at the top. Then push "OK".

After that, go to the entry at:

apps > evolution > addressbook > display

... and change the "primary addressbook" to the number that your addressbook had in the "sources" key that you just edited above.

---

