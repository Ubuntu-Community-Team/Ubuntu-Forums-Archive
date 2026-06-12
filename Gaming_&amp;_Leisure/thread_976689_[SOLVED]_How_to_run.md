---
title: "[SOLVED] How to run?"
date: 2008-11-09
forum: Gaming &amp; Leisure
---

### Post by tadcan on 2008-11-09
Ok I downloaded 'battle for wesnoth' and 'book of eschalon' and opened them with the package manager. In 8.04 I was able to find a file and run it.

Now in 8.10 i don't seem to be able to....

---

### Post by crazyfuturamanoob on 2008-11-10
> **tadcan said:**
> Ok I downloaded 'battle for wesnoth' and 'book of eschalon' and opened them with the package manager. In 8.04 I was able to find a file and run it.

Now in 8.10 i don't seem to be able to....

Any error messages? Have you tried re-install? What is the problem? :confused:

---

### Post by tadcan on 2008-11-10
Basically i dont know how I got it to start in 8.04 or the correct way to start the programs. I have unzipped the packages into the home folder. Before I was able right click on an icon choose run and play the game. 

That doesn't seem to work. And being a total noob I'm lost.... :(

---

### Post by jorj82 on 2008-11-10
Try installing the games from **Applications -> Add/Remove**, and they'll show up under **Applications -> Games**

---

### Post by tadcan on 2008-11-10
That worked for wesnoth, but book of eschalon is not in the repos.

---

### Post by Perfect Storm on 2008-11-10
> **tadcan said:**
> That worked for wesnoth, but book of eschalon is not in the repos.

Normally commercial games you won't find with a .deb or with a repo.
They have to be installed "manually".

Stuff that aren't part of the repo won't be listed either.


Buy the way book II will soon be released, hopefully they make it available to be bought through greenhouse, so we have something like steam for linux.

---

### Post by tadcan on 2008-11-10
Ok, so is there a guide to doing manual installs?

I have installed fallout (first one) to fill my rpg needs. :guitar:

Edit. Saw the link! found a guide. Trying it now.

---

### Post by tadcan on 2008-11-10
Ahh I'm so close. I got down to entering the info into the launcher atthe very end.

I chose type: application
        Name: As listed in guide
        Command: sh /home/tadcan/.Games/eschalon_book_1_demo/Launch_ES1.sh
(Since I got the demo I changed the line)

So I see the game listed in the games section. But it doesn't launch when I click on it. I don't even know where to Browse for it to find the correct command. Any ideas?

---

### Post by Perfect Storm on 2008-11-10
Try exexcute this command in the terminal, it may tell you what went wrong;

```
sh /home/tadcan/.Games/eschalon_book_1_demo/Launch_ES1.sh
```

You can't see the .Games folder in your home directory. The dot infront of files and folders name makes them hidden (do not change files/folders hidden ad libitum as it counts as name change).
In the file-browser you can set it to show hidden to go in there to make changes.

---

### Post by tadcan on 2008-11-11
I got this response

```
/home/tadcan/.Games/eschalon_book_1_demo/Launch_ES1.sh: 4: ./eschalon_book_1: not found
```

Looks like I made a mess of something earlier. 

The install involved some guess work. i.e changing _demo

And doing things in the terminal I have never done before. This bit esp confused me. 


Add the following;

#!/bin/bash

cd ~/.Games/eschalon_book_1
./eschalon_book_1

Save [ctrl] + [o] and exit [ctrl] + [x].

---

### Post by Perfect Storm on 2008-11-11
This is the path to its folder;

cd ~/.Games/eschalon_book_1

cd = change directory
~/.Games/eschalon_book_1 = the path. Note the ~ infront. It means it will look in the users directory (the user you're logged into). So it means /home/<user>/.Games/eschalon_book_1
Also note there's a diffrences in upper and lower cases letters.

So you have to change this line as well to fit the demo.
cd ~/.Games/eschalon_book_1_demo

./eschalon_book_1 = Will execute the binary file.

---

### Post by tadcan on 2008-11-12
I ran this and it seemed to work
```
cd ~/.Games/eschalon_book_1_demo
```

I presumed this ```
./eschalon_book_1_demo
``` was for the menus as a link for the button in games.

I tried to launch and got an error message. "Failed to execute child process. file or directory does not exist "

In the terminal ```
tadcan@Quad:~$ ./eschalon_book_1
bash: ./eschalon_book_1: No such file or directory
tadcan@Quad:~$ ./eschalon_book_1_demo
bash: ./eschalon_book_1_demo: No such file or directory
tadcan@Quad:~$ 
```

---

### Post by Vadi on 2008-11-12
Try dragging the "eschalon_book_1" file from the file manager into the terminal and pressing enter. It'll find it then.

(and this is why stuff should be in canonical's partner repository! ;))

---

### Post by Perfect Storm on 2008-11-12
> **tadcan said:**
> I ran this and it seemed to work
```
cd ~/.Games/eschalon_book_1_demo
```

I presumed this ```
./eschalon_book_1_demo
``` was for the menus as a link for the button in games.

I tried to launch and got an error message. "Failed to execute child process. file or directory does not exist "

In the terminal ```
tadcan@Quad:~$ ./eschalon_book_1
bash: ./eschalon_book_1: No such file or directory
tadcan@Quad:~$ ./eschalon_book_1_demo
bash: ./eschalon_book_1_demo: No such file or directory
tadcan@Quad:~$ 
```

You can't execute the file at **tadcan@Quad:~$**
You need to change directory in the terminal.

```
cd ~/.Games/eschalon_book_1_demo
./eschalon_book_1
```

---

### Post by tadcan on 2008-11-12
Not sure what you mean by file manager. 

I reveled the hidden files and found and .Games folder in the Home dir. 

Ecshalon is there.

---

### Post by Perfect Storm on 2008-11-12
> **tadcan said:**
> Not sure what you mean by file manager. 

I reveled the hidden files and found and .Games folder in the Home dir. 

Ecshalon is there.

file manger = file browser

please post the outcome of this;

```
cd ~/.Games/eschalon_book_1_demo
ls -a
```

---

### Post by tadcan on 2008-11-12
```
tadcan@Quad:~$ cd ~/.Games/eschalon_book_1_demo
tadcan@Quad:~/.Games/eschalon_book_1_demo$ ls -a
```

---

### Post by Vadi on 2008-11-12
Go to places - search for files, and search for "eschalon_book_1". Where does it find it?

---

### Post by tadcan on 2008-11-12
/home/tadcan/Desktop/eschalon_book_1_demo
/home/tadcan/Desktop/eschalon_book_1_demo.tar.gz
/home/tadcan/Desktop/eschalon_book_1_demo/eschalon_book_1_demo

---

### Post by Vadi on 2008-11-12
*"/home/tadcan/Desktop/eschalon_book_1_demo"* means that the file should be right on your desktop. Try double-clicking on it, does it start? If no, right-click, select properties, permissions, allow executing as program, and double-click to start.

---

### Post by tadcan on 2008-11-12
I clicked on the icon with two blue cogs and nothing happens.

As in the screen shot

---

### Post by Vadi on 2008-11-12
OK. I'll make you a video in a moment.

---

### Post by Vadi on 2008-11-12
See this: [http://dl.getdropbox.com/u/84880/Delete%20Nov%2024th/eshalon-on-ubuntu-1.ogv](http://dl.getdropbox.com/u/84880/Delete%20Nov%2024th/eshalon-on-ubuntu-1.ogv) (right-click and save as, then watch)

If it doesn't work, try this: [http://dl.getdropbox.com/u/84880/Delete%20Nov%2024th/eshalon-on-ubuntu-2.ogv.ogv](http://dl.getdropbox.com/u/84880/Delete%20Nov%2024th/eshalon-on-ubuntu-2.ogv.ogv)

Let me know if you get stuck.

---

### Post by tadcan on 2008-11-12
Thanks for the video, very nice.

When I right click and select open nothing happens. The box appeared in 8.04. There maybe some strange bug/conflict in 8.10 and my machine.

Edit. I installed the .exe version through wine. The launch window appears in the bottom panel. But cant be shown on the screen. Something strange is going on.

---

### Post by Vadi on 2008-11-12
Did you try the second video?

Copy/paste the text from the terminal (right click to copy) here.

---

### Post by tadcan on 2008-11-12
Sorry I thought it was a second link to the same video

Why would I get this?

```
tadcan@Quad:~$ file:///home/tadcan/Desktop/eschalon_book_1/Eschalon_Book_I 
bash: file:///home/tadcan/Desktop/eschalon_book_1/Eschalon_Book_I: No such file or directory
```

---

### Post by Vadi on 2008-11-12
Select "paste filenames", not the "paste" option here

---

### Post by tadcan on 2008-11-13
```
tadcan@Quad:~$ '/home/tadcan/Desktop/eschalon_book_1_demo/eschalon_book_1_demo' /home/tadcan/Desktop/eschalon_book_1_demo/eschalon_book_1_demo: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

---

### Post by Vadi on 2008-11-13
Now at least we know what the issue is.

Here, try clicking on [this]("apt:libstdc++5") to install what I think it needs and try the game again.

---

### Post by tadcan on 2008-11-13
That worked. I can start the game now. When I tried to put the icon of the game in the game menu it would only see .svg. Is there a way to a) get it to see a .png or convert it to a .svg. I tried gimp, but not one of its file types.

---

### Post by Vadi on 2008-11-13
I'm glad that worked. Sorry it took so long to figure out - usually running a program from the terminal is the first thing you'd do to find out what's wrong, because it says in there.

svg to png yes, png to svg quite hard without special tools, I wouldn't even try it. I've asked if they can provide one: [http://basiliskgames.com/forums/viewtopic.php?f=11&t=1975](http://basiliskgames.com/forums/viewtopic.php?f=11&t=1975)

---

### Post by tadcan on 2008-11-13
Thanks, I'll know for net time. Still really new to this linux thing!

---

### Post by Vadi on 2008-11-13
Yep. Feel free to ask if you'll need help.

---

