---
title: "What's the &quot;empty trash&quot; command? (Solved)"
date: 2005-11-13
forum: Desktop Environments
---

### Post by aysiu on 2005-11-13
I love keyboard shortcuts. I have a keyboard shortcut for just about everything I do (I hate using the mouse).

Unfortunately, I can't add an "empty trash" command to Apps > Metacity > Global Keybindings / Keybinding Commands because I don't know what the command is for emptying the trash.

Does anyone know what command does this or how I can find it?

---

### Post by Xian on 2005-11-13
Wouldn't it have to be something along the lines of:

# rm -rf ~/Desktop/Trash/*

???

---

### Post by aysiu on 2005-11-13
[QUOTE=Xian]Wouldn't it have to be something along the lines of:

# rm -rf ~/Desktop/Trash/*

???[/QUOTE] Trash isn't on my desktop. It's in my panel.

**Edit**: I just realized it's in my regular /home folder. Let me see if I can modify the command you gave me.

---

### Post by aysiu on 2005-11-13
Okay.
So the command ```
rm -rf ~/.Trash/*
``` works... from the terminal and from the "Run" dialogue (Alt-F2), but when I try to define it as keyboard shortcut, the shortcut doesn't work. Any ideas?

---

### Post by Xian on 2005-11-13
Being a terminal junkie this is the part where I say, "I'm stumped". :)

---

### Post by aysiu on 2005-11-13
[QUOTE=Xian]Being a terminal junkie this is the part where I say, "I'm stumped". :)[/QUOTE] It's cool. Thanks for the help. I can probably take it from here with a little trial and error now that I at least know what the command is...

---

### Post by anatole on 2005-11-13
sometimes complex commands do not work when defined to keybindings, sessions, etcetera... i never understood why, but here is what should work:
write a script with the command you want to run, make it executable and call the script from where you define the keybindings.

---

### Post by bartc on 2005-11-13
Just a guess, but this might be the reason:

when you type something like "**rm -rf ~/.Trash/***" in you terminal, the terminal interprets the "**~**" and replaces it with the path to your home dir. It then passes the expanded path as an argument to the program **rm**. In short: the terminal interprets "**rm -rf ~/.Trash/***" as: run **rm** with arguments "**-rf /home/bart/.Trash/***" (In my case). 
The keybindings application doesn't seem to know that "**~/.Trash/***" should be translated to "**/home/bart/.Trash/***" and passes "**~/.Trash/***" as an argument to **rm**, which doesn't know how to interpret the **"~"** either.

This also explains why it probably will work when you bind a key to a script which executes the command. The line **"#!/bin/sh"** indicates that this script should be interpreted by the Bourne shell.

So I guess both approuches will work. Either using the full path to your .Trash dir, or using a script.

Correct me if I'm wrong...

---

### Post by aysiu on 2005-11-13
Thanks for people trying to help me out!
I don't know anything about writing scripts.
And I did try using the full path (/home/username/.Trash) instead of ~/.Trash--still no go.

I think I can live without that keyboard shortcut. If there were an easy way, that'd be cool, but if it's too much trouble, I can use the mouse. Thanks again for everyone trying to help.

---

### Post by weblars on 2005-11-13
It is not that hard.
You can create the script i.e. in your home directory.

```
gedit ~/emptytrash.sh
```

Copy&Paste these two lines into your editor and save the file:

```
#!/bin/sh
rm -rf ~/.Trash/*
```

Make the script executable:

```
chmod +x emptytrash.sh
```

The keybinding command should be
```

~/emptytrash.sh
```

---

### Post by aysiu on 2005-11-13
Thank you for the script! Wow. That was easy.
I thought scripts were more complicated than that.
The only thing I had to do to get it to work, though, was to make the keybinding command ```
/home/username/emptytrash.sh
``` For some reason ```
~/emptytrash.sh
``` wasn't recognized properly as a command. Thanks again.

---

### Post by aysiu on 2006-05-07
Okay... reviving a really old thread.

I now mainly use KDE instead of Gnome.

I wrote a script that only sort of works: ```
#!/bin/bash
rm -rf ~/.local/share/Trash/files/*
rm -rf ~/.local/share/Trash/info/*
cp ~/.kde/share/config/trashrc_empty ~/.kde/share/config/trashrc
``` This is after I've already created a *trashrc_empty* file that changes the trash empty full flag to "false."

The problem is that the icon doesn't change to the empty icon after I run it. All the files get emptied, and the trashrc flag changes, but how do I get the icon to change--i.e., have the same behavior as when I click on the trash can and select "empty trash"?

---

### Post by aysiu on 2006-05-09
Any ideas...? Or are people not answering this because it says "solved" and it's still posted in the Gnome section...?

---

### Post by Crashmaxx on 2006-05-15
Well, if after doing that you create a folder and delete it and empty it normally it changes the icon, but I'm not sure if you could incorporate that into a script.

---

### Post by aysiu on 2006-05-15
[QUOTE=Crashmaxx]Well, if after doing that you create a folder and delete it and empty it normally it changes the icon, but I'm not sure if you could incorporate that into a script.[/QUOTE] I'm sorry, but what folder would I create and delete...?

---

### Post by Crashmaxx on 2006-05-16
It doesn't matter, just using it normally clears the icon. Just a blank folder with normal permissions.

But did gnome work right? Cause I made the script and made a launcher next to the trash can and it works great. I prefer it to empty trash because it seems to ignore permissions and that always causes me trouble.

But when I run the scripts in a terminal I have the same problem you do. Go figure.

I'll try it in KDE and see what happens.

---

### Post by aysiu on 2006-05-16
The Gnome "empty trash" command works, and it actually changes the icon from full to empty.

The KDE script is the one I'm having trouble with now...

---

### Post by Crashmaxx on 2006-05-16
I figured out that it looks like trashrc always says [Status] Empty=true, so the last line is doing nothing. Need to figure out how the trash 'knows' its empty.

---

