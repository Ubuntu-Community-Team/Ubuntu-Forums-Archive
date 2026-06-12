---
title: "Trash can promblem"
date: 2005-06-05
forum: Desktop Environments
---

### Post by redclawz on 2005-06-05
I had a folder in my trash can that i wanted to delete it. When i tried i got a permission error. I asked one of my good friends how do i delelte it and he gave me this line.

sudo rm -rf ~/.Trash/*

IT worked, but now when i put something new in the trash can it does not show up at all. How can i see the files/folders that are int eh trash can again?

---

### Post by flanker on 2005-06-05
Strange, that should work.

Try deleting the actual Trash directory (along with its contents)

sudo rm -rf ~/.Trash

logout and back in again and create / delete a file in your home directory.

---

