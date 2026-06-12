---
title: "I need Help Setting Up TCSH"
date: 2009-06-09
forum: General Help
---

### Post by bgood44 on 2009-06-09
Hey everyone, 

I recently Installed Ubuntu onto my laptop.  I dual boot with xp.  I believe my ubuntu is jaunty jackalope, or whatever the most recent version is as I have been keeping up with the updates.  At work we use tcsh on our computers and I would also like to have it on my personal computer.  I am very new to linux and am still learning (thats why I installed it on my pc...It is growing on me).  


I installed tcsh using the synaptic package manager.  I than changed it to my default shell by typing into the command line : chsh -s /bin/tcsh

The shell seems to be working fine but there are a few things that are bothering me.  

1.  First and foremost, there is no .tcshrc file.  Shouldn't it have came with the download?  If not, where can I get a general one that will work well with ubuntu

2.  I think this is probably related to number 1 but here goes ..... When I have the default bash as my shell, when I use the 'ls' command, the different listings show up in different colors, for example, directories are blue , compiled c++ programs are green, and text files are black.    When I 'ls' in tcsh, everything shows up the same color, black.  I Imagine this is related to the lack of .tcshr file.


3.  This isn't really a problem, more of a general question...Like I said I am very new to linux, can any of you recommend a source for me to learn about shell scripting in tcsh?


Thanks,

Brad

---

### Post by bgood44 on 2009-06-10
Anyone ?

---

### Post by nomarior on 2009-08-03
Hi bgood44,

it's a shame no one answered you so far. Here is what I know:

1. tcsh uses the ".cshrc" file, that means, if you what to configure your tcsh, just create a .cshrc file.
     edit: you can just as well create a .tcshrc file (probably better, if you don't want to share the config with a csh [be it there or not, maybe you need that one in the future, who knows?])

2. that's what I just tried to find out, when google showed up your post. I haven't solved that one yet.
edit: HEURECA! There's a really simple trick. Make sure you have the following line in your .tcshrc file:
alias ls "ls --color=auto"

I also like to add the following aliases after that one (just in case anyone is interested in those):
alias l "ls -l"
alias ll "ls -lA"

Don't forget to read the new source with "source .tcshrc".

3. I recommend you learn to use bourne shell for scripting (the original "sh", not the bourne again shell "bash"). It is more cumbersome to script in bourne shell, but the big advantage is, that every system has a bourne shell and your script does not have dependencies on more fancy shells.

As to where to start learning bourne shell, I just google it every time I need to look something up. It is always good to look at several places, because one always learns some new tricks that way. To get started try this link: [http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)

For everything else, manpages are your friend. -> man tcsh, man sh, man whatever

Best regards

---

