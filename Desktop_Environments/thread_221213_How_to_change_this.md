---
title: "How to change this?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Hoffmann on 2006-07-22
Hello,

By mistake I got a brown backround on every single "alias" word of my .bashrc file. I mean, the backround is JUST on that word (ALIAS). :confused: How can I get this back to normal?

Thanks

---

### Post by taurus on 2006-07-22
If you edited ~/.bashrc, then you need to look in ~/.bashrc to see what you did wrong.  Otherwise, post it here and somebody will spot it for you!

---

### Post by ardchoille on 2006-07-22
If you did a search for the word "alias" in ~/.bashrc, then that word will have a different background to show you the highlighted instances of the search. You can always close the document, then click on File and choose it or open it again from File -> Open, then the highlight should be gone.

---

### Post by Hoffmann on 2006-07-22
In the previous post, I forgot to say that the problem occurs just when I read the .bashrc with vi editor. So, it seems like my program is related to vi. 
Any idea about removing that brown HIGHLIGHT on the word 'alias' on my .bashrc file?
Thanks, once again.

---

### Post by jayemef on 2006-07-22
What editor are you using? This sounds like a Vi symptom, which can be fixed by either using the command **set nohlsearch** while in command mode, or adding it to your ~/.vimrc:
```
set nohlsearch
```

---

### Post by scxtt on 2006-07-22
just search for some non-existant word when in vi, like:

/floccinaucinihilipilification

---

### Post by Hoffmann on 2006-07-22
> **jayemef said:**
> What editor are you using? This sounds like a Vi symptom, which can be fixed by either using the command **set nohlsearch** while in command mode, or adding it to your ~/.vimrc:
```
set nohlsearch
```

Hi jayemef,

Your suggestion worked.

Thanks!
Hoffmann

---

### Post by scxtt on 2006-07-22
yeah it works, but no highlighting on search will be visible in vi - why disable a feature like that?

---

### Post by jayemef on 2006-07-22
Because **set incsearch** compliments it. With both set, Vi will do highlighting as you type your search, as well as jump directly to the first instance.

---

### Post by scxtt on 2006-07-22
that's pretty cool, maybe i'm to used to having all items i've searched for highlighted, but i'd get more mileage out of **set hlsearch** -- but cool tip ...

---

### Post by jayemef on 2006-07-23
Here's my .vimrc, if at all interested:
```

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" General                                                                    "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
filetype on              " Make Vim aware of the file type.
set nocompatible         " Get rid of Vi compatibility mode.
set isk+=_,$,@,%,#,-     " Make these characters count as part of a word.
set viminfo+=!           " Make sure we can save viminfo.


""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Theme/Colors                                                               "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
syntax on                " Enable syntax highlighting.
colorscheme Default      " Change colorscheme.


""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Vim UI                                                                     "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set ruler                " Always show info along bottom.
set noerrorbells         " Disable error bells.


""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Visual Cues                                                                "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set showmatch            " Show matching braces and brackets.
set mat=5                " How many tenths of a second to show a match.
set nohlsearch           " Don't continue to highlight searched phrases.
set incsearch            " But do highlight as you type your search.
set visualbell           " Blink instead of beep.
set so=5                 " Keep 5 lines for scope.


""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Text Formatting/Layout                                                     "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set fo=tcrqn             " See help (complex).
set ai                   " Autoindent.
set si                   " Smart indent.
set cindent              " C-style indenting.
set tabstop=4            " Tab spacing (settings below coorespond to unify.
set softtabstop=4        " Unify.
set shiftwidth=4         " Indent/outdent by 4 columns.
set shiftround           " Always indent/outdent to the nearest tabstop.
set expandtab            " Use spaces instead of tabs.
set smarttab             " Use tabs at the start of a line, spaces elsewhere.


""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Folding                                                                    "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set foldenable           " Turn on folding.
set foldmethod=indent    " Make folding indent sensitive.
set foldlevel=100        " Don't autofold for me.
set foldopen-=search     " Don't open folds when you search into them.
set foldopen-=undo       " Don't open folds when you undo stuff.


```

Looks crappy without a mono-width font, but you get the picture...

---

