---
title: "Window Manager Replacement Script"
date: 2009-07-07
forum: Desktop Environments
---

### Post by finch127 on 2009-07-07
So everyone, this is my first "howto" sort of post, and I have what I hope is a potentially useful script that I want to share. 

[COLOR="Red"]WHO NEEDS THIS SCRIPT:[/COLOR]
Basically, when I first switched to Ubuntu from Windows, I was always trying to get a higher framerate in games, and I noticed with a simple GLX Gears test that Metacity had a much higher result than Compiz. So, I wrote a script that simply takes a command you want to run (EG, a game program like vegastrike) and switches to Metacity and then when the game exits, it switches back to Compiz. This script can be edited to use your window managers of choice, or, if someone wants to help me, they can find a way to automatically detect the window managers and act accordingly but this is complicated and useless in my opinion. Basically, if you want metacity's higher framerates but dont want to do this:

```

user@whatever:~# metacity --replace

user@whatever:~# programname

user@whatever:~# compiz --replace

```

Then this script is a good idea.

[COLOR="Red"]HOW TO "INSTALL" THIS SCRIPT:[/COLOR]

For all you more advanced people, the basic process is to download the text file, make it executable, and move it to somewhere in your $PATH to make it convenient. You don't have to but I personally like it that way.

For all of you beginners out there, just download the file attached. Name the text file wmswitch (I would take off the .sh at the end) or you can feel free to name it anything you like and save it to your Desktop (I am assuming you named it wmswitch). Then, open a terminal by using Alt+F2 and typing "gnome-terminal" without the quotes. Then do this:

```
sudo -s
```

Enter your password to become root

```
chmod +x wmswitch
```

To make it executable

```
mv wmswitch /usr/bin/wmswitch
```

To make it easy to run the file

Finally, exit the terminal. Then from now on, all you have to do is start a terminal and type wmswitch to run the script.

[COLOR="Red"]USING THE SCRIPT:[/COLOR]

It's fairly simple. It first asks you for the program you want to run, and you dont need exact paths (if you don't know what a path is don't worry). For example I want to run Vegastrike so all I do is type "vegastrike" without the quotes when it asks. Then the script does a simple test to see if the program you typed actually exists. If it does it switches WMs and runs the program. If it doesn't, the script restarts. It's that simple.

Also, if you care to put this in a Desktop Shortcut or whatever, just type wmswitch -p "program name" (without the quotes) in the line that asks for command. This was recently added and is not available in older (pre 1.0) versions of the script

[COLOR="Red"]THE SCRIPT IS NOW ATTACHED![/COLOR]

UPDATE: Because the script is getting very large, I have decided to attach it as a text file for you to chmod +x blah blah blah, as I had described earlier. Also, I updated some bugs and added a few features like the Metacity test and also the -p flag for shortcut usage as well as some cosmetic/readability improvements.

POSSIBLE BUGS: 

1. If you want to run a program that is not in your $PATH this will not work so you need to either put the program in your $PATH or forget the script and do it manually.

2. Compiz and Metacity like to pony out and just stop working sometimes, but that is not the scripts fault. If you find that you are still in Metacity after you run your program, you will have to manually replace.

Happy Gaming/Whatever!

---XIII

---

### Post by jpeddicord on 2009-07-11
Moved to Desktop Environments, since this is a script and not so much a tutorial.

Jacob

---

### Post by finch127 on 2009-07-13
Oh, alright, I had problems deciding where this should go anyway! Thank you.

---

### Post by finch127 on 2009-07-21
Well I feel like an idiot:

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Looks like a much better way of doing this was already developed by someone else!

---

