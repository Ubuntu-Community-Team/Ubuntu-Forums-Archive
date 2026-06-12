---
title: "File-roller doesn't show an overwrite confirmation dialog"
date: 2009-06-09
forum: General Help
---

### Post by rolandpish on 2009-06-09
Hello.
I'm using file-roller to handle my archive files. The problem is that it doesn't show an overwrite confirmation dialog when a file exists.

How can I enable this option in file-roller?

Is there another archive manager which has this option?

Thanks in advance

---

### Post by michy99 on 2009-06-09
What version of Ubuntu and what version of file-roller are you using?

Is this what you are looking for?

---

### Post by rolandpish on 2009-06-09
> **michy99 said:**
> What version of Ubuntu and what version of file-roller are you using?

Is this what you are looking for?

Thanks Michy.
First I tried checking the "overwrite existing files" checkbox. But file-roller simply overwrite the existing files without confirmation.
Then I tried unchecking that option, but when I extract the files it just doesn't overwrite the existing files and tells me nothing.

I usually extract a compressed file and I need to overwrite some of the files inside it. That's why I need some sort of "overwrite confirmation dialog".

I just installed Ark and it has exactly what I need, but the problem is that Ark doesn't handle (creation and extraction) of password protected files.

Any help is greatly appreciated.

Thanks

---

### Post by michy99 on 2009-06-09
The only other thing I can suggest is using the command-line for whatever archive format you are using (rar, zip, tar, etc.) It is a little more involved, but you have more control over the process. Just use the man command to read the manual page for each command.

---

### Post by rolandpish on 2009-06-09
> **michy99 said:**
> The only other thing I can suggest is using the command-line for whatever archive format you are using (rar, zip, tar, etc.) It is a little more involved, but you have more control over the process. Just use the man command to read the manual page for each command.

Thanks again Michy.
The problem is that sometimes this task is performed by another person who is not likely to use the console and prefers a GUI.

Well, I will keep trying other archive managers.

Thanks!

---

### Post by michy99 on 2009-06-09
I agree that it is an oversight in file-roller. Maybe it will be addressed in future releases. I know that the current release has features that were not in earlier versions.

---

### Post by rolandpish on 2009-06-09
> **rolandpish said:**
> 
I just installed Ark and it has exactly what I need, but the problem is that Ark doesn't handle (creation and extraction) of password protected files.


Ok. I realized that Ark can extract password protected files. What Ark doesn't do is create a new zip password protected file.

For now I can create the password protected files with file-roller and do everything else with Ark.

Thanks a lot for your help!

---

