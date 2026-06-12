---
title: "Trash bin"
date: 2009-06-02
forum: General Help
---

### Post by Maysun on 2009-06-02
I have noticed I can move files from the Desktop to a trash bin.
But where is this trash bin located? Does it mean whatever I put there is eternally lost or can I retrieve it somehow?

---

### Post by talava on 2009-06-02
The trash icon is in the left sidebar of the Computer-view in file browser (places->Computer in top menu by default).

Also, you can put the trash icon on your desktop by typing 'gconf-editor' in terminal.
Go to: apps -> nautilus -> desktop and tick trash_icon_visible.
Notice also the other options there. You can put the Home folder and Computer-icons to your desktop too. This should make your desktop more windows-like.

And just as a sidenote:
The trash bin is located at /home/your_user_name/.local/share/Trash
The .local-folder is hidden, and can be accessed by ticking 'Show hidden files' in the view-tab or by pressing ctrl+H. But you don't really need to know the exact location to access your trash...

---

### Post by Legace on 2009-06-02
> **Maysun said:**
> I have noticed I can move files from the Desktop to a trash bin.
But where is this trash bin located? Does it mean whatever I put there is eternally lost or can I retrieve it somehow?

When you delete something, or when you drag and drop something into the Trash bin, it is stored there until a specific amount (of gigabytes, usually).

If you want to restore a file, double-click on the Trash icon, and find the file(s) you like. Once you've found it, right-click on the file(s) and select "Restore" :)

---

### Post by Maysun on 2009-06-03
Thank you!

---

### Post by Shazaam on 2009-06-03
AND, there is a /root/local/share/Trash too.:)

---

