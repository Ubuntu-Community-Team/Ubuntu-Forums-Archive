---
title: "Terminal overlays non-printing characters onto normal characters"
date: 2012-04-19
forum: Desktop Environments
---

### Post by leo_m on 2012-04-19
I am trying to view a file which contains non-printable characters, those characters are shown in gnome-terminal as hex sequences, but are rendered on top of existing ascii characters, so the ascii characters get hidden beneath these hex sequences.

Is there a way so that the hex characters display beside the ascii characters (i.e. in their own space) instead of partially overlaying on the normal ascii characters?

Other terminal emulators completely omit this non-printable characters from the display/rendering, but that's not what I want.  I want to continue to display the hex sequences, but without affecting the other ascii characters before such non-printable characters in the file.

The profiles and the fonts settings in gnome-terminal did not help.

---

### Post by sudodus on 2012-04-19
How is the output created? Are you reading a file or is it the output from a program, that is running?

If it is a file, you can select various viewers or editors to view it, for example less, nano, gedit, emacs or even a hex editor.

If it is from a program, you might try different terminals. For example xterm, which is very flexible. Read ```
man xterm
```
or if possible, redirect the output to file and read it with a suitable editor.

---

### Post by leo_m on 2012-04-24
> **sudodus said:**
> How is the output created? Are you reading a file or is it the output from a program, that is running?
I am using tail to view a log which gets updated in real-time

> **sudodus said:**
>  If it is a file, you can select various viewers or editors to view it, for example less, nano, gedit, emacs or even a hex editor.
It is a file, but I want to use tail -f so I can see updates happening in real-time - the main purpose is to view live log.  Using less displays ^A character for one of the non-printable characters (and doesn't display the other non-printable character at all, which is hex 01) which is an acceptable workaround for me as it does not overlay the ascii characters with any graphics and also shows these characters in reverse color so they stand out. But I cannot start using tail -f file | less as that doesn't update the display as the log gets updated.  It would still have been nice if someone could tell how to replace the graphics displayed by terminal/ubuntu by default for non-printing characters with some ascii character sequence instead, so I could just use tail -f file instead of having to pipe it through less.  Using tail -f only, the ^A character was not displayed at all, but the hex 01 was displayed as a graphic (or so I think).

---

### Post by sudodus on 2012-04-24
Try

```
tail -f file | sed -n 'l'
```

Description:
In ```
man sed
``` you can find the command 'lower case L'
```
l      List out the current line in a 'visually unambiguous' form.
```

---

### Post by leo_m on 2012-04-25
> **leo_m said:**
> Using less displays ^A character for one of the non-printable characters (and doesn't display the other non-printable character at all, which is hex 01)

Using tail -f file | less displays ^A character for the hex 01, correction to the above.

> But I cannot start using tail -f file | less as that doesn't update the display as the log gets updated.I don't know; sometimes it does, sometimes it doesn't (update the display as the log gets updated); I don't know (can't recollect) what I did that caused it (tail -f file | less) to not update the display atleast once; perhaps it happens after the command is left running for some time, but as I said, don't know definitively.

> tail -f file | sed -n 'l'yep, works.  displays the hex sequence (for hex01 displays \001, albeit not in reverse color).  Thanks.

It would still have been nice if someone could tell how to replace the  graphics displayed by terminal/ubuntu by default for non-printing  characters with some ascii character sequence instead, so I could just  use tail -f file instead of having to pipe it through less or sed (or some other program).

I am prepending [SOLVED] to the title as this now has workaround(s)/acceptable solution(s) though the question of replacing the graphical characters with ascii characters in terminal/ubuntu still remains (for non-printable characters).  I tried Gnome Log Viewer as well, that too shows graphical characters/graphics for non-printable characters, so am suspecting it is a system-wide setting somewhere (or maybe not, but I have no idea where to change this/these setting(s)).

---

