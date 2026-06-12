---
title: "ls command help.  one screen at a time?"
date: 2009-05-24
forum: General Help
---

### Post by helstreak on 2009-05-24
when i use the ls command it just spits everything out at once and just shows me the last of the file.  is there anyway i can have it return just one screen at a time?

thanks :)

---

### Post by asmoore82 on 2009-05-24
The Spirit of UNIX is small tools that accomplish simple tasks very effectively.
Then, you combine the tools in your own ways to accomplish more complex tasks.

On the CLI, this is done through "Pipeline Commands" using the ``|'' pipe character - Shift+Backslash on most keyboards.

To break down ls output into screens, **pipe** its output to the `more` utility:
```
ls | more
```
in `more` use the spacebar to show the next screen and ``q'' to quit

Even better for most purposes, pipe to the `less` utility for interactive text scolling:
```
ls | less
```
in `less` use up and down arrows to scroll, page up and page down keys to scroll whole screens, and ``q'' to quit.

---

### Post by helstreak on 2009-05-24
> **asmoore82 said:**
> The Spirit of UNIX is small tools that accomplish simple tasks very effectively.
Then, you combine the tools in your own ways to accomplish more complex tasks.

On the CLI, this is done through "Pipeline Commands" using the ``|'' pipe character - Shift+Backslash on most keyboards.

To break down ls output into screens, **pipe** its output to the `more` utility:
```
ls | more
```
in `more` use the spacebar to show the next screen and ``q'' to quit

Even better for most purposes, pipe to the `less` utility for interactive text scolling:
```
ls | less
```
in `less` use up and down arrows to scroll, page up and page down keys to scroll whole screens, and ``q'' to quit.

thank you so much, i've been trying to figure out how to do this for a couple months hehehe :)

---

### Post by helstreak on 2009-05-24
> **asmoore82 said:**
> The Spirit of UNIX is small tools that accomplish simple tasks very effectively.
Then, you combine the tools in your own ways to accomplish more complex tasks.

On the CLI, this is done through "Pipeline Commands" using the ``|'' pipe character - Shift+Backslash on most keyboards.

To break down ls output into screens, **pipe** its output to the `more` utility:
```
ls | more
```
in `more` use the spacebar to show the next screen and ``q'' to quit

Even better for most purposes, pipe to the `less` utility for interactive text scolling:
```
ls | less
```
in `less` use up and down arrows to scroll, page up and page down keys to scroll whole screens, and ``q'' to quit.

thank you so much, i've been trying to figure out how to do this for a couple months hehehe :)

is there a way to color code files and such?  thanks again :) :)

---

### Post by asmoore82 on 2009-05-24
```
ls --color=auto
```
you can make this permanent by adding an alias to your ~/.bashrc
```
alias ls='ls --color=auto'
```

---

