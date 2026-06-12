---
title: "working directory in bash $PS1 too long"
date: 2008-12-27
forum: General Help
---

### Post by monocalvo on 2008-12-27
I'm getting started in programming and scripting on my dual boot. One of the things I would like to change is the fact that my prompt gets too long when working with stuff in windows, for example:
monocalvo@UbuntuBox:/media/WindowsBox/Documents and Settings/monocalvo/My Documents/scripts$
As you can see, it gets a bit irritating working with that long of a prompt. how can I change it to the current directory, not the full directory? I'm assuming I need to alter the $PS1 variable in .bashrc, but I don't know what to change \w to. My current $PS1 is: ${debian_chroot:+($debian_chroot)}\u@\h:\w\$

I am using the latest version (as far as I know) of GNOME bash, 2.24.1.1

Thanks

---

### Post by wootah on 2008-12-27
> **monocalvo said:**
> I'm getting started in programming and scripting on my dual boot. One of the things I would like to change is the fact that my prompt gets too long when working with stuff in windows, for example:
monocalvo@UbuntuBox:/media/WindowsBox/Documents and Settings/monocalvo/My Documents/scripts$
As you can see, it gets a bit irritating working with that long of a prompt. how can I change it to the current directory, not the full directory? I'm assuming I need to alter the $PS1 variable in .bashrc, but I don't know what to change \w to. My current $PS1 is: ${debian_chroot:+($debian_chroot)}\u@\h:\w\$

I am using the latest version (as far as I know) of GNOME bash, 2.24.1.1

Thanks
Hey there!

Yup, you need to edit ~/.bashrc and look for the line that sets $PS1. What you can do is man bash    then press / and type PROMPTING <enter> and press n until you reach the prompting section. This details everything you need to know and because I'm a nice dood :D here's the list:

> PROMPTING
       When executing interactively, bash displays the primary prompt PS1 when
       it  is  ready  to  read a command, and the secondary prompt PS2 when it
       needs more input to complete  a  command.   Bash  allows  these  prompt
       strings  to  be  customized  by inserting a number of backslash-escaped
       special characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date in "Weekday Month Date" format (e.g.,  "Tue  May
                     26")
              \D{format}
                     the  format  is  passed  to strftime(3) and the result is
                     inserted into the prompt string; an empty format  results
                     in a locale-specific time representation.  The braces are
                     required
              \e     an ASCII escape character (033)
              \h     the hostname up to the first &#8216;.&#8217;
              \H     the hostname
              \j     the number of jobs currently managed by the shell
              \l     the basename of the shell&#8217;s terminal device name
              \n     newline
              \r     carriage return
              \s     the name of the shell, the basename of  $0  (the  portion
                     following the final slash)
              \t     the current time in 24-hour HH:MM:SS format
              \T     the current time in 12-hour HH:MM:SS format
              \@     the current time in 12-hour am/pm format
              \A     the current time in 24-hour HH:MM format
              \u     the username of the current user
              \v     the version of bash (e.g., 2.00)
              \V     the release of bash, version + patch level (e.g., 2.00.0)
              \w     the current working  directory,  with  $HOME  abbreviated
                     with a tilde
              \W     the basename of the current working directory, with $HOME
                     abbreviated with a tilde
              \!     the history number of this command
              \#     the command number of this command
              \$     if the effective UID is 0, a #, otherwise a $
              \nnn   the character corresponding to the octal number nnn
              \\     a backslash
              \[     begin a sequence of non-printing characters, which  could
                     be  used  to  embed  a terminal control sequence into the
                     prompt
              \]     end a sequence of non-printing characters

       The command number and the history number are  usually  different:  the
       history  number of a command is its position in the history list, which
       may include commands  restored  from  the  history  file  (see  HISTORY
       below),  while  the  command  number is the position in the sequence of
       commands executed during the current shell session.  After  the  string
       is  decoded,  it is expanded via parameter expansion, command substitu&#8208;
       tion, arithmetic expansion, and quote removal, subject to the value  of
       the  promptvars  shell option (see the description of the shopt command
       under SHELL BUILTIN COMMANDS below).
Maybe try \W ?

EDIT: If I understand correctly, \W is what you are looking for (just the current directory). You'll need to close your terminal window, or logout/log-back-in if you are in VT.

---

### Post by dagnabit dang doohickey on 2008-12-27
Capitalize the "w" in your current PS1 string.

Another option is a symlink:
```
ln -s "/media/WindowsBox/Documents and Settings/monocalvo/My Documents" "~/WinDocs"
```

---

### Post by lswb on 2008-12-27
Check man bash and scroll down to the section entitled "PROMPTING"

I believe changing '\w' to '\W' will give the effect you want.

---

### Post by snova on 2008-12-27
> **monocalvo said:**
> how can I change it to the current directory, not the full directory? I'm assuming I need to alter the $PS1 variable in .bashrc, but I don't know what to change \w to. My current $PS1 is: ${debian_chroot:+($debian_chroot)}\u@\h:\w\$

Good guess. Yes, PS1 controls the prompt.

Unfortunately, \W does nothing more than replace /home/<user> with ~, similar to how ~ is replaced with /home/<user> when navigating the filesystem. But you aren't in your home directory, so there's nothing to collapse.

> I am using the latest version (as far as I know) of GNOME bash, 2.24.1.1

*Gnome* Bash? I've never heard of such a thing! :P

(Incidentally, that's the Gnome version number, not Bash's.)

---

### Post by monocalvo on 2008-12-27
That did it. Thank you for your help, I learned my lesson- check the man pages again.

---

### Post by RealPSL on 2008-12-28
Try ```
PS1="[\u@\h \W]\\$ "
```

---

