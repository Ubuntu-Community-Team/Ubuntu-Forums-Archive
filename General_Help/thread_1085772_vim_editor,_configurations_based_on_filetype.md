---
title: "vim editor, configurations based on filetype"
date: 2009-03-03
forum: General Help
---

### Post by pokeyThePenguin on 2009-03-03
I would like to have Vim enable and disable and set certain things based on what filetype is being edited.

For example, if I open up a C file, I want Vim to automatically enable c-syntax highlighting and set autoindent and highlight matching brackets.

I understand I can add those commands to a .vimrc file in my home directory, but how do I get Vim to only execute those commands if the filetype is .c?

Also, is .vimrc a user created file? I don't have .vimrc, so I'm just making sure that that's why I don't have it (I haven't created it yet).

---

### Post by BJ_Covert_Action on 2009-03-03
By no means am I a Vim expert, but I did run through the tutorial embedded in the program and found that the vimrc file is indeed user created. In fact, your version of vim probably came with an example vimrc file that you can read and write to your own vimrc file to make your life easy. For more information on this (basically to run the Vim tutorial that comes with Vim), locate the 'tutor' file within your Vim directory (mine was located under the subdirectory vim72). Then just open a terminal, navigate to that particular directory and type: 'vim tutor' or 'gvim tutor' depending on your preference (gvim opens the GUI version of Vim).

It can be a bit tedious but it is a good place to start learning Vim. It is very interactive. For the information that is particular to the vimrc file scroll down to Section 7.2 and it will tell you a bit about the vimrc file.

Again, I am no expert, but going through the whole tutorial did help. If someone more experienced than me has better advice/sources you might want to take their word over mine.

I hope this helps.
Cheers,
Brady

---

### Post by Slim Odds on 2009-03-03
Yes, .vimrc (and maybe .gvimrc) are files that you create.

Here's what I do (it does some other stuff also):
```

function! s:LoadSrcFiles()
     setlocal ff=unix
     setlocal foldmethod=syntax
     highlight WhiteSpaceEOL ctermbg=lightgreen guibg=#303050
     match WhiteSpaceEOL /\s\+$/
 endfunction

" For source code files, use some special settings
autocmd FileType c,cpp,ruby,python,cmake,vim, call s:LoadSrcFiles()

```BTW: I put "syntax enable" in my .vimrc also (it's fine to just turn it on globally, since it only highlights file types that have highlighting info).

---

### Post by pokeyThePenguin on 2009-03-03
Great! Thanks guys!

This is what my .vimrc looks like right now (it's fairly bare at the moment):
```

function ConfigureForC()
        syntax enable
endfunction

autocmd FileType c call ConfigureForC()

```

Note that your function name must start with a capital letter. :)

---

### Post by Slim Odds on 2009-03-03
> **pokeyThePenguin said:**
> Note that your function name must start with a capital letter. :)

It's even better to limit the scope by putting the "s:" in there.

Also, why don't you just put "syntax enable" in your .vimrc for everything?

BTW, your version turns syntax highlighting on **globally** anyway.

---

