---
title: "Help, How do I remove an entire directory?"
date: 2009-01-19
forum: General Help
---

### Post by vandorjw on 2009-01-19
I have to remove an a directory and all its files. How do I do this?

rmdir -f help (didn't work)

ps: help is filled with files.

I need an answer in the next hour.

thanks in advance

---

### Post by p_quarles on 2009-01-19
Try:
```
rm -ri /path/to/dir
```
The i stands for "interactive," and prompts you about each file. Safer is to use a file manager to move the directory to trash.

---

### Post by oldos2er on 2009-01-19
What do you mean "help is filled with files"? Hopefully you're not deleting anything outside your /home.

---

### Post by p_quarles on 2009-01-19
> **oldos2er said:**
> What do you mean "help is filled with files"? Hopefully you're not deleting anything outside your /home.
"help" is the name of the directory. rmdir won't by default execute a request to remove a directory that has contents.

---

### Post by mbeach on 2009-01-19
perhaps look up the "rm" command.  
```

man rm
```

specifically take a look at the Options for --recursive

its a good idea to use the full path to the folder to make sure you don't delete something you didn't mean to.

---

### Post by vandorjw on 2009-02-04
Thanks for the replies. I went around the problem by graphically logging in to the remote computer. Whoever said that help was a directory was correct.

Before I had graphical capabilities,it was necessary for me to know how to do it using the command line. But now I can  right click and delete things.

Thanks for the quick responses, I got them on time. Just didn't bother to reply until now.

Cheers - CC7:popcorn:

---

