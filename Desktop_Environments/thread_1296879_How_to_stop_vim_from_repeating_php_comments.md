---
title: "How to stop vim from repeating php comments"
date: 2009-10-21
forum: Desktop Environments
---

### Post by frankvw on 2009-10-21
Hi,everyone,

I'm sure this is simple but it drives me bats.

I have vim 1:7.1.314 installed on Intrepid. Which works fine, except that its default behavior is to repeat comments when I edit php files. When a line starts with a double slash ('//') to denote a PHP comment, vim will place the double slash on the next line too when I hit enter. Meaning that when I paste a PHP snippet that contains a comment somewhere, I end up with garbage.

I tried to edit /etc/vim/vimrc to enable 'compatible' mode, but that broke the showing of matching brackets (which could not be turned on again) and worse, it reduces the 'undo' function ('u' key) to one level only.

I tried to enable syntax highlighting, but that causes vim to spout errors when I try to edit a PHP file (something that seems to be related to errors in /usr/share/vim/vim71/syntax/php.vim).

Suggestions anyone? I **need** to stop vim from inserting comment delimitors, but without breaking the multi-level undo, and preferably without breaking the matching brackets feature too. On top of that syntax highlighting without errors would be great, too, but the unwanted insertion of comment delimitors is the critical issue here.

All suggestions would be greatly appreciated!

// FvW

---

### Post by Morons on 2010-01-21
I have exactly this problem but It will also repeat the # in bash fileas as well as in settings files like 
> vi /etc/network/interfaces
This section> # The primary network interface
iface eth0 inet static
        address 192.168.11.110
        netmask 255.255.255.0
        network 192.168.11.0
        broadcast 192.168.11.255
        gateway 192.168.11.1
Will Become (note the line tabing will also increase adding one tab extra per line the "quote" below does not show the white characters
> # The primary network interface
# iface eth0 inet static
#         address 192.168.11.110
#                 netmask 255.255.255.0
#                         network 192.168.11.0
#                                 broadcast 192.168.11.255
#                                         gateway 192.168.11.1
#

---

### Post by DaithiF on 2010-01-21
Hi, in your .vimrc, add a line for:
```
au FileType php setl fo-=ro

```

this will turn off (just for php files) a couple of format options which control auto-commenting

to learn more, in vim do:
:help fo-table
:help comments

---

### Post by Morons on 2010-01-22
Althow your answer covers php it did nothing for my "setting" files that have no extention, they are pain files with application settings like the /etc/network/interfaces and most /etc files

---

### Post by DaithiF on 2010-01-22
to do it for all file types you could either:
```
au FileType * setl fo-=ro
```

or I think this should also work (though untested)
```
set fo-=ro
```

---

### Post by Morons on 2010-01-22
Thanx, TUVM wow nice

---

