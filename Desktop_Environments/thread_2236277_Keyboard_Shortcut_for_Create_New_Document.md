---
title: "Keyboard Shortcut for Create New Document"
date: 2014-07-25
forum: Desktop Environments
---

### Post by vni.jamie on 2014-07-25
I'd like to make a keyboard shortcut similar to ctrl+shift+n that will create a new document in the active folder.

I was hoping I could just add something to they keyboard shortcuts in preferences along the lines of 

ctrl+alt+n = touch {$current_dir}/newfile

However I'm not sure what to put in place of {$current_dir} or if there is any system variable I could use there at all.

---

### Post by Jim_Nora on 2014-07-25
Would using a single '.' work?  At a bash prompt '.' refers to the current directory, and '..' refers to the parent directory.
Perhaps
           ctrl+alt+n = touch ./newfile
would work in this setting.

---

