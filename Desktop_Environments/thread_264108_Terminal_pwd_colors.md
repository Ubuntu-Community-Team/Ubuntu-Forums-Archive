---
title: "Terminal pwd colors"
date: 2006-09-24
forum: Desktop Environments
---

### Post by MdaG on 2006-09-24
How do I set colors to my gnome-terminal? I mean the path colors
```
user@user-laptop:~/school/exjobb$ ./main.py <- THIS LINE
Read from file: 64511 samples, 1.33 seconds
Remove sequential duplicates: 61979 samples, 0.23 seconds
Remove saccade movements: 61711 samples, 0.15 seconds
Remove all duplicates: 13431 samples, 0.95 seconds
Finding mean in clusters 5.15 seconds
Rotate data onto axises 0.06 seconds
Calibration took a total of 7.87 seconds
user@user-laptop:~/school/exjobb$ <- THIS LINE
```
I want the lines marked "<- THIS LINE" to have a separate color like green or red or something like that. I want the rest to be white on black background. I know how to do this in an Aterm, but I want to try and only use the GNOME-apps and set them to my liking.

---

### Post by henriquemaia on 2006-09-24
First of all, you have to set the colour scheme in gnome terminal, to put it  white on black. Just follow these steps:

1: open gnome-terminal
2: go to Edit > Profiles
3: you should see there's one there, the default. You can create a new one or edit that. I chose to edit that. Select it and press Edit (on the right of that window)
4: go to the Colors tab
5: on Built-in schemes, choose White on black (or whatever you like best)

Close everything. Now you have the terminal with the look you want.

Now, as to the colours of the path. You have to edit your .bashrc file.

Do:

```
gedit ~/.bashrc
```

On the opened file, check for:

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

Uncomment the second line. Save the file and in order to test it, open a new terminal session (by pressing ctrl+shift+t on gnome-terminal). You'll see the new colours on your prompt. You can change them to whatever you like if you edit that second line. You just have to search for a tutorial on how to use colours on the prompt in order to understand the colours codes.

---

### Post by MdaG on 2006-09-25
Sweet! Thanks :-)

---

### Post by andiii on 2006-09-26
```

PROMPT_COMMAND='PS1="\[\e[1;32m\]\u\[\e[0;31m\]@\h:\[\e[1;34m\]\w\[\e[0;32m\]\
\`if [ $? -ne 0 ]; then echo -n \"\[\e[1;31m\]:(\"; else echo -n \"\[\e[1;32m\]\
:)\"; fi\`\[\e[0;33m\]$ \[\e[0m\]"'

```

Try this.. it adds a Smiley face at the end. A happy smiley when exit 0, sad smiley when some error occured. Funny AND useful.

---

