---
title: "Cannot Empty my Trash?"
date: 2009-03-09
forum: General Help
---

### Post by sports fan Matt on 2009-03-09
I have an interesting problem, I cannot seem to empty my trash bin in Ubuntu.  This problem has started recently, and im curious as to why?  All ive done was install a few updates..Anyone have any ideas?

---

### Post by woodenbrick on 2009-03-09
I occasionally have the same problem do you get a popup dialog named file operations that never closes? 
When this happens I run: 
sudo rm -rf ~/.local/share/Trash/* 
but it would be nice to have it fixed.

---

### Post by sports fan Matt on 2009-03-09
No error message, no, and funny thing is i ran that command and it didnt empty my trash..strange.

---

### Post by bumanie on 2009-03-09
Pre-Hardy, use> sudo rm -rf /home/yourusername/.Trash/*

In Hardy and intrepid, use> sudo rm -rf /home/yourusername/.local/share/Trash/files/*


---

### Post by woodenbrick on 2009-03-10
I just remembered something, if you have separate partitions mounted then the trash from these other partitions will be located in a different place /the-mount-point-of-partition/.Trash-1000 so run the above command substituting that directory instead.

---

