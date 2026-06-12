---
title: "Evolution: How to clear address book"
date: 2009-11-30
forum: Desktop Environments
---

### Post by mindless1973 on 2009-11-30
Hi,

I imported contacts from another application recently and since then, I have some troubles with the Evolution address book. I have two contacts that I can't delete and which causes Evolution to crash whenever I hit the Birthday&Anniversary calendar entry.

Anyway, as my addressbook seemed to be messed up, I would like to delete the complete Personal Address book and create a new one. However, I don't know how.

I can't delete the whole addressbook from Evolution, the Delete option is grayed out. I can't delete those two contacts, I always get an error message when I try to delete them. When I open them and remove all data, I can delete them, but they show up again when I restart Evolution (with all the deleted data again in them).

So, my aim would rather be to delete the addressbook physically on the disk and create a complete new one!

My System: Ubuntu Hardy LTS
Evolution: 2.22.3.1

Any help appreciated!

bye
Marcus.

---

### Post by Aearenda on 2009-12-01
Here is what I would try (I am here assuming that you have only one address book - if you have more, don't do this, as the folder path I'm giving will be wrong):

1. Close Evolution.
2. Start a terminal (sorry, but it's easy to copy and paste the commands in) do the following commands:
3. ```
evolution --force-shutdown
```This will stop the data server background process, alarm notifier etc.
4. ```
mv ~/.evolution/addressbook/local/system ~.evolution/addressbook/local/system.bak
```This renames the address book so evolution won't find it.
5. ```
evolution
```This will start Evolution and let us see any error messages it spits out. Hopefully it will now create an empty address book for you. 
6. If it's happy, close evolution, close the terminal, and then start evolution from the menu as usual. 

If it doesn't work, here's how to revert what we just did:
1. Repeat steps 1 to 3 above.
2. ```
mv ~/.evolution/addressbook/local/system.bak ~.evolution/addressbook/local/system
```This reverses the rename above.
3. Repeat steps 5 and 6 above.

I should say here that I don't have a Hardy system to test this on properly. Take a backup before you start!

---

### Post by mindless1973 on 2009-12-01
Thanks!

It did exactly what I needed, cleared my address book and now, Evolution is stable again!

Thanks!

bye
me.

---

