---
title: "Colourful bash ala the fish shell"
date: 2009-02-12
forum: General Help
---

### Post by monsterstack on 2009-02-12
The fish shell is a really great shell to use (I use it as my default shell), but it's quite a pain to customise. It doesn't honour the bashrc file, and any customisation has to be made via fish files. Furthermore, the syntax of the fish shell is different enough so that doing some things common on the command-line (for me anyway) are a little bit oblique. Or perhaps I'm just too familiar with the bash way of doing things, who knows.

But the out-of-the-box features are really cool. I was wondering if anyone knows of a way to make plain ol' bash react in a similar fashion. Specifically, my favourite feature of fish is the excellent coloured tab-completion system. When you start to type in the terminal, the shell automatically scans your $path directories for terms matching that command in real time. For commands that aren't found, the font is red. So, if I type "amarok", the font will remain red till the last letter has been typed. For multiple-possibility tab-completions it reacts the same way as bash and shows a handy list. The colour thing is really useful, though: it spots syntax errors and typos and all that good stuff before I actually execute commands. 

Any advice appreciated.

---

### Post by bodhi.zazen on 2009-02-12
You will get a ton of opinions, I advise zsh

The biggest problem with zsh is you need a decent .zshrc.

Mine is here (read the comments at the top, ie install most and display-dhammapada ;) )

[http://bodhizazen.net/adblock/zshrc](http://bodhizazen.net/adblock/zshrc)

save the file to ~.zshrc (after reviewing it of course).

And yes, you identified all the major issues with fish, nice idea, but running a non-standards compliant shell, like fish, is, IMO, more trouble then it is worth.

---

### Post by monsterstack on 2009-02-12
Just given it a go, with a few quick edits to your rc script. Whilst it isn't *exactly* what I was looking for, it seems pretty cool. The tab completion thing is pretty spectacular with its scrollability. I'll have a go at editing it a bit more, I think. I love what you've done with the calender thing. Thanks very much!

---

### Post by bodhi.zazen on 2009-02-12
You are most welcome.

most is a pager and will display man pages in color (you still call them with the man command).

have fun, zsh has a ton of features (I am still discovering some).

---

