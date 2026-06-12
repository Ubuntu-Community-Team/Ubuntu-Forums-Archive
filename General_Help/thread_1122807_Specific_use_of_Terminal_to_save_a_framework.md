---
title: "Specific use of Terminal to save a framework"
date: 2009-04-11
forum: General Help
---

### Post by tinoater on 2009-04-11
Using Mac OSX Leopard. Im not sure if this is the right place to post but terminal in google returned this site.
Accidentally I moved, not copied, a framework from one place to another, now, not suprisingly, no applications will start. I have started the computer in single user mode but I can't get the syntax right to copy the folder back to its original position. If anyone could help me I would be grateful, these forums seem to be very prompt and knowledgable.

Problem:Transferred /System/Library/Frameworks/ApplicationServices.framework/Versions/A/Frameworks/LaunchServices.framework to
/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks

I need to copy the whole folder with contents back to the other folder, im unsure of the syntax, ie cp -r? Any help would be excellent.

---

### Post by schmidtbag on 2009-04-11
lol you're on the ubuntu forums, and ubuntu is a distribution of linux, you have the wrong OS.  look up "insanely mac", i've encountered those forums before when looking up stuff.

both linux and mac have terminals because they're both unix/bsd based, so, both will have some of the same basic commands.

i may be able to answer your quesiton anyway.  i believe mac does have the "sudo" command (if not, look up online how to become root in mac) and then just do "sudo mv -rf /System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks /System/Library/Frameworks/ApplicationServices.framework/Versions/A/Frameworks/LaunchServices.framework"

you may need to remove the "-rf", i'm not entirely sure, i don't use the command almost ever

---

### Post by tinoater on 2009-04-11
Well thats embarrasing. Thanks for the pointer Ill post at insanely mac, sorry about this. I tried your code, and I removed the -rf but it returns that its a read only file system? So do you know how to get around this?

---

### Post by schmidtbag on 2009-04-11
the r in "-rf" means recrusive, meaning, the folder you chose and every succeeding folder and file within it.  f means force, so it ignores things like a read-only system

---

### Post by tinoater on 2009-04-12
When I do use the -rf I get a whole host of errors on each file as far as I can tell, things like "Bad file descriptor", "no such file or directory", "Unable to copy extended attributes". Any ideas? Im not gonna pretend to know what any of that really means.

---

### Post by tinoater on 2009-04-12
Its sorted now guys :). Thank you for your help, im surprised by how prompt it was.
Thank you again.

---

### Post by schmidtbag on 2009-04-12
your welcome, hopefully you'll switch to linux some day!  theres a whole section in these forums for people who use macs and they may be able to help you out

---

