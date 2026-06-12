---
title: "Synaptic Packet Manager"
date: 2009-02-26
forum: General Help
---

### Post by phr33k-dc on 2009-02-26
For example i install secure-delete in the synaptic manager but i cant find it to run it? i tryed 'run' and a couple of other things but cant get at it. Iv install other things and how come i can run them with 'run'???
Any help greatly appreciated.....

---

### Post by jelle_ on 2009-02-26
secure delete uses command line. try to open it in a terminal

---

### Post by phr33k-dc on 2009-02-26
what command should i use for terminal?

---

### Post by geirha on 2009-02-26
search it up in synaptic, right click it, select properties, then look at the "installed files" tab. 

If it installs a .desktop-file under /usr/share/applications, then that means it adds an entry in the menu (i.e. it is a gui application). 

If it isn't a gui applications, look for files installed in /usr/bin/ or /usr/games/. If it installs /usr/bin/foo, then you can open a terminal and run "foo", though it's advicable to first run "foo --help" or "foo -h" first, to get a short description of what the program does (most programs accept the --help and/or -h option, but not all, so it's more of a rule of thumb). 

If it doesn't install anything under /usr/bin or /usr/games, then the package is probably a library or a documentation package.

You can also get a list of the files it install with the terminal command ```
dpkg -L *packagename*
```

---

### Post by phr33k-dc on 2009-02-26
the package looks like its installed undeer usr/bin but for foo in the terminal its say 'command not found'

---

### Post by mb_webguy on 2009-02-26
Hehe...  Geirha was using "foo" as a generic program name.  Substitute the name of your program for "foo".

---

### Post by thtrgremlin on 2009-02-26
the command to use secure-delete is 'shred'.

I'd recommend reading the manual:```
man shred
``` in general, but I found a great page that should get you started:[http://www.techthrob.com/tech/securedelete.php]("http://www.techthrob.com/tech/securedelete.php").

What you would probably really want is to add a script to nautilus that will allow you to right click on files and delete them securely, but that is a bit more of an adventure, but worth investing some time into.

---

### Post by phr33k-dc on 2009-02-26
still nothing in command line after that and im sure its not a library or something. Could somebody try it please? its very small. that would be great help

---

### Post by phr33k-dc on 2009-02-26
thanks man was writing my post wen u posted. cheers il try it

---

### Post by jonobr on 2009-02-26
the command your looking for is shred

if you type 

```
shred --help
```

it will give the options, recommend you reasearch the program using howtos or knowledge articles before executing

---

### Post by phr33k-dc on 2009-02-26
Do i have to use this program in terminal?

---

### Post by jonobr on 2009-02-26
eek, the answer was given before my post , sorry

---

### Post by phr33k-dc on 2009-02-26
Do i have to use this program in terminal???

---

### Post by phr33k-dc on 2009-02-26
Could you tell me how to add a script to the nautalis so i just have to right click to delete them securly? if answer is too long just email me at [email]davecarr26@gmail.com[/email]
Thanks in advance for any help

---

### Post by phr33k-dc on 2009-02-26
If anyone has any ideas just post 'em up

---

### Post by oldos2er on 2009-02-26
[http://linux.softpedia.com/get/Desktop-Environment/Tools/shred-file-32162.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/shred-file-32162.shtml)

---

### Post by phr33k-dc on 2009-02-26
sorry this is getting over my head. could someone give me a step by step guide to do what that link says in it? sorry

---

### Post by phr33k-dc on 2009-02-26
What is the path i should put in for shred in the Nautilus Actions Configuration?

---

### Post by phr33k-dc on 2009-02-26
Anything guys

---

### Post by thtrgremlin on 2009-02-26
Not to throw you in over your head, but 'man bash' can get you started with regard to scripts, as well as the power of the command line. basically, a script begins with '#!/bin/bash' and after that just type the list of commands into the file. When you run the script, it will run all the commands just like you had typed them into the terminal.

[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/") is a good site to get started pretty quickly.

If you feel like you have been thrown into the deep end with regard to this info, just put in the back of your mind as something to possibly try if you are feeling adventurous one day. scripts are fun and have virtually unlimited potential.

Best luck, and sorry for the slow reply.

---

### Post by phr33k-dc on 2009-02-26
hey no bother about it but im just tring to install this one thing and then ill let it go. ill be up all night if i dont get it. is there any chance you could do it and tell me what to do or even just tell me what to do?

---

### Post by phr33k-dc on 2009-02-26
I have the script but how to i implement it into nautilus and shred

---

### Post by phr33k-dc on 2009-02-26
u can email me if the post is too long

---

### Post by phr33k-dc on 2009-02-26
please anyone?

---

### Post by jonobr on 2009-02-26
A chara

Dia dhuit as an USA.
Fan noimead agus tarraing anáil......

Your posting is fast a frenetic and makes it look like the Gardai are about to break down your door.

I am guessing bash scripting is too much work for you  and will not accomplish much for you until you have the time and patience to learn it.

errors in scripting the shred command could have terrible effects on your system if you get it wrong.,


All that being said, tell me what the major problem is,
You want to completely remove a file from your system,
is this the cause of your agitation?

If so, Im taking it the Shred command is working based on your posts.
Now that that is working, what do you want to get rid of and whats the problem running it command line.

You seem to be showing some urgency, but it looks as if you have what you need to get the job done.
(unless Im missing something)

---

### Post by phr33k-dc on 2009-02-27
no no its ok no rush and sorry bout late reply. i was getting very annoyed and any help you can give will be well appreciated.
p.s are u irish living in the usa?

---

### Post by jonobr on 2009-02-27
> living in the usa? 

Yep.

> are u irish

UP THE ROYAL.......

Does that answer that question? :P

---

### Post by phr33k-dc on 2009-02-28
Ha ye that answers my question........ Up the IRISH!

---

