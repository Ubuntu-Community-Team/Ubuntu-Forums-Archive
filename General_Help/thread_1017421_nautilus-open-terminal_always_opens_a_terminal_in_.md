---
title: "nautilus-open-terminal always opens a terminal in the home directory"
date: 2008-12-21
forum: General Help
---

### Post by cyberslayer on 2008-12-21
Hello,

I've just installed 8.10 and nautilus-open-terminal does not seem to work properly.  Regardless of which folder it is run from, it always opens a terminal in the home directory.  I am using gnome but I have changed the default terminal to konsole.  This problem does not seem to occur when the default terminal is gnome-terminal.  Anyone know how to fix this?

Thanks

---

### Post by mc4man on 2008-12-21
With out being 100% sure, logically nautilus-open-terminal is a nautilus extension that opens a dir. at its prompt in a gnome terminal.
So I guess it wouldn't be surprising if it didn't work with a konsole terminal

---

### Post by cyberslayer on 2008-12-21
Well I had it working with konsole without doing anything special in 8.04 (and other older versions).  8.10 is the only version I have tried it with that does not work.  It works with at least 8.04 and 7.10 although I am not sure about versions earlier than 7.10.

Thanks

---

### Post by oldos2er on 2008-12-21
> **cyberslayer said:**
> Hello,

I've just installed 8.10 and nautilus-open-terminal does not seem to work properly.  Regardless of which folder it is run from, it always opens a terminal in the home directory.  I am using gnome but I have changed the default terminal to konsole.  This problem does not seem to occur when the default terminal is gnome-terminal.  Anyone know how to fix this?

Thanks

 You probably need to use gconf-editor to somehow change settings from gnome-terminal to konsole--or go back to using gnome-terminal.

---

### Post by cyberslayer on 2008-12-21
I tried that but the only option under nautilus-open-terminal is desktop_opens_home_dir which does something else.

Thanks

---

### Post by dcstar on 2008-12-22
> **cyberslayer said:**
> Well I had it working with konsole without doing anything special in 8.04 (and other older versions).  8.10 is the only version I have tried it with that does not work.  It works with at least 8.04 and 7.10 although I am not sure about versions earlier than 7.10.


Then it is a konsole issue not accepting the directory information.

The Gnome version in each Ubuntu version is different, and there is no guarantee that "foreign" utilities like konsole are updated to work with the newer Gnomes.

---

### Post by necro351 on 2010-05-13
DISCLAIMER: I know this thread is old, but if I solve the related problem, I reply to threads that I find on Google as someone else may find it when doing a similar search.

So Ubuntu's Open Terminal command in nautilus is actually using the -x option in gnome-terminal.  If you go to

System->Preferences->Preferred Applications then click the 'System' tab you will see a 'default' Terminal application.  If you are _not_ using gnome-terminal (for instance I use xterm) then you need to set this to custom, pick your terminal program, and specify the correct 'execute' flag.

In xterm this is -e, in gnome-terminal this is -x.

Furthermore if your 'terminal' is actually a script (as in my case, since default xterm is unusable) then you need to be careful about how you pass arguments to your terminal program, as the script will strip off the '"' characters.  Here is my 'terminal' script:

```

#!/bin/bash

exec xterm -fa "Bitstream Vera Sans Mono" -rv -cr white +sb -fs 11 "$@"

```

The "$@" is supposed to be quoted, and tells bash 'leave the remaining arguments alone, do not interpret anything, leave each word as it was passed in with '"'s and all'.

Now the 'System' tab has two settings I am interested in, the terminal program, and the execute flag:

Command:

```

/home/rick/.xterm-exec

```

Execute flag:

```

-e

```

Now if I hit my keyboard shortcut for my terminal, it pops up in '~', and if I right-click a directory in nautilus and hit 'Open Terminal' it passes in the flags to -e that open the terminal in that directory.  If you are curious, or are debugging, the actual string that is passed in by 'Open Terminal' to the -e/-x flag is:

```

<program> <exec-flag> /bin/sh -c cd '<cwd>' && exec $SHELL -l

```

If you are using Konsole, find its execute flag, and you should be fine, otherwise if you are using a script, you can do what I did.

---

