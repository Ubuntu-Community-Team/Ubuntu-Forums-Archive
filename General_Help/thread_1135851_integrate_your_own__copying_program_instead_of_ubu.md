---
title: "integrate your own  copying program instead of ubuntus copying program"
date: 2009-04-24
forum: General Help
---

### Post by khizar on 2009-04-24
i am doing a semester project whr i am tryng to write a file copier tht will resume the copied file in case of an interuption like copy handler in windows. can i integrate it into the OS such tht if i copy and paste something, my program is used instead of the program tht comes with ubuntu??
this will just make a gud , easy to use software n might get me a little extra credit :).
so guys any help will be greatly appreciated
cheers
khizar

---

### Post by jsowoc on 2009-04-24
As far as I know, the program "cp" is called whenever any copying is done. If you are able to write a (reliable) replacement for cp, you could replace the file, and your cp will be used.

Just make sure your version of "cp" supports all the command-line arguments that the original "cp" supports. ;-)

---

### Post by issih on 2009-04-24
You can just make an alias

[http://sillydog.org/unix/shell/alias.php](http://sillydog.org/unix/shell/alias.php)

That way your command is launched whenever cp is called, that should do it. You really will need to make your version compatible with the cli parameters of cp though, or you may break anything that relies on it.

Hope that helps

---

### Post by khizar on 2009-04-25
thanx alot guys...
this freedom is just wat never lets me go back to windows....:D

---

