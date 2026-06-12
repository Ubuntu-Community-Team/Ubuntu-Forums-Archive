---
title: "Customize the Command Line? (Add Current Time)"
date: 2009-06-17
forum: General Help
---

### Post by aphexcoil on 2009-06-17
Currently, I am using Ubuntu through an SSH connection.  I am sitting in the logs folder, so the prompt currently looks like this:

someuser@somecomputer /var/log $

I am curious if it is possible to customize the command line to include the current date, the current time or both.

For instance:

someuser@somecomputer 15:09:50 /var/log $  *OR*

15:09:50 someuser@somecomputer /var/log $ 

I am doing a lot of work with cron testing and would like to see the time.

Thank you in advance for any help you can give!

---

### Post by Cheesemill on 2009-06-17
You can customize pretty much anything you want in your bash prompt, takek a look here for a complete run-down:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
You basically have to edit the PS1 variable in your ~/.bashrc file, I've not played with it much myself but I think you would have to add[FONT=monospace]
[/FONT]```
\t
```where you want the time to appear.

I'm sure someone more knowledgeable can give you the exact location :)

---

### Post by geirha on 2009-06-17
You can add a command to your prompt, but it will only be run each time the prompt is drawn, but hitting enter to draw a new prompt, rather than "date<enter>" is probably an improvement.

```
PS1='$(date +%H:%M:%S) \u@\h \w \$ '
```

EDIT: Ah, yes. as Cheesemill suggested, \t does the same as the $(date...), so
```
PS1='\t \u@\h \w \$ '
```

---

### Post by jonobr on 2009-06-17
Removing my comment as the guys beat me to it

Just to remind make a backup of .bashrc  before modyfing

---

### Post by unutbu on 2009-06-17
Edit your ~/.bashrc. Search for "[ "$color_prompt" = yes ]" and add "\t" in two places so the code looks like the following:

```
if [ "$color_prompt" = yes ]; then
    PS1='**\t **${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='**\t **${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

---

### Post by aphexcoil on 2009-06-17
> **Cheesemill said:**
> You can customize pretty much anything you want in your bash prompt, takek a look here for a complete run-down:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
You basically have to edit the PS1 variable in your ~/.bashrc file, I've not played with it much myself but I think you would have to add[FONT=monospace]
[/FONT]```
\t
```where you want the time to appear.

I'm sure someone more knowledgeable can give you the exact location :)

Thanks to everyone who replied.  The /t suggestion worked like a charm.  I just set the PS1 variable from the prompt since I didn't want to make the changes permanent.  

Just for further reference for everyone else who would like to customize the command line and to add to the great advice in this thread, here is a cheat-sheet.


[LIST]
[*]**\a** :     an ASCII bell character (07)
[*]**\d** :     the date in "Weekday Month Date" format (e.g., "Tue May 26")
[*]**\D{format}** : the format is passed to strftime(3) and the result is inserted into the prompt string; an empty format results in a locale-specific time representation. The braces are required
[*]**\e** :     an ASCII escape character (033)
[*]**\h** :     the hostname up to the first '.'
[*]**\H** :     the hostname
[*]**\j** :     the number of jobs currently managed by the shell
[*]**\l** :     the basename of the shell’s terminal device name
[*]**\n** :     newline
[*]**\r** :     carriage return
[*]**\s** :     the name of the shell, the basename of $0 (the portion following the final slash)
[*]**\t** :     the current time in 24-hour HH:MM:SS format
[*]**\T** :     the current time in 12-hour HH:MM:SS format
[*]**\@** :     the current time in 12-hour am/pm format
[*]**\A** :     the current time in 24-hour HH:MM format
[*]**\u** :     the username of the current user
[*]**\v** :     the version of bash (e.g., 2.00)
[*]**\V** :     the release of bash, version + patch level (e.g., 2.00.0)
[*]**\w** :     the current working directory, with $HOME abbreviated with a tilde
[*]**\W** :     the basename of the current working directory, with $HOME abbreviated with a tilde
[*]**\!** :     the history number of this command
[*]**\#** :     the command number of this command
[*]**\$** :     if the effective UID is 0, a #, otherwise a $
[*]**\nnn** :   the character corresponding to the octal number nnn
[*]**\\** :     a backslash
[*]**\[** :     begin a sequence of non-printing characters, which could be used to embed a terminal control sequence into the prompt
[*]**\]** :     end a sequence of non-printing characters
[/LIST]

To view the current parameters of your command line type the following at the command line prompt:

echo $PS1

This will return something similar to:

[B]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\]
[/B]
To put the time in front of everything, slip a \T into this variable by placing the following at a prompt:

[B]PS1 = "_\T_ ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\]"
[/B]
The underlined part is where I made the change.  This results in my prompt now looking like:

**04:30:31 jason@supercomLINUX ~ $**

Sweet!  :D

---

