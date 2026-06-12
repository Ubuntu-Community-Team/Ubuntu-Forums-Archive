---
title: "need a command i used a week ago"
date: 2006-01-12
forum: General Help
---

### Post by ice60 on 2006-01-12
hi, i used a command in terminal about a week ago which had a word i haven't used before. how do i tell terminal to find that command? or where are all the old commands kept so i can search for the word with gedit? thanks

---

### Post by kabus on 2006-01-12
enter in a terminal

```
history | grep *yourword*
```

and it will give you a list of recent commands containing *yourword*.

---

### Post by matthew on 2006-01-12
[quote=ice60]hi, i used a command in terminal about a week ago which had a word i haven't used before. how do i tell terminal to find that command? or where are all the old commands kept so i can search for the word with gedit? thanks[/quote]From a command prompt in the terminal use the up arrow to scroll back and see previously used commands or look in /home/username/.bash_history

---

### Post by Jave27 on 2006-01-12
Easiest way: Press the up arrow a bunch of times until you find it.  If the last one that appears is newer than when you typed your command, you're out of luck.

I can't remember off-hand which file that history is stored in, but look in your home directory by typing "ls -a" to get all of the hidden folders, and I think it's under ".bashrc/" or something like that.

---

### Post by hillbilly on 2006-01-12
You could also do an "escape" then "/" and type a part of the command you used and press enter, and the shell will display the complete command containing the part you typed !! If it doesnt show up, it means that the command has not been used in some time. And this sequence will only work if  you have set vi as yoru history editor. You can do this temporarily by
> set -o vi

---

### Post by GeneralZod on 2006-01-12
[QUOTE=hillbilly]You could also do an "escape" then "/" and type a part of the command you used and press enter, and the shell will display the complete command containing the part you typed !! If it doesnt show up, it means that the command has not been used in some time. And this sequence will only work if  you have set vi as yoru history editor. You can do this temporarily by[/QUOTE]

CTRL+R does a similar thing - press CTRL+R, start typing your command, and the last line you've entered that contains the characters you typed is displayed.  Keep pressing CTRL+R to see earlier ones! :)

---

### Post by Thirsteh on 2006-01-12
gedit ~/.bash_history       -- almost the same thing as history but might be a little easier to browse?

---

### Post by ice60 on 2006-01-12
thanks everyone. i just managed to find the command before i rechecked back here :rolleyes: but i'm glad i asked because all the answers helped me learn something. i think i need to learn more about grep, i have the man open but i need to learn man first :D 

does anyone know where i can learn how to use, i think it's man? i don't think it's man, i'm looking at it now - "man man". it's the program which it runs in i need help with, Vi?? i once had a help man or file open in terminal which started by saying press such and such to move forward then "n" to go back again. it showed how to know where you are, which "chapter" came next, which was before etc can anyone help?

---

### Post by hillbilly on 2006-01-12
I think you are talking about info man !! Is that it ?

---

### Post by ice60 on 2006-01-12
[QUOTE=hillbilly]I think you are talking about info man !! Is that it ?[/QUOTE]
it's similar but i don't think that's it. i don't think it was man but the program it self because it says staright away how to navigate around in it e.g. up and down keys or whatever the key is to move to the end of the paragraph then "n" to get back again. 

it then goes on to explain what this, at the top, means
```
File: *manpages*,  Node: man,  Up: (dir)
```

---

### Post by hillbilly on 2006-01-12
No no what i mean was > $/> info man or
$/> info ls

Is the program you are looking for "info" ??

---

