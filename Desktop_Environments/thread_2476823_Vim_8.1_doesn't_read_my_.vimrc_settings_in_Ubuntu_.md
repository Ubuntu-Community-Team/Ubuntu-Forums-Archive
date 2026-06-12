---
title: "Vim 8.1 doesn't read my .vimrc settings in Ubuntu 20.04"
date: 2022-07-08
forum: Desktop Environments
---

### Post by nibal on 2022-07-08
Hi

Recently I upgraded my ubuntu to 20.04.
I need a block in reverse video for cursor.
No matter what I put in my .vimrc file, I always get the same "invisible" cursor that disappears completely
over my dark background. If I just remove my .vimrc file, nothing changes.
I can only assume that vim doesn't read my .vimrc file:(
Since I always invoke vim as vi, I uninstalled vim-tiny, so that it doesn't
interfere with my display.
I edited also the /etc/vim/vimrc for any incompatible settings, but there was nothing that could
cause such a problem:( Since vim doesn't read my .vimrc file, where is it getting those weird settings?
I would like to also change my terminal cursor to block, reverse video.
Right now it is the same "invisible" cursor as in vim. Could it be the same cause?

TIA
Nikos

---

### Post by Holger_Gehrke on 2022-07-09
I'm not an experienced user of vi, but I do think it runs in the terminal and that governs the appearance of the cursor. If I change the cursor in my xfce4-terminal with "Bearbeiten"->"Einstellungen" tab "Allgemein", item "Eingabemarkenform" (That should be "Edit"->"Settings", tab "General", item "Cursor Shape" ...) then the cursor shape in vi will be whatever I set. This is in XUbuntu using xfce4-terminal, but the gnome-terminal in Ubuntu should have similar options as described in [https://help.gnome.org/users/gnome-terminal/stable/app-cursor.html.en](https://help.gnome.org/users/gnome-terminal/stable/app-cursor.html.en) .

Holger

---

### Post by nibal on 2022-07-09
Thx for your fast reply,

We can set vim cursor independently from the terminal.
However, since i want to change both this is what I have in my gnome-terminal Preferences:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290702&stc=1[/IMG]

Unfortunately, it doesn't work. My cursor is neither block, nor beam not even umderline. It is just "invisible" and very difficult to work with:(

Nikos

---

### Post by #&amp;thj^% on 2022-07-09
Could you give this a quick try:
```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```
To revert:
```
gsettings set org.gnome.settings-daemon.plugins.cursor active true
```

---

### Post by nibal on 2022-07-09
Thx,

Sorry it didn't work:(
Highlighted text still invisible with either setting:(

---

### Post by #&amp;thj^% on 2022-07-09
Thanks for trying.
If you want to know for sure if vim is accessing your ~/.vimrc on startup you can launch it with strace:
```

strace -o vim_strace vim
```

then quit vim. Open the vim_strace file and search for "vimrc" in the file. you should find a line like this:
```

stat64("/home/youruser/.vimrc", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
```

which means that at least vim sees the file.
A easier way to see is to use:
```
grep .vimrc vim_strace
```
Maybe this will point to something we can use.

---

### Post by nibal on 2022-07-09
Thx for your fast reply,

It's reading my .vimrc file, but not using it :(
Probably some syntax error in the vimrc file?
Doesn't vim report any errors in a log?
Attaching my .vimrc...Hmmm it errs "invalid file".
It will take the gziped file;-)
[ATTACH]290703[/ATTACH]

Nikos

---

### Post by #&amp;thj^% on 2022-07-09
I seen a few things different but this is something to look at:
Just a snip of mine:
```
" Disable compatibility with vi which can cause unexpected issues.
set nocompatible

" Enable type file detection. Vim will be able to try to detect the type of file in use.
filetype on

" Enable plugins and load plugin for the detected file type.
filetype plugin on

" Load an indent file for the detected file type.
filetype indent on
" Turn syntax highlighting on.
syntax on
" Add numbers to each line on the left-hand side.
set number
" Highlight cursor line underneath the cursor horizontally.
set cursorline

" Highlight cursor line underneath the cursor vertically.
set cursorcolumn

```
If you don't want line numbers just omit what I show.

---

### Post by nibal on 2022-07-09
Hi Fallen,

I just rebooted into my Ubuntu, and this time I have block cursors in both the terminal and vim
I had rebooted a thousand times before and nothing happened. What was different this time was that I clicked on
gnome-terminal settings, without changing them. I tried them immediately but with no effect.
Maybe it needed a reboot:( 
Now all my colors are off, and I have to fix them:)
Thank you for all your time and help.
I will borrow a few of your vimrc settings:)
Line numbers are fine...cursor column and line were confusing with a block cursor...
Damn! What's wrong with this forum? It logs you out every 5' and throws you out of the thread:( 

Take Care
Nikos

---

