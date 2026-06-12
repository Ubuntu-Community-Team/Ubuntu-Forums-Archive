---
title: "vi / vim syntax highlighting"
date: 2006-01-03
forum: General Help
---

### Post by 5-HT on 2006-01-03
Hi, I wondering if someone may be able to help me out with an issue (or is it?) that I'm having with syntax highlighting in vim?

For whatever reason, syntax highlighting only works if I open up an existing file with vim.

If I just open up vim and type, syntax highlighting is disabled.

I've tried setting 'syntax on' and 'syntax enable' during run-time and they work great, but only on previously saved files.

I've tried creating my own .vimrc file containing both 'syntax on' and 'syntax enable', uncommenting the 'syntax on' in /etc/vim/vimrc, using the suggested vimrc file ($VIMRUNTIME/vimrc_example.vim) placed in ~/.vimrc by vimtutor (great tutorial !), and searched all threads I could find on the subject with no luck.


Is this normal behaviour for vim, or does anyone have any ideas?

Thanks for any help!

---

### Post by schilcha on 2006-01-03
This is, what works for me:

:syn on

:set syn=perl

of course, substitute "perl" with whatever you need -- I don't know if there's an automatism to this (e.g. set syn=auto).

I don't need this, if the new filename has the correct extension (e.g. newfile.pl)

---

### Post by 5-HT on 2006-01-03
Worked great, thanks!

Guess the file must be defined beforehand to get it to work automatically, but this works beautifully for anything in the buffer.

---

### Post by jrib on 2006-01-03
apparently I can't read your whole post before posting, ignore this :P

---

### Post by darth_vector on 2006-01-03
to enable syntax highlighting by default, edit /etc/vim/vimrc. find the line

```
" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
" syntax on
```

and uncomment the last line. or write your own .vimrc file :)

---

### Post by 5-HT on 2006-01-07
[QUOTE=darth_vector]to enable syntax highlighting by default, edit /etc/vim/vimrc. find the line....[/Quote]

Thanks for the help.
I tried uncommenting that line in /etc/vim/vimrc as well as creating a ~/.vimrc and putting it in there, and while that works for preexisting files (or a new file that I named when opening up vim) it didn't do the trick for opening up vi and starting to type on the fly prior to naming the file (or even naming it once done).


Schilcha's suggestion of entering:

:syn on

:set syn=<language of choice>

Worked great for that situation.

Guess it would be easier to just name it when opening, but this serves as a great fallback (for my laziness...).

Thanks.

---

### Post by Strife on 2006-01-07
What I usually do is name the new file that I'm working on. That is, if you start vim from the command line, you'd do

```
vim file.cpp
```

for example. Similarly, from within vim, you would do

```
:new file.cpp
```

or

```
:e file.cpp
```

That way from the moment you start typing, you'll get syntax highlighting. That seems to be the easiest way to do it for me.

---

### Post by 5-HT on 2006-01-13
[QUOTE=Strife]...[/QUOTE]

Thanks for the tip, guess there are many ways to get the same thing done.
Gotta love *nix for that!

---

### Post by lm317t on 2006-04-24
I find the following .vimrc helpful on most of my linux installs.  Its very intuitive to most noobs.  Its based on Mandrake 10.1's vimrc file.  There are many annoyances I have found with the default Ubuntu vimrc setup.  
```


syntax on

"Set a statusbar
set statusline=~

"I know it's horrible for a vi master but useful for newbies.
imap <C-a> <Esc>I
imap <C-e> <ESC>A
map <C-Tab> <C-W>w
imap <C-Tab> <C-O><C-W>w
cmap <C-Tab> <C-C><C-Tab>

"Some macros to manage the buffer of vim
map <F5> :bp<C-M>
map <F6> :bn<C-M>
map <F7> :bd<C-M>

"Default backspace like normal
set bs=2

"Terminal for 80 char ? so vim can play till 79 char.
"set textwidth=79

"Some option desactivate by default (remove the no).
set nobackup
set nohlsearch
set noincsearch

"Display a status-bar.
"set laststatus=2

"Show the position of the cursor.
set ruler

"no wrap
"set nowrap

"Show matching parenthese.
set showmatch

set background=dark

"" Gzip and Bzip2 files support
" Take from the Debian package and the exemple on $VIM/vim_exemples
if has("autocmd")

" Set some sensible defaults for editing C-files
augroup cprog
  " Remove all cprog autocommands
  au!

  " When starting to edit a file:
  "   For *.c and *.h files set formatting of comments and set C-indenting on.
  "   For other files switch it off.
  "   Don't change the order, it's important that the line with * comes first.
  autocmd BufRead *       set formatoptions=tcql nocindent comments&
  autocmd BufRead *.c,*.h set formatoptions=croql cindent comments=sr:/*,mb:*,el:*/,://
augroup END

" Also, support editing of gzip-compressed files. DO NOT REMOVE THIS!
" This is also used when loading the compressed helpfiles.
augroup gzip
  " Remove all gzip autocommands
  au!

  " Enable editing of gzipped files
  "       read: set binary mode before reading the file
  "             uncompress text in buffer after reading
  "      write: compress file after writing
  "     append: uncompress file, append, compress file
  autocmd BufReadPre,FileReadPre        *.gz set bin
  autocmd BufReadPre,FileReadPre        *.gz let ch_save = &ch|set ch=2
  autocmd BufReadPost,FileReadPost      *.gz '[,']!gunzip
  autocmd BufReadPost,FileReadPost      *.gz set nobin
  autocmd BufReadPost,FileReadPost      *.gz let &ch = ch_save|unlet ch_save
  autocmd BufReadPost,FileReadPost      *.gz execute ":doautocmd BufReadPost " . %:r

  autocmd BufWritePost,FileWritePost    *.gz !mv <afile> <afile>:r
  autocmd BufWritePost,FileWritePost    *.gz !gzip <afile>:r

  autocmd FileAppendPre                 *.gz !gunzip <afile>
  autocmd FileAppendPre                 *.gz !mv <afile>:r <afile>
  autocmd FileAppendPost                *.gz !mv <afile> <afile>:r
  autocmd FileAppendPost                *.gz !gzip <afile>:r
augroup END

augroup bzip2
  " Remove all bzip2 autocommands
  au!

  " Enable editing of bzipped files
  "       read: set binary mode before reading the file
  "             uncompress text in buffer after reading
  "      write: compress file after writing
  "     append: uncompress file, append, compress file
  autocmd BufReadPre,FileReadPre        *.bz2 set bin
  autocmd BufReadPre,FileReadPre        *.bz2 let ch_save = &ch|set ch=2
  autocmd BufReadPost,FileReadPost      *.bz2 set cmdheight=2|'[,']!bunzip2
  autocmd BufReadPost,FileReadPost      *.bz2 set cmdheight=1 nobin|execute ":doautocmd BufReadPost " . %:r
  autocmd BufReadPost,FileReadPost      *.bz2 let &ch = ch_save|unlet ch_save

  autocmd BufWritePost,FileWritePost    *.bz2 !mv <afile> <afile>:r
  autocmd BufWritePost,FileWritePost    *.bz2 !bzip2 <afile>:r

  autocmd FileAppendPre                 *.bz2 !bunzip2 <afile>
  autocmd FileAppendPre                 *.bz2 !mv <afile>:r <afile>
  autocmd FileAppendPost                *.bz2 !mv <afile> <afile>:r
  autocmd FileAppendPost                *.bz2 !bzip2 -9 --repetitive-best <afile>:r
augroup END

endif " has ("autocmd")


```

---

### Post by diogo.delgaudio on 2006-04-24
gr8 topic.. just what i was looking for... ;)

---

### Post by mdecler2 on 2006-12-02
> **schilcha said:**
> This is, what works for me:

:syn on

:set syn=perl

of course, substitute "perl" with whatever you need -- I don't know if there's an automatism to this (e.g. set syn=auto).

I don't need this, if the new filename has the correct extension (e.g. newfile.pl)

This works great. However, I find that typing this in every time I open a file is tedious. CUrrently, Vim maps certain file extensions to a syntax highlighting scheme with "syntax on". I get c++ highlighting for .cpp files.

I want vim to recognize another files extension, namely .def, to highlight with the c++ color scheme.

Does anyone have any ideas for modifying the .vimrc? Or some other solution to my problem that doesn't involve setting syn every time?

---

### Post by balki2005 on 2007-06-03
helllo,

I tried to  setup  the syntax highlighting,  but  i  recieve everythime this  error:

E319: Sorry, the command is not available in this version 

I work  with  ubuntu Festy and i have  vim  version:

VIM - Vi IMproved 7.0 (2006 May 7, compiled May 22 2007 21:10:57)

and  the  configuration files  it says that  you  need a version  5 or higher

what  goes  wrong ??

thanks in advance,

balki2005:(:(

---

### Post by DC@DR on 2007-06-03
You should create a .vimrc file in your home folder, and put something like this:
```

syntax enable
set number
filetype on
filetype plugin on
set tabstop=4
set softtabstop=4
set shiftwidth=4
set noexpandtab
set smarttab
set noerrorbells
set nocompatible
set ai
set si
set cindent
set mouse=a
set nowrap
set incsearch
set showmatch
set mat=5
set wrap
set hls
set cul
set wrapscan
set sol

```
or take a look here: [http://www.vi-improved.org/vimrc.php](http://www.vi-improved.org/vimrc.php)

---

### Post by balki2005 on 2007-06-03
I have  done  you said, but still  have  this  error:

jonay@thunderdragon:/etc/init.d$ vim vbesave
Error detected while processing /home/jonay/.vimrc:
line    1:
E319: Sorry, the command is not available in this version: syntax enable
line   15:
E538: No mouse support: mouse=a
Press ENTER or type command to continue
jonay@thunderdragon:/etc/init.d$ vim vbesave
Error detected while processing /home/jonay/.vimrc:
line    1:
E319: Sorry, the command is not available in this version: syntax enable
line   15:
E538: No mouse support: mouse=a

thanks in  advance,

balki2005:(

---

### Post by austinz on 2007-07-29
Hi

From launchpad:

> Thank you Prasad.

You mention you tried to install available packages depending on vi, but, have you installed vim-runtime?

The standard vim package installed on Debian systems is vim-tiny.
This package contains a minimal version of vim compiled with no
GUI and a small subset of features in order to keep the package
size small.
If you want additional features (for instance syntax highlighting),
you should download the vim-runtime package.
You can donwload this with the following command:

sudo apt-get install vim-runtime

I hope this helps.

I also installed the vim-full package:

sudo apt-get install vim-full

and everything now works for me.  Hope this works for you!

Austin

---

