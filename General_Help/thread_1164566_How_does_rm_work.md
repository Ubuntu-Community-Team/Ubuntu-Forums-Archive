---
title: "How does rm work?"
date: 2009-05-19
forum: General Help
---

### Post by randyklein99 on 2009-05-19
I made a rather egregious error today. Instead of using ls, I typed rm.  Don't ask how.  But I ended up typing:

```

rm -r /home/user/

```

Luckily, I got an error when rm hit the .gvfs directory and it stopped removing files.  Fortunately, this was done on a non-critical computer, so data loss was not a worry.  

But the only thing that I have noticed is missing are the files on the Desktop and my Firefox bookmarks and add-ons.  

I'm not sure what else got axed, so I'm wondering in what order does rm delete files?

---

### Post by WRDN on 2009-05-19
I'm not 100% sure, but, from what was removed, it appears files are deleted in alphabetical order (both hidden and viewable at the same time).

---

### Post by ActiveFrost on 2009-05-19
*rm -r* means that files are being deleted recursively, however, I'm not sure about from where it starts ( recursively by size, type, modification date, etc. ).

---

### Post by redmk2 on 2009-05-19
> **randyklein99 said:**
> I made a rather egregious error today. Instead of using ls, I typed rm.  Don't ask how.  But I ended up typing:

```

rm -r /home/user/

```

Luckily, I got an error when rm hit the .gvfs directory and it stopped removing files.  Fortunately, this was done on a non-critical computer, so data loss was not a worry.  

But the only thing that I have noticed is missing are the files on the Desktop and my Firefox bookmarks and add-ons.  

I'm not sure what else got axed, so I'm wondering in what order does rm delete files?

the command rm -r starts removing files in the current directory alphabetically. When it has removed all the files it descends into the next directory (alphabetically) and so on. after all the files are removed it removes the directories.

A neat way to prevent yourself from this happening again is to create a .bash_aliases file and add the following```
alias rm='rm -i'
```Then when you use rm it will always ask if you really want to remove this file/dir.

---

### Post by randyklein99 on 2009-05-20
> **redmk2 said:**
> A neat way to prevent yourself from this happening again is to create a .bash_aliases file and add the following```
alias rm='rm -i'
```Then when you use rm it will always ask if you really want to remove this file/dir.

That sounds like a great idea.  Can you expand on how to do that?

---

### Post by _Purple_ on 2009-05-20
Open the file ~/.bashrc using this command
```
gedit ~/.bashrc 
```

Then add the following line at the end of the file 
```
alias rm='rm -i'
```

Then save the file. You do not have to restart your PC for this change to take effect. Just close the terminal window and open a new one.

---

### Post by randyklein99 on 2009-05-20
Did it and it works.  Thanks a bunch for that.

---

### Post by b@sh_n3rd on 2009-05-20
> **_Purple_ said:**
> Open the file ~/.bashrc using this command
```
gedit ~/.bashrc 
```Then add the following line at the end of the file 
```
alias rm='rm -i'
```Then save the file. You do not have to restart your PC for this change to take effect. Just close the terminal window and open a new one.

Now, that's cool...thanks for the tip...I added it too :D

---

### Post by redmk2 on 2009-05-20
> **randyklein99 said:**
> That sounds like a great idea.  Can you expand on how to do that?

You will find all kinds of aliases as you go along.  The ~/.bashrc file can become cluttered.  The way to set up a .bash_aliases file is to ***uncomment*** this part of the ~/.bashrc file as shown below```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

Then you can create a ~/.bash_aliases file and add your aliases with your favorite text editor.

---

