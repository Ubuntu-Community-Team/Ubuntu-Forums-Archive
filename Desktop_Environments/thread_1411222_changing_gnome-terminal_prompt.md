---
title: "changing gnome-terminal prompt"
date: 2010-02-19
forum: Desktop Environments
---

### Post by twowheels on 2010-02-19
Hi all
Have been trying to change the look of my gnome-terminal prompt what iam looking for is something like
19/02/2010@07;24;40 twowheels-desktop ;~ $
so far i have
07:24:40 twowheels@twowheels-desktop:~$
played around with \%Y in the PS1 with no success keep getting errors on none existing lines 
Exstract from .bashrc
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\T \u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
Thanks

---

### Post by GolemXIV on 2010-02-19
This guide has a lot of good information about configuring the bash prompt. 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html)
> [COLOR=#000000]       When  executing  interactively,  bash displays the primary
       prompt PS1 when it is ready to read  a  command,  and  the
       secondary  prompt PS2 when it needs more input to complete
       a command.  Bash allows these prompt strings  to  be  cus*
       tomized by inserting a number of backslash-escaped special
       characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date  in  "Weekday  Month  Date"  format
                     (e.g., "Tue May 26")
              \e     an ASCII escape character (033)
              \h     the hostname up to the first `.'
              \H     the hostname
              \j     the  number of jobs currently managed by the
                     shell
              \l     the basename of the shell's terminal  device
                     name
              \n     newline
              \r     carriage return
              \s     the  name  of  the shell, the basename of $0
                     (the portion following the final slash)
              \t     the current time in 24-hour HH:MM:SS format
              \T     the current time in 12-hour HH:MM:SS format
              \@     the current time in 12-hour am/pm format
              \u     the username of the current user
              \v     the version of bash (e.g., 2.00)
              \V     the release of bash,  version  +  patchlevel
                     (e.g., 2.00.0)
              \w     the current working directory
              \W     the  basename  of the current working direc*
                     tory
              \!     the history number of this command
              \#     the command number of this command
              \$     if the effective UID is 0, a #, otherwise  a
                     $
              \nnn   the  character  corresponding  to  the octal
                     number nnn
              \\     a backslash
              \[     begin a sequence of non-printing characters,
                     which could be used to embed a terminal con*
                     trol sequence into the prompt
              \]     end a sequence of non-printing characters[/COLOR]

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x690.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x690.html)
> If you don't like the built-ins for date and  time, extracting the same information from the **date** command is  relatively easy.  Examples already seen in this HOWTO include  **date +%H%M**, which will put in the hour in 24 hour format, and the minute.   **date "+%A, %d %B %Y"** will give  something like  "Sunday, 06 June 1999".  For a full list of the interpreted sequences, type **date --help**  or  **man date**.

---

### Post by Hero of Time on 2010-02-20
For some better example than howto text, here's my prompt with date and update:
```
\[\e[0;32m\](\[\e[1;33m\]\u\[\e[1;37m\]@\[\e[0;35m\]\h\[\e[1;37m\] - \[\e[0;33m\]$(date "+%a, %d %b %y, %H:%M") \[\e[1;34m\]Uptime: \[\e[0;32m\])\n
(\[\e[1;37m\]${PWD} \$\[\e[0;32m\])>\[\e[0;00m\]
```
Which results in something like this:
```
(sasquatch@Lain - Sat, 20 Feb 10, 14:02 Uptime: 2h 18m)
(/home/sasquatch $)>
```
Of course, with colours. The part you are interested in, is the date part:
```
$(date "+%a, %d %b %y, %H:%M")
```
Read the man page of date to get the proper output variables.

---

### Post by twowheels on 2010-02-20
Hi 
Thanks for replying and the info will continue tickering with the .bashrc file tonight
Regards
twowheels

---

### Post by gmargo on 2010-02-21
Here's a PS1 string for the format you're looking for, I think (without the chroot stuff):
```

# 19/02/2010@07;24;40 twowheels-desktop ;~ $
PS1="\D{%d/%m/%Y@%H;%M;%S} \h ;\w \$ "

```I like using colors in my prompt, but I don't like dealing with all those escape sequences, so I put the colors in variables, and build the prompt with them, like this:

```

# Ansi terminal colors
cRED="\[\033[31m\]"
cGRN="\[\033[32m\]"
cBRN="\[\033[33m\]"
cBLU="\[\033[34m\]"
cPUR="\[\033[35m\]"
cTUR="\[\033[36m\]"
cGRY="\[\033[37m\]"
cNOM="\[\033[0m\]"

PS1="${cRED}\u@\h \!${cNOM}\$ "

```

---

### Post by Hero of Time on 2010-02-22
If you want all colours available, here's my 'table' with them.
```
      black="\[\e[0;30m\]"
   darkgray="\[\e[1;30m\]"
        red="\[\e[0;31m\]"
   lightred="\[\e[1;31m\]"
      green="\[\e[0;32m\]"
 lightgreen="\[\e[1;32m\]"
      brown="\[\e[0;33m\]"
     yellow="\[\e[1;33m\]"
       blue="\[\e[0;34m\]"
  lightblue="\[\e[1;34m\]"
     purple="\[\e[0;35m\]"
lightpurple="\[\e[1;35m\]"
       cyan="\[\e[0;36m\]"
  lightcyan="\[\e[1;36m\]"
  lightgray="\[\e[0;37m\]"
      white="\[\e[1;37m\]"
     normal="\[\e[0;00m\]"
```

As in the comments in .bashrc about colours, they can distract you, but I, like the one above me, prefer colours. I like them because you can easily spot the start and end of certain output, like dmesg. It's also useful to put a different colour for different users/systems. I have the same prompt on different systems, but with different colours. Root always gets red as warning colour ;).

---

