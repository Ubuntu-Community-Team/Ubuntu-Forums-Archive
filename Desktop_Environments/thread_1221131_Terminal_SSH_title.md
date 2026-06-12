---
title: "Terminal SSH title"
date: 2009-07-23
forum: Desktop Environments
---

### Post by OpenBluntSurgery on 2009-07-23
Hello,
I would like to make the terminal title dynamic for SSH sessions I connect to.
I am using aliases in my .bashrc to connect via ssh to servers, would it be some kind of script that I would need to make to update the title?


Any ideas are welcome.


Thanks and this is my first post =)

---

### Post by dlmarti on 2009-07-23
Set the PS1 evn variable on your hosts to emit the escape sequence that resets the title.

[http://http://www.ibiblio.org/pub/Linux/docs/HOWTO/Xterm-Title]("http://http//www.ibiblio.org/pub/Linux/docs/HOWTO/Xterm-Title")

---

### Post by chichilalescu on 2009-11-04
This page has some details
[http://vim.wikia.com/wiki/Automatically_set_screen_title](http://vim.wikia.com/wiki/Automatically_set_screen_title)

What I did was to enter the following in my .vimrc:

```

set titlestring=%t%(\ %M%)%(\ (%{expand(\ "%:p:h\")})%)%(\ %a%)\ -\ %{hostname()}
set title

```

I'm not sure it's perfect, but it seems to work.

---

