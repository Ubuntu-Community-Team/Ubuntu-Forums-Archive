---
title: "want to know about some command"
date: 2009-05-08
forum: General Help
---

### Post by muctadir on 2009-05-08
rm -f 
rm -rf

what does these commands do??????????

---

### Post by alexandari on 2009-05-08
the command **rm -rf *** removes everything from the directory you`r in.
If you just type it without a **cd** command before that,kiss your /home bye buye

---

### Post by _sAm_ on 2009-05-08
Open a terminal and type 
man rm
and you will get a good explanation. 

Instead of a terminal you can also use this webpage: [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by muctadir on 2009-05-08
then how can i use it safely???

please give me an example.........

---

### Post by Alekz_ on 2009-05-08
The rm (remove) command deletes a file/folder

-f means 'force' and -rf means 'recurcivily' and 'force', which could(and will) remove every file/folder below the folder you're!

---

### Post by mcduck on 2009-05-08
rm is the command used to delete files/directories. "-f" (as in "force) makes it force the removing, without asking user confirmation for anything. And "-r" ("recursive") makes it do a recursive delete, removing all subdirectories and their contents as well. (without -r, rm refuses to delete directories that are not empty).

Pretty normal command, and definitely a necessary one. But also one you should be careful with as there's no way to undo if you accidentally remove wrong file or run the command in wrong place.

As a general rule, I'd recommend never using the -f option with rm unless you really, really know that you need it. It's a bit safer that way, and in general there's no reason to use excessive force to do every little thing.

To use rm safely, just forget about the "force" and only use "recursive" when you need to. And check the command you typed before executing it, you don't want any typos or the result might be completely different form what you tried to do.

Pretty much the same thing as always when you are deleting stuff. You just need to make sure you don't delete wrong files.

---

### Post by Alekz_ on 2009-05-08
> **muctadir said:**
> then how can i use it safely???

please give me an example.........
Example:

```
 rm -rf /tmp/* 
```

It you remove EVERYTHING into you /tmp diretory!

Becarful! It won't ask IF you really want to delete!

---

### Post by mcduck on 2009-05-08
> **Alekz_ said:**
> Example:

```
 rm -rf /tmp/* 
```

It you remove EVERYTHING into you /tmp diretory!

Becarful! It won't ask IF you really want to delete!

..and if you mistype the command like this (notice the space after first slash):
```
 rm -rf / tmp/* 
```
..you'll end up deleting everything on your system. Or at least everything the user running the command can delete.

That's why you should be careful. An not use options like "-r" and "-f" unless you really need them. Most of the time you don't.

---

### Post by muctadir on 2009-05-08
then tell me what command is safer to do the same work.......????????



what about using cd with the rm command.. what will it do????

---

### Post by kaibob on 2009-05-08
> **muctadir said:**
> then tell me what command is safer to do the same work.......????????
The -i option prompts before deleting a file or directory and is safer:

```
rm -i file
```

You can add the -r option if you want to delete files and directories recursively.

---

### Post by Alekz_ on 2009-05-08
Well... SAFER is you remove files and folders from your graphic interface..

But, IF you NEED to remove from command line, type the full path of what you want to delete!

Example:
```
rm -f /home/somebody/Desktop/myfolder/file
```

or

```
rm -r /home/somebody/Desktop/myfolder
```

if you want to delete a folder!

---

### Post by bodhi.zazen on 2009-05-08
> **muctadir said:**
> then tell me what command is safer to do the same work.......????????



what about using cd with the rm command.. what will it do????

Define "safe"

I alias rm, cp, and mv to use -i in .bashrc

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

the -i flag == "interactive" and will give confirmation.

See the difference ?

```

# make 2 empty files
bodhi@ufbt:~$ touch foo foo-you

# Call rm directly (no alias) , foo is removed without confirmation
bodhi@ufbt:~$ /bin/rm foo                             

#Call rm w/ alias, confirmation is required to remove foo-you
bodhi@ufbt:~$ rm foo-you                                      
rm: remove regular empty file `foo-you'? y
bodhi@ufbt:~$
```Note -i is over ridden by -f
-r = recursive

```
bodhi@ufbt:~$ mkdir foo && touch foo/{file_1,file_2}

bodhi@ufbt:~$ ls foo                                          
file_1  file_2

# -f overrides -i
bodhi@ufbt:~$ rm -rf foo                                      

bodhi@ufbt:~$ mkdir foo && touch foo/{file_1,file_2}
bodhi@ufbt:~$ rm -r foo                                       
rm: descend into directory `foo'? y
rm: remove regular empty file `foo/file_1'? y
rm: remove regular empty file `foo/file_2'? y
rm: remove directory `foo'? y
```So if you use rm -rf you need to confirm your path before you hit enter.

FYI ; rm -rf / does nothing on Ubuntu :

```
bodhi@ufbt:~$ **[COLOR=darkred]sudo rm -rf /[/COLOR]**
[sudo] password for bodhi:
**[COLOR=green]rm: cannot remove root directory `/'[/COLOR]**
bodhi@ufbt:~$ 
```:twisted:

---

