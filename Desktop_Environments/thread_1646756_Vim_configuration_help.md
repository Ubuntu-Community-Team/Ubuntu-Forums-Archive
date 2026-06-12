---
title: "Vim configuration help"
date: 2010-12-16
forum: Desktop Environments
---

### Post by lucacerone on 2010-12-16
> Full solution in a tutorial-like fashion can be found below at:
[http://ubuntuforums.org/showthread.php?p=10248614#post10248614](http://ubuntuforums.org/showthread.php?p=10248614#post10248614)
Dear all,
I'm trying to configure Vim so that I can apply
a color scheme I like but without any success.

I tell you what I've done so that hopefully you can help me.

I have created a .vim folder in my home directory.

I downloaded the Color Sampler Pack from [http://www.vim.org/scripts/script.php?script_id=625](http://www.vim.org/scripts/script.php?script_id=625) and extracted it in the .vim folder.

When I load Vim, I try to apply the color scheme
I want by writing:

:colorscheme fine_blue

In vim the colour are not applied.
However it works fine using gvim (but I'd like to use
vim, since I often login to my account through ssh).

In the package page, something is told by scheme that work in
gvim but in vim, but I couldn't understand what's it about,
and how to make things work.

Also in gvim the colorscheme I chose is applied once,
but whenever I close the program, I lose the settings
and I have to reload the colour scheme again.

So here are the 3 tasks I'd like to do:
1) make the fine_blue (or whatever else) colour scheme working into vim
2) make it the default colour scheme so that I don't have to load it every time
3) make this be available when I'm connecting through ssh also.

Can you guys help me please?
Cheers, -Luca

> P.s. full solution in a tutorial-like fashion can be found below at:
[http://ubuntuforums.org/showthread.php?p=10248614#post10248614](http://ubuntuforums.org/showthread.php?p=10248614#post10248614)

---

### Post by lykeion on 2010-12-16
[http://vimcasts.org/episodes/creating-colorschemes-for-vim/](http://vimcasts.org/episodes/creating-colorschemes-for-vim/)

---

### Post by lucacerone on 2010-12-16
Thanks, but it's not really what I want to do.
I already have a set of colors schemes that I like.
They were created for gvim but I can't make them work
in vim and can't understand why.

Thanks in any case,
other suggestions?

---

### Post by gmargo on 2010-12-16
In the description field of the Color Sampler Pack page you gave, there's a link to "CSApprox", which is a script to use gvim color schemes in vim, which sounds like what you're asking for. 

[http://www.vim.org/scripts/script.php?script_id=2390](http://www.vim.org/scripts/script.php?script_id=2390)

As far as your other questions....  To load a color scheme every time you start vim, place the command in your $HOME/.vimrc file.

---

### Post by lucacerone on 2010-12-16
Hi, thanks, I've read about the package but I couldn't
manage to make it work.
Apparently Vim doesn't think my shell is 256 colours.
But using some script I've found on the web to test
whether I'm using 256 colours or not, it seems to me
that the shell (bash) supports them.

Has any of you tried and make it work?
If so could you tell me how?
Cheers, -Luca

---

### Post by lucacerone on 2010-12-17
I finally found a solution.
So I'm writing a mini-tutorial on how to
get vim colorus working.

1) First of all it's necessary to enable 256 colours in your shell.
to check if they're enabled just open a terminal and write
```

tput colors

```
you should get a number.
If it's 256 you can go to step 3 else skip to step 2.

2) Enable 256 colors (this works for bash, xterm and I could get
colours also through ssh connection).

In order to do this you need to add the following
```

if [ -e /usr/share/terminfo/x/xterm-256color ]; then
        export TERM='xterm-256color'
else
        export TERM='xterm-color'
fi

```

both to your ~/.bashrc and to your ~/.profile
file.

After editing these two files reload the configurations by typing:
```

source ~/.bashrc
source ~/.profile

```

After this step your shell should be ready for the 256 colours.
Check this typing: "tput colors"  in your terminal.

3. Add the colour schemes you want to vim.
You can then add color schemes you create or find online
in your ~/.vim/colors folder. (if it doesn't exist create it)

Then modify the file ~/.vimrc (if it doesn't exist create it)
and add the lines
```

set t_Co=256
colorscheme= <colorschemename> #No extension .vim!!!

```

When opening vim now your colour scheme should be working :)

4) Optional
If you want a package of colour schemes just download them from:
[http://www.vim.org/scripts/script.php?script_id=625](http://www.vim.org/scripts/script.php?script_id=625)

To be able to easily scroll them and check how they look
download this plugin:
[http://www.vim.org/scripts/script.php?script_id=1488](http://www.vim.org/scripts/script.php?script_id=1488)
(Download file ScrollColors.vim and put it into your ~/.vim/plugin )

To be able to convert gvim color schemes use this plugin:
(simply extract it in your .vim directory and the files will be in the right place)
[http://www.vim.org/scripts/script.php?script_id=2390](http://www.vim.org/scripts/script.php?script_id=2390)

Hope this can help to save some time to some of you!
Cheers, -Luca

---

