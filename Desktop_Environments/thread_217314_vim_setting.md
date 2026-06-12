---
title: "vim setting"
date: 2006-07-16
forum: Desktop Environments
---

### Post by soongwoo on 2006-07-16
I like vim under Ubuntu which shows the cursor postion
with row and column number at the bottom right corner.

I want to set it under my old machine.
Is there anyone how to configure vimrc for displaying
line number and column number at the bottom right?

Thanks
soongwoo

---

### Post by Athropos on 2006-07-17
Here is my .vimrc as an example. The "set statusline" is what you are looking for.

```

" General Setup
" -------------

" Disable compatibility with vi
set nocompatible

" Use the Unix file format
set fileformats=unix,dos

" Display line number in front of each line in the left margin
set number

" I don't like backups
set nobackup

" Display commands in the bottom right corner as they are typed
set showcmd

" Smoother redraws
set ttyfast

" Enable syntax highlighting
syntax on





" Colors
" ------

set background=dark

highlight Normal      ctermfg=White
highlight StatusLine  ctermfg=White         ctermbg=DarkGreen   cterm=NONE
highlight User1       ctermfg=White         ctermbg=DarkGreen   cterm=NONE
highlight LineNr      ctermfg=Red
highlight Visual      ctermfg=White         ctermbg=LightRed
highlight Search      ctermfg=White         ctermbg=LightRed
highlight Cursor      ctermfg=Black         ctermbg=Green





" Additional filetypes
" --------------------

if has("autocmd")
    au BufRead,BufNewFile *.cls set filetype=tex
    au BufRead,BufNewFile sconstruct set filetype=python
endif





" Indenting and Tabbing
" ---------------------

" Number of spaces used for (auto)indenting
set shiftwidth=4

" Number of spaces to insert for a <tab>
set softtabstop=4

" Insert spaces when the <tab> key is pressed
set expandtab

" Enable specific indenting for c-code and others and some nice options for cindenting
set cindent





" Search
" ------

" I can't live without incremental search
set incsearch

" Highlight the search terms
set hlsearch

" Ignore case when searching...
set ignorecase
" ...but take it into account if there is an uppercase letter in the pattern
set smartcase

" Wrap search when EOF is reached
set wrapscan





" Status
" ------

" Always display the status line
set laststatus=2

" format string
set statusline=%1*\File:\ %*%f%1*%5m%*%=\L%-5l\ \C%-4c%5p%%\ [%L\ \lines]

" Show the current editing status
set showmode





" Edition
" -------

" Allow the backspace key to delete anything
set backspace=indent,eol,start

" Display trailing spaces using ~ characters and tabs with -> characters
set lcs=tab:<-,trail:~

" Don't break words
set linebreak

" Display as many lines as possible
set display=lastline





" Maps
" ----

" Ctrl-x :
" In command mode, clear the highlight after a search
map <C-X> :let @/=""<CR>

" Move between visible lines and not between real lines
map <silent> <Up> gk
map <silent> <Down> gj
map <silent> <home> g<home>
map <silent> <end> g<end>

imap <silent> <Up> <C-o>gk
imap <silent> <Down> <C-o>gj
imap <silent> <home> <C-o>g<home>
imap <silent> <end> <C-o>g<end>

```

---

### Post by soongwoo on 2006-07-24
Thank you very much.
I'll let you know what happens in FC5.

soongwoo

---

### Post by reclusivemonkey on 2006-07-25
> **soongwoo said:**
> Thank you very much.
I'll let you know what happens in FC5.

soongwoo

vimtutor will give you all sorts of tips about using vim.

---

### Post by davebgimp on 2006-09-19
> **Athropos said:**
> Here is my .vimrc as an example. The "set statusline" is what you are looking for.

Handy. Thanks for the .vimrc.

---

