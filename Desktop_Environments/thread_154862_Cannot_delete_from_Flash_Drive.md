---
title: "Cannot delete from Flash Drive"
date: 2006-04-04
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-04-04
I was a gnome user but now a kde user now.

I have this wierd problem. I have 512MB flash drive. If I try to delete something it wont let me delete. I get an error saying "Creating folders is not supported with protocol trash".

I goto console to delete the folder from /media/FLASDRIVE/folder_name and I can do that. I never had this problem in gnome. I also tested this with SuSe box.

Could you please point out the problem with this thing.

Every help is appreciated.

---

### Post by frodon on 2006-04-04
When you use a file browser to delete a flash drive it often create a .trash directory (which is hidden) therefore you can see you flash drive empty in the file browser whereas your .trash on your flash drive is full.
You don't have this problem in terminal because when you erase something in terminal it don't use a trash it just delete it.

---

### Post by krypto_wizard on 2006-04-04
What should i do to fix this ??? Because Gnome and Suse KDE is not giving me this problem.




[QUOTE=frodon]When you use a file browser to delete a flash drive it often create a .trash directory (which is hidden) therefore you can see you flash drive empty in the file browser whereas your .trash on your flash drive is full.
You don't have this problem in terminal because when you erase something in terminal it don't use a trash it just delete it.[/QUOTE]

---

### Post by frodon on 2006-04-05
Ho i'm not sure it's the problem here, it could be but it's not sure. To solve that just delete the .trash folder generally we don't do it because it's an hidden directory and therefore we often forget to delete it.

---

