---
title: "Terminal - Getting autocomplete to work with aliased program names"
date: 2009-06-12
forum: General Help
---

### Post by Lyuokdea on 2009-06-12
Hi All,

So I'm starting to use gvim more, however, due to laziness, i have it aliased as gv in .bashrc (i know that's also another program, but i don't use it).... However, when i type in gv, the terminal automatically stops allowing me to use tab to autocomplete the file I want to open (assumably because it doesn't know what gv can do with any files that I have)

How do you set up autocomplete to work regardless of how sensible the terminal thinks the command is?

Thanks,

~Lyuokdea

---

### Post by jonobr on 2009-06-12
Hello

I have not used GVIM
However, Just to clarify,

GVIM runs ok after the alias and GVIM should be doing an autocomplete?

IF that's right, then it doesn't sound like an alias issue, it sounds like an application one?

in regular vi, theres no autocomplete function AFAIK...

---

### Post by jenkinbr on 2009-06-12
> **jonobr said:**
> Hello

I have not used GVIM
However, Just to clarify,

GVIM runs ok after the alias and GVIM should be doing an autocomplete?

IF that's right, then it doesn't sound like an alias issue, it sounds like an application one?

in regular vi, theres no autocomplete function AFAIK...
No, this is an alias issue

I have added the following to my .bashrc file:

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias install='sudo apt-get install'

All these aliases work fine, but using tab-compleation does not work.

---

### Post by jonobr on 2009-06-12
Hi jenkinbr

Just a biit confused,

When you alias into GVIM, the app runs and then autocomplete in the app does not work?

Does that mean that GVIM opens with some of your profile settings which stop autocompete to work, or do I have this backways?

---

### Post by jenkinbr on 2009-06-12
No, we're saying that specifying a command option or file name on the command-line doesn't work IF the program is aliased.

I was quoting a completly different example to confirm that the issue is with the aliases and not gvim.

We're talking about terminal tab compleation, not vim (or gvim) tab-completion.

---

### Post by Lyuokdea on 2009-06-12
Right....like what jenkinbr said...

gvim works perfectly, this is a problem with the terminal.

When i'm in the terminal and i want to load some (usually rather length output data file name)....i'll want to use autocomplete to save time on typing the filename.

This works fine if the first thing i type in is "gvim" or "vim" or any other registered program

but when the first thing typed in is gv (the alias for gvim), it doesn't know that this is a program that can open files, so it refuses to autocomplete files that I might want to open, which is quite annoying to me.

Thanks in advance for any help you can give,

~Lyuokdea

---

### Post by jenkinbr on 2009-06-12
I just tryed creating a symlink in my private ~/bin directory
```
ln -s /usr/bin/gvim ~/bin/gv
```

but tab-compleate still doesn't work.

---

### Post by jonobr on 2009-06-12
Gotcha,

Thanks for the clarification folks..

---

### Post by benj1 on 2009-06-12
just get rid of gv, then when you type gv it will expand to gvim, simple

---

### Post by jenkinbr on 2009-06-12
> **benj1 said:**
> just get rid of gv, then when you type gv it will expand to gvim, simple
No it wont, because of all the gvfs stuff.

---

### Post by maheshasolkar on 2009-06-12
Tab completion in bash is governed by /etc/bash_completion. Looking at that file, 'gv' (ghostview) will only complete files that match this pattern:

```
  '!*.@(@(?(e)ps|?(E)PS|pdf|PDF)?(.gz|.GZ|.bz2|.BZ2|.Z))'
```

i.e., printables and archives.

You can edit /etc/bash_completion to match completion rules for gv to match those of gvim - or move 'gv' from ghostview line to gvim line.

---

### Post by benj1 on 2009-06-12
> **jenkinbr said:**
> No it wont, because of all the gvfs stuff.

no youre right, what i meant if you remove gv, then the alias gv for gvim will work normaly, because there isn't a name conflict.

EDIT: if you alias gv to something else with a slash before hand ie alias notgv='\gv' that should avoid problems aswell

---

### Post by jenkinbr on 2009-06-12
> **maheshasolkar said:**
> Tab completion in bash is governed by /etc/bash_completion. Looking at that file, 'gv' (ghostview) will only complete files that match this pattern:

```
  '!*.@(@(?(e)ps|?(E)PS|pdf|PDF)?(.gz|.GZ|.bz2|.BZ2|.Z))'
```

i.e., printables and archives.

You can edit /etc/bash_completion to match completion rules for gv to match those of gvim - or move 'gv' from ghostview line to gvim line.
thanks

Oh my, that file is rather scary...

---

