---
title: "Searching for question marks"
date: 2008-02-09
forum: Desktop Environments
---

### Post by amiga_os on 2008-02-09
I'm trying to copy a lot of files to an external harddrive.  It's formatted with FAT32.  ext3 supports several characters that FAT32 doesn't.

Many of these I can search for with Places->Search for Files... for example a colon.  But how do I search for a question mark?  It's a wildcard character, and the search seems to treat it like that...

One day, a nifty little feature would make a whole directory tree "FAT compatible" at the click of a button.

---

### Post by scorp123 on 2008-02-09
> **amiga_os said:**
>  But how do I search for a question mark? Escape it. Means: Put a backslash "\" in front of it.

I just created this file:  "Can you read this?.txt"```
 touch "Can you read this?.txt" 
``` And now when I search for it .... ```
find . -name '*\?*' -print
``` ... It gets found: ```
> find . -name '*\?*' -print
./Can you read this?.txt 
```

BTW, explanation for the command above: **[COLOR="Blue"]find . -name '*\?*' -print[/COLOR]**
The syntax is:  **find** *where-to-look* **-name** *what-to-look-for* **-action1 -action2 -action3** .... 

[LIST]
[*][COLOR="Red"]find[/COLOR] : name of the command we execute here.
[*][COLOR="Red"] .[/COLOR] : a dot " . " means "right here" in terminal speak; e.g. I want "find" to search the current directory.
[*] [COLOR="Red"]-name[/COLOR] : we tell the command that we know the name of what we are looking for.
[*] [COLOR="Red"]'*\?*'[/COLOR] : search for anything that might have a question mark somewhere in its name; treat the question mark as a character and not as a wildcard.
[*] [COLOR="Red"]-print[/COLOR] : print the name and location of a file with these characteristics.
[/LIST]

More examples (I created the files via the "touch" command):
```
> find . -name '*\?*' -print
./Can you read this?
./Can you find me? Can you read this? Really?? No kidding?.txt
./Can you read this?.txt
```

---

### Post by amiga_os on 2008-02-10
Thanks scorp... however...

Just recreated your test... with a file with the same name.  It turned up using find on the command... however it doesn't turn up with the Places->Search for Files gui.

I tried *\?* and \? (which I'd tried already anyway).

Is there any way to run this search in the gui?

---

### Post by scorp123 on 2008-02-10
> **amiga_os said:**
>  Is there any way to run this search in the gui? I tried myself and it indeed seems to ignore the question mark as search argument, no matter how you write it. It seems that the capabilities of this GUI file search are very limited, so you'd probably have to use the terminal anyway.

---

### Post by amiga_os on 2008-02-10
Yeah... thanks again scorp

I'm going to post this as a bug

---

### Post by juan_suave on 2008-02-18
Thanks!  This helped with renaming a bunch of MP3s that wouldn't copy to my ipos.. i mean ipod.  :)

---

