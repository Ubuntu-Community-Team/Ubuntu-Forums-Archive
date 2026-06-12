---
title: "How to run command line tools with parameters through the Applications menu."
date: 2007-06-27
forum: Desktop Environments
---

### Post by lolipop on 2007-06-27
Hi there, ;D

I don't know if I'am in the good section but it seems that it's a Gnome issue so...

I would like to start command line tools through the Applications menu. I use Alacarte and the only thing i can do is to run the programs in gnome-terminal, but after the execution gnome-terminal shuts down itself. :(

I can't give parameters to my command line tool and that's my problem because I really want to keep the entry in the Applications menu.

How could I do what I want to do ?

Thanks in advance. :)

---

### Post by lolipop on 2007-06-28
Up!

---

### Post by AZzKikR on 2007-06-28
> **lolipop said:**
> Up!

Okay, if your parameters are fixed, you can always write a bash script with the command, and then in the menu editor, pointing towards that bash script. I do this for instance for Diablo II:

I created a Bash script called diablo2. I made executable by typing
```
chmod +x diablo2
```

Within that file I just do

```
#!/bin/bash
WINEDEBUG=fixme-all,err-all
wine ~/.wine/drive_c/Program\ Files/Diablo\ II/Diablo\ II.exe -skiptobnet
```

Is this something you are looking for?

---

### Post by lolipop on 2007-06-28
Not exactly. :/

My parameters aren't fixed.

I would like that the user can run "ls" (for instance) and that he's able to add all the options (like "-a" or "-l") he wants after the command.

Edit : And I can't create 1000 bash scripts if I have 1000 parameter possibilities.

---

### Post by AZzKikR on 2007-06-28
> **lolipop said:**
> Edit : And I can't create 1000 bash scripts if I have 1000 parameter possibilities.

Haha, I can quite understand that :) 

I can't tell this for sure, BUT I thought Gnome supplied an application to create an input window for scripting applications. 

For instance, if you want a user to input a value through a Gnome window, you could execute the application gnome-dialog and using command line parameters on that application, display what you want. I don't know if it supports user input, but I do know it can display graphical messages to users. Perhaps it's worth investigating that. 

ps. I do not know if that was the name of the application, I just know something like that exists by default, I just  can't recall the name. I am not at my Ubuntu box atm (at work, using WinXP, bah). I'll search on the net in the meantime.

---

### Post by lolipop on 2007-06-28
> **AZzKikR said:**
> I am not at my Ubuntu box atm (at work, using WinXP, bah).
Erf I know that. I'm in the same case. :/

> **AZzKikR said:**
> I can't tell this for sure, BUT I thought Gnome supplied an application to create an input window for scripting applications. 
Is the result displayed in a terminal ? It seems it's like ALT+F2. The problem is that you must click a second time on the item to run the script one more time. And you can't reuse the parameters of the previous execution ( there's no function like "arrow up" in the terminal ). Or yes ?

My dream would be approximatively that :
I click on the item : a prompt appears with the command ( like >>ls ). I add -a, it shows me the result of "ls -a" and it come back to the prompt with the initial command. Thus I can use another parameter...
It's really strange that Gnome doesn't allow to do that simply. O.o

---

### Post by AZzKikR on 2007-06-28
> **lolipop said:**
> Is the result displayed in a terminal ? It seems it's like ALT+F2. The problem is that you must click a second time on the item to run the script one more time. And you can't reuse the parameters of the previous execution ( there's no function like "arrow up" in the terminal ). Or yes ?

My dream would be approximatively that :
I click on the item : a prompt appears with the command ( like >>ls ). I add -a, it shows me the result of "ls -a" and it come back to the prompt with the initial command. Thus I can use another parameter...
It's really strange that Gnome doesn't allow to do that simply. O.o

Everything is scriptable, whether it is with Python or Bash or [fill in your favorite]. Endless possibilities.

I know it must be programmable to make something like:

[LIST=1]
[*]Show an input box (Python + GTK, Perl + GTK, whatever);
[*]User puts in value;
[*]Script checks the value. If CANCEL was clicked, abort the script;
[*]If a value was entered, and OK was clicked, execute the script with the given parameter;
[*]Go to 1 (using a while loop, or goto:labels or such)
[/LIST]

I could look into it when I am at home (which will be approx. 2,5 hours). Hang in until then :)

ps. You say that it's really strange that Gnome doesn't allow such a functionality simply, but I don't really understand why you want that. Care to give a real example? :)

---

### Post by lolipop on 2007-06-28
> **AZzKikR said:**
> but I don't really understand why you want that. Care to give a real example? :)
For instance I would like the user can run the "mount" command through the Applications menu. Applications >> System tools >> "mount".

Then "mount -h" runs into a term ( to show all the possibilities to the user ) and the prompt returns to the command line to allow the user mounting what he wants.

That, or without running "mount -h", just "prompting" it (The user only has to type "enter" to run it.).

I would like to do that for "mount", "make", etc. I explain with "ls" because it's easier, no ?

I simply think that it's more user-friendly to start this kind of tools through the menu instead of the terminal.

---

### Post by AZzKikR on 2007-07-04
Ok, I think I have found something which might enable you to do what you want. It's called 'zenity' and it's installed by default. It allows you to show custom dialogs (to a certain extent).

Examples are:
```
$ zenity --entry
```

and more customized:

```
$ zenity --entry --title "Mount options" --text "Enter parameters for the mount command:"
```

Type these in  your console and see what it does. The output to the console is actually the value you used as input. With some scripting, what you want can be achieved. Do you want me to look into this further for you?

---

### Post by masam on 2007-07-26
i'm sorta in the same boat, alittle different though.
i'm trying to figure out what would be the best way to(for example) set up an MSDOS batch file using the %1 variable string[only linux style].
i keep looking for code, but i either get "baby steps to the door" or "how to hack your government officials and look k3wl doing it".
i cant seem to find any middle of the fence docs.

from what i can figure(correct me if i'm wrong, still somewhat new to linux), i have to create a script[dvd.sh]
and insert all of my code into that(the process of going from .avi to DVD: idvid; tovid; makexml; dvdauthor; makeisofs.).

i want to type "sudo dvd.sh videoclip.avi" and have it pass "videoclip.avi" to all the mentioned programs.
what do i use to represent videoclip.avi as a variable(or can we do this in C++)?

thanks in advance.

---

