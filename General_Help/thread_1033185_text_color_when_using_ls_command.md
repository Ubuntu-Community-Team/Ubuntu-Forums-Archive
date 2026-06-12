---
title: "text color when using ls command"
date: 2009-01-07
forum: General Help
---

### Post by pdah on 2009-01-07
Hi everybody, 
I'm using black color for the background of terminal. Each time using 'ls' command, I can't see the folder with mode 777 cause it's background color is green and the text is in black. Do you know how to change the color for this kind of folder ? I tried to search a lot on google but didn't find a solution yet.
Thanks.

---

### Post by nothingspecial on 2009-01-07
```
gedit .bashrc
```

Look for the line ```
alias ls='ls --color=auto'
```

Put a # in front of it.

Save 
Close
```

bash
```  to restart bash

Now ls will output only in white

It would be a good idea to read up on editing your .bashrc before you do this. Don't change anything else and make sure you get this right.

You are commenting out an alias. That particular alias tells yhe terminal to use colour in the out put for ls. So every time you type ls bash interprets it as ls --colour=auto.

Alias`s are usefull. I always put a few in my .bashrc after installing.
For example to connect to my server graphically I type ```
ssh -X -C -c blowfish user@192.168.1.3
```

I can`t be bothered to type that every time so in my .bashrc, I add a line

```
alias server='ssh -X -C -c blowfish user@192.168.1.3'
```

Now to access my server I just type ```
server
```

---

### Post by pdah on 2009-01-07
Thanks for your reply. Anyway, my point is not disabling all the color here, I just want to change the color in the case when folder permission is 777.

---

### Post by Thanoulis on 2009-01-07
The colors in the *ls --color=auto* command are handled by the *dircolors* command. Look into the manual of dircolors to see how you want to display your ls colors.
Another way is to change the 777 attribute to 755.
```
chmod 755 <dirname>
```
That way it won't have the greenish background.

---

