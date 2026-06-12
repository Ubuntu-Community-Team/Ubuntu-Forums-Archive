---
title: "fonts help"
date: 2005-06-18
forum: Desktop Environments
---

### Post by vaskark on 2005-06-18
I have Hoary and Windows on the same drive. I want my fonts from my Windows partition available to Hoary. How can I do that? I know I could make ~/.fonts a symlink to my windows font folder, but I'd rather just leave that for local fonts for now. I imagine I'd have to add the path to some system fonts file. Can anyone advise? This would be easy if NTFS drives were writable from linux!

---

### Post by desdinova on 2005-06-18
The problem with NTFS is not Linux's fault - MS have not released the specs. Why not simply just copy over the fonts to /.fonts?

---

### Post by vaskark on 2005-06-18
[QUOTE=desdinova]The problem with NTFS is not Linux's fault - MS have not released the specs. Why not simply just copy over the fonts to /.fonts?[/QUOTE]

Well, that was my first plan. But I figured there's probably a more elegant solution :)

---

### Post by Alexander Kirillov on 2005-06-18
[QUOTE=vaskark]Well, that was my first plan. But I figured there's probably a more elegant solution :)[/QUOTE]
 If you find one, let us know - I also just copied the fonts from WIndows. The only difference is, I copied them to a subdirectory under /usr/share/fonts (to make them available to all users,. not just me)

---

