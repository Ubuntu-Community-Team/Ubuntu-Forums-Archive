---
title: "Screen (terminal multiplexer) and Vim not playing nicely"
date: 2009-02-24
forum: Desktop Environments
---

### Post by harisund on 2009-02-24
Note: This is not a Ubuntu specific problem, but it is a "desktop environment" problem if you look at it from my point of view (my command line is my "desktop" for the most part :-) ) 

Anyway, here goes. In my ~/.vimrc I have the following line: 
map <C-F10> <C-C>:s/^/\/\/<CR>:noh<CR>

What this does is comment out my C++ code by adding "//" to the beginning of the line. (Among other things, if I am in insert mode, it goes to command mode thanks to C-C, and it also removes the highlighting that follows with noh.) I often select blocks of text using visual mode in VI, and comment out the lines using this shortcut (ctrl + F10) 

However, I just realized that when use Vim under Screen (the terminal multiplexer) Ctrl+F10 no longer is recognized by Vim. After a little poking around I understand it's used by screen. 

:bindkey -d 

Executing the above on screen reveals that F10, F11 keys are being used for something else. 
:k9:               -> stuff ^[[20~
:k;:               -> stuff ^[[21~
:F1:               -> stuff ^[[23~
:F2:               -> stuff ^[[24~

The above lines indicate F9, F10, F11, F12 keys are bound to something. And I don't like it. 

(In Vim they seem to be replacing the text to upper case). 

I understand we need to have a "bindkey -k F1 ... " line in our ~/.screenrc to remove the key binding in screen, but I am not having much success. Anyone help please?

---

