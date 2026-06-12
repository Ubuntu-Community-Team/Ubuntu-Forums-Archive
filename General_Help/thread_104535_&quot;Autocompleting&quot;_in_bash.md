---
title: "&quot;Autocompleting&quot; in bash"
date: 2005-12-16
forum: General Help
---

### Post by Nasso on 2005-12-16
At school they dont use bash, they use zsh, or something like that. Zsh has a feature i really want in my terminals! If you type in a part of a filename and press TAB it will autocomplete as much as possible. If you hit TAB once more it will start to cycling through the available files.

An example. I got 2 files named filename.pdf and filename.png. I write file and press TAB, it will autocomplete out "filename." for me. Now i hit TAB once more and the first possible file is completely written out in the terminal, filename.pdf that is. If i hit TAB once more filename.png will be written out and if i hit it once again it will cycle and filename.pdf will be written again.

To my question. Can i get this feature in ubuntu?

---

### Post by Zelut on 2005-12-16
That feature should be in by default.  I use it everytime I'm in the terminal.... have you tried it?

---

### Post by Nasso on 2005-12-16
[QUOTE=kuyaedz]That feature should be in by default.  I use it everytime I'm in the terminal.... have you tried it?[/QUOTE]

In my terminal it just prints a list of the possibilities. It doesnt autocomplete cyclic when i hit tab twice.

---

### Post by Casey on 2005-12-16
[QUOTE=kuyaedz]That feature should be in by default.  I use it everytime I'm in the terminal.... have you tried it?[/QUOTE]

Autocomplete in bash will only complete to the last common letter.  Pressing autocomplete again will list the files with that name.  Personally, I like this behavior but I think he's looking for this portion:

"Now i hit TAB once more and the first possible file is completely written out in the terminal, filename.pdf that is. If i hit TAB once more filename.png will be written out and if i hit it once again it will cycle and filename.pdf will be written again."

Edit: Sorry for the late reply =)

---

### Post by lcg on 2005-12-16
[QUOTE=Nasso]At school they dont use bash, they use zsh, or something like that. Zsh has a feature i really want in my terminals! If you type in a part of a filename and press TAB it will autocomplete as much as possible. If you hit TAB once more it will start to cycling through the available files.[/QUOTE]
Maybe I'm missing something, but if you want the features of zsh, why not just install zsh? ;)
```
$ sudo apt-get install zsh
$ chsh -s /usr/bin/zsh
```

Et voilà, zsh in your terminals.

HTH,
Lars

---

### Post by Nasso on 2005-12-16
[QUOTE=lcg]Maybe I'm missing something, but if you want the features of zsh, why not just install zsh? ;)
```
$ sudo apt-get install zsh
$ chsh -s /usr/bin/zsh
```

Et voil&#224;, zsh in your terminals.

HTH,
Lars[/QUOTE]

oh, i didnt think it was so easy to change :) thanks!

edit: That didnt work :( Well, it worked, it didnt give me any errors but i still dont have the functionality i want :(
thx anyway!

---

