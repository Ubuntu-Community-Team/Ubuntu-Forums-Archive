---
title: "Path Issues"
date: 2011-07-20
forum: Desktop Environments
---

### Post by mastahyeti on 2011-07-20
I have a number of programs that I would like to be able to run via either gnome-do or <alt>+F2 run dialog. I am keeping these programs in ~/.bin and I went into my bashrc file and added this location to my path and even after restarting the computer gnome-do and the run dialog are not picking up on this path. It is working fine from the terminal, so I know I didn't actually mess up the path. Is there some place else where I need to add this path for this to work? Thanks!

---

### Post by AlphaLexman on 2011-07-20
Normally users put their programs in ~/bin NOT ~/[COLOR="Red"]**.**[/COLOR]bin
Not that it makes a difference, just double-check your ~/.bashrc to make sure your $PATH matches.
```
echo $PATH
```

---

### Post by enimeizoo on 2011-07-20
Not sure about gnome, but in kde, krunner doesn't use the same env variables, not sure if it is because it overwrites it when launched, or something.

Maybe try to run in the run dialog. 
```
echo $PATH > output.txt
```And see what path is used.

---

### Post by mastahyeti on 2011-07-20
Here is the my path in gnome-terminal:

btoews@btoews01:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:~/.bin

interestingly though, entering "echo $PATH > /home/username/output" didn't create a file... It must be something about how the run dialog actually runs commands. It must launch binaries rather than actually running shell commands.

Still no solution. Any further ideas?

---

### Post by AlphaLexman on 2011-07-20
Is there a 'Run in terminal' radio button in the run dialog box?
If so, activate it, if not try running a shell before your program...
```
sh /home/username/.bin/foo
```

---

### Post by mastahyeti on 2011-07-20
I tried the "run in terminal" button and it also didn't work. As for the sh idea, it does work if I give the whole path like that, but I was hoping to be able to just type the name of the program.

---

### Post by AlphaLexman on 2011-07-20
Is (Are) the program(s) compiled binaries, or shell scripts??

If you type in enough unique characters does the 'run dialog' finish the program_name for you??

---

### Post by mastahyeti on 2011-07-20
The one I am testing with right now is a symbolic link to a binary. it doesn't autocomplete

---

### Post by AlphaLexman on 2011-07-20
Why not just put the actual path to the binary in your $PATH variable instead of linking to it in ~/.bin ??

The run dialog would then perform as expected.

---

### Post by mastahyeti on 2011-07-20
because it would screw up my relative paths if I moved the bin. Right now, I have things laid out like this:

~/.bin/myapp/myapp                     = Actual binary
~/.bin/myapp/myapp.cfg                 = config file or whatever
~/.bin/myapp/lib/foo                   = some library or other file needed by binary
~/.bin/myapp => ~/.bin/myapp/myapp     = symlink to binary that is on $PATH

This way I don't need to add each sub directory to $path . Does that make sense?

---

### Post by wojox on 2011-07-20
How many bin directories do you have in $HOME?

Does the end of .bashrc look like this:

```
if [ -d "$HOME/bin" ] ; then
  PATH="$PATH:$HOME/bin"
fi

```

That keeps it persistent through out reboots.

---

### Post by AlphaLexman on 2011-07-20
> **mastahyeti said:**
> Does that make sense?
Well... 
NO.

Config files and library files do **NOT** need to be in the $PATH variable.

Besides, your $PATH variable could be a thousand characters long, and the command interpreter would give up after the first one found.

---

