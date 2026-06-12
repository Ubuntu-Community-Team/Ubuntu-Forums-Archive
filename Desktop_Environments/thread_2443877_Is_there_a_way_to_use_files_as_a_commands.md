---
title: "Is there a way to use files as a commands"
date: 2020-05-21
forum: Desktop Environments
---

### Post by explodersname on 2020-05-21
That may sound confusing but what i mean is, well its better to use an example. Say i have a .desktop file in my files application. Is there a way to make it so when i click it, it opens the terminal and types the command gtk-launch path/to/file/app.desktop? I think this would be a really useful feature to have if its not already a thing. Mainly because you could open apps from the desktop using .desktop files. Or you could execute .jar files without annoying scripting. I know you can already do this basically with .sh scripts but i find those annoying to make. Thanks

---

### Post by TheFu on 2020-05-21
Without knowing the specific file manager, we can't answer.  Each has different behaviors.  Many allow running scripts directly.  

Script files are lists of commands, in order like any other programming language.  On all Unix systems, files have "permissions."  Part of those permissions are the execute bits.  There are bits to all allow the file owner to run it, members of the group for the files to run it, and for others (not members of the group or the owner) to run it. These can be enabled or disabled separately.

These are not specific to ".desktop" files, which are meta-data more similar to the old Windows 3.0 .pif files.

Scripts can be written in any scripting language supported/installed on the system.  Python, bash, sh, zsh, fish, perl, awk, sed, ruby, whatever. There must be 100 other languages.

[https://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/](https://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/)
[https://www.tldp.org/LDP/Bash-Beginners-Guide/html/](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/)

Any commands that you can type into a shell/terminal, can be used in a script. It is best NOT to use GUI tools in a script, but using a script to setup conditions before calling a GUI tool is extremely common.  Firefox starts this way, for example.

Feel free to ask questions about a specific script.  Just be certain to post that you have - even psuedo-code is fine.  When I'm creating a script, I usually begin by writing comments for each step, then go back and fill in the code later. Often, each comment becomes a function/subroutine.  But really simple scripts of just 1 - 5 lines usually don't need that.

I have **caja**, a file manager, on a computer here.  Double-clicking on a script with execute permissions opens it inside an editor, vim, with about the ugliest color scheme I've ever seen.  Must admit, this is the first time I've tried that in about 15 yrs.  

However, by right-clicking on the file, I was able to set an action for all "shell script" files in the future.  I told it to run **bash**.  From that point on, double-clicking on the file ran bash and passed the script into it.  Tried it with a few other scripts and they worked as expected.  The vast majority of my scripts require arguments on the command line, so dlb-click isn't really viable for about 98% of my scripts.  Plus many will not be written in other scripting languages.

You can have a .desktop file point at a script, if you like too.

---

### Post by lvm on 2020-05-21
First of all, gtk-launch wouldn't be of much help here as it starts .desktop files from a single location /usr/share/applications, not from an arbitrary path. In KDE you can associate "kioclient exec <file>" with .desktop extension in your file manager e.g. in mc you will have to add

```
regex/\.desktop$
        Open=kioclient exec %f >/dev/null 2>&1 &
```

to extension file. In other desktop environments you will probably have to resort to scripting you don't like so much to parse the .desktop file and start the program specified in the Exec line. But then linux is for people who like scripting and hate clicking.

---

### Post by CatKiller on 2020-05-21
I'm really struggling to see what you're trying to achieve. Perhaps you could clarify? 

> **explodersname said:**
> Mainly because you could open apps from the desktop using .desktop files.

That's what .desktop files *do*.

For the specific case of Gnome and the desktop, they *removed* that function because the Gnome devs don't like icons on the desktop. If you use a different desktop environment, or use a different file manager than the default to handle the desktop on Gnome, .desktop files will do what .desktop files do.

---

