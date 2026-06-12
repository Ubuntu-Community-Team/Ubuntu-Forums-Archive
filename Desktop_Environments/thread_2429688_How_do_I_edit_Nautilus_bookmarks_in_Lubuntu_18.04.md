---
title: "How do I edit Nautilus bookmarks in Lubuntu 18.04?"
date: 2019-10-22
forum: Desktop Environments
---

### Post by Paddy Landau on 2019-10-22
I recently upgraded from Lubuntu 16.04 to 18.04. Now, I find that I cannot edit my bookmarks in Nautilus.

I used to press Ctrl+D within Nautilus to get a bookmark editor, but that no longer works, and I cannot find out how to access them to edit bookmarks (add, rename, delete).

How can I edit bookmarks in Lubuntu 18.04? If it helps, Nautilus version is 3.26.4.

---

### Post by PaulW2U on 2019-10-22
To delete or rename a bookmark just right click the bookmark in the sidebar and select 'Delete' or 'Rename'.

Adding a bookmark is not very obvious. Open the folder that you want to bookmark and then click the Menu in the title bar. There's a button labelled 'Bookmark this location'.

Hope that helps.

---

### Post by Paddy Landau on 2019-10-22
Thank you, Paul. It's obvious in hindsight, isn't it? I feel a little silly now :)

Can I edit an existing bookmark to make it point somewhere else (I used to be able to do that)? Or must I to delete it and recreate it?

---

### Post by PaulW2U on 2019-10-22
It's delete and re-create I'm afraid. :(

That was something that I found that I needed to do in order to update a port number in a bookmark that connects my PC to another PC via an SSH connection. 

But....if you like editing config files then you'll find all your bookmarks in ~/.config/gtk-3.0/bookmarks where you can add, delete, rename or edit as much as you like. Usual disclaimer re editing hidden config files applies. :)

---

### Post by Paddy Landau on 2019-10-22
Thank you. I think that I'll stick with delete-and-recreate. It's a pity that they removed the functionality to edit bookmarks, but at least it's a minor inconvenience.

---

