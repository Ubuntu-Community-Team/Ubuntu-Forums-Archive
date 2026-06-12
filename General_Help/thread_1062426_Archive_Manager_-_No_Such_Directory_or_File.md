---
title: "Archive Manager - No Such Directory or File"
date: 2009-02-06
forum: General Help
---

### Post by alea21 on 2009-02-06
So everytime I go to install something this message comes up along with the code line:

Cannot access archive. No such file or directory.

[CODE LINE HERE]

How do I fix this? I have no idea what I need to put into the archive.

---

### Post by mb_webguy on 2009-02-06
Sorry, but I'm a bit confused.  What does Archive Manager have to do with installing anything?  Archive Manager is what you use to extract zip files and other file archives.  

Are you talking about a package manager, like Synaptic?

---

### Post by alea21 on 2009-02-06
Archive Manager appears when that message comes up so I was assuming it had something to do with that.

---

### Post by mb_webguy on 2009-02-06
How exactly are you trying to install something?  What *exactly* are you doing to cause that message?

---

### Post by alea21 on 2009-02-06
Whenever I try to install anything - Installing my printer following [this](http://ubuntuforums.org/showthread.php?t=590793&highlight=install+brother+printer) thread. Just installing anything that isn't on the Add/Remove List it comes up with that.

---

### Post by mb_webguy on 2009-02-06
Which command is giving you the problem, dpkg?

It sounds like either you're in the wrong directory or else you've typed the name of the file incorrectly.  Use the "ls" command to make sure the file you're trying to install is actually in the directory you think it is.  If it's there, then make sure you're typing the name correctly.  Remember, Linux is case-sensitive, so "myfile.txt" and "MyFile.txt" are not the same.  An easy way to make sure you're typing a long filename correctly is to start typing the name and then hit the Tab key to autocomplete the name.

---

### Post by alea21 on 2009-02-07
I got the printer working but whenever I try to install something via the executable setup file it comes up with:

An Error Occured While Opening the Archive

(null)

Command Line Output
[collapsible box here]

---

### Post by alea21 on 2009-02-07
*bump* - I really need help! I can't install anything that needs to use an executable file to run it.

---

