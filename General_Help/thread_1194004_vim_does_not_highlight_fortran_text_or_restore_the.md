---
title: "vim does not highlight fortran text or restore the cursor location"
date: 2009-06-22
forum: General Help
---

### Post by centguy on 2009-06-22
Hi,

I have apt-get install vim to get a new vim, but then I cannot see that vim gives me a new look when I open a C or Fortran90 or cpp files where text are highlighted according to the syntax. When I reopen a file, the cursor starts from line 1, which is not the line when I closed the file previously. Thanks for your support!

---

### Post by lloyd_b on 2009-06-22
1.  In the file "~/.vimrc", ensure that "syntax on" is present (and not commented out.  This enables syntax highlighting.

2.  If the file "~/.viminfo" exists and is readable/writeable, then the file position should be saved.  Verify that this file does exist, and that your user has permissions to read/write it.  Also, check that the section of "~/.vimrc" covering this feature is uncommented:```
" Uncomment the following to have Vim jump to the last position when
" reopening a file
if has("autocmd")
  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
    \| exe "normal g'\"" | endif
endif
```

Lloyd B.

---

### Post by geirha on 2009-06-22
To get your vim configured as you want it, copy /etc/vim/vimrc to .vimrc in your home-folder
```
cp /etc/vim/vimrc ~/.vimrc
```

Then edit ~/.vimrc and uncomment the configuration you want.

You can also edit /etc/vim/vimrc instead of course. That will affect all users, not just you.

---

### Post by centguy on 2009-06-22
Thanks! This is very useful! It works!

---

