---
title: "yes, it is another .bash_profile queery"
date: 2010-05-03
forum: Desktop Environments
---

### Post by no_ordinary_funace on 2010-05-03
Hi there,

I'm trying to play around with shell scripts.  The tutorial I'm using says to open the .bash_profile but it does not say how.

I read another thread on this forum which gives some hints but when I follow the advice I run into a couple of problems.

One poster said the file is usually hidden and that I could use "locate" to find it.  When I tried I got this path

```
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile
```When I use "less" to try and read the dot.bash_profile file I get this

```
#####.bash_profile:personal initialization file for bash###### 
           #this script file is executed by bash(1) for login shells. by default
           #it does nothing as ~/.bashrc is already sourced by /etc/profile
```When I read the "profile" file in /etc I get something that looks a bit like what the tutorial says I should see (i.e. squiggly lines around what appear to be letters and words)

Errrr, wait, it seems like I probably should just substitute this /etc/profile for the .bash_profile in the tutorial I'm reading and see if that works, but since I've already come this far can I get some explanation about why /etc/profile is used instead of .bash_profile and if one really is meant to be a substitute for the other?  Or maybe a link which specifically deals with this issue so I don't have to search through a million google pages?

Thanks

---

### Post by mr.c.d on 2010-05-03
I think you just need to:
```
touch ~/.bash_profile
```
then edit that..

---

### Post by Mazin on 2010-05-03
/etc/profile is not a substitute for your personal ~/.bash_profile.

More to the point, I don't think that Ubuntu uses a .bash_profile file.  What are you trying to accomplish?  Have you considered using your .bashrc file instead?

---

### Post by no_ordinary_funace on 2010-05-04
Hi Mazin,

I'm trying to accomplish practicing shell scripts, like aliases and functions.  The tutorial says (for example) to add such things to the .bash_profile as they will only last for the current session unless added to the .bash_profile.

It also says to open .bash_profile with my favorite text editor, like vi, emacs, nano, or gedit, but it does not say HOW to do such a thing.  Is emacs and vi meant to come standard with Ubuntu? (I'm using karmic).

However, a user on this forum said somewhere that .bash_profile is usually hidden.  So which is it?  Just open it up all easy like, or is it hidden?  In some cases people are suggesting that it does not even exist and in in other cases people are suggesting that it's not useful even if it did exist!  GAHHHHHHH!!!!!!

I tried the "touch ~/.bash_profile" code suggested earlier, but I'm not sure what that is supposed to accomplish. When I try "locate .bash_profile"  I get

```


/home/my_comp/.bash_profile
/home/my_comp/.bash_profile~
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile


```

When I follow this line of code I'm taken to the page which says my .bash_profile is useless because .bashrc is already sourced by /etc/bash, which you are saying is NOT a substitute which seems to be what the note IS saying.  I've already kicked my cat 6 times and I still don't understand this.

Apparently, .bashrc is meant to apply when opening terminals after logging in, whereas .bash_profile is meant to apply at the time of log-in itself.

Anyway, I've found what looks like the relevant .bashrc (although using locate lists several instances of .bashrc in several different folders so I just picked the one in my home folder) so I'll probably just use that to play around with, although I'm still confused about this .bash_profile thing.

Well,
Thanks.

---

### Post by th5th on 2010-05-04
> **no_ordinary_funace said:**
> (...) open .bash_profile with my favorite text editor, like vi, emacs, nano, or gedit, but it does not say HOW to do such a thing.  Is emacs and vi meant to come standard with Ubuntu? (I'm using karmic).

This part is easy. On the command line, type:

```
vim .bash_profile
```

or if you like emacs or nano, substitute "vim" for the one you fancy. They all come bundled with pretty much every Linux distribution.


> **no_ordinary_funace said:**
> (...) .bash_profile is usually hidden. So which is it? Just open it up all easy like, or is it hidden? In some cases people are suggesting that it does not even exist and in in other cases people are suggesting that it's not useful even if it did exist! GAHHHHHHH!!!!!!

Files beginning with a dot (eg. ".bashrc", ".bash_profile" etc.) are hidden in Linux. I am not sure how to show them in the file manager (Nautilus in GNOME... it'll be somewhere in the settings), but on the command line type:

```
ls -a
```

to show all (hidden and non-hidden) files in the current directory. On the matter of which file you are after, I would say take a look in each one (if you see them when you do "ls -a") and see which matches the tutorial. For the record my .bash_profile file executes my .bashrc file, so it could well end up that either is good.

Oh and if someone tells you to run a command like "ls -a" or "touch .bashrc" and you don't know what it does, run:

```
man ls
man touch
```

first! It will display the man(ual) page for the command and tell you more than anyone will ever need to know about it!

---

### Post by no_ordinary_funace on 2010-05-04
Hi 5th,

I tried your suggestion for both vim and emacs but in both cases I was told to do a "sudo apt-get vim, dummy".  Looks like I got the fun distribution.  Guess I'll add it to the list of stuff to download and study.

I also tried your suggestion re: ls -a and found the .bash_profile, except that there are two of them.  .bash_profile and .bash_profile~.  When viewing both of them are exactly the same, no contents except for my trial script.  Oh well. 

I tried the trial script with .bashrc in nano and after rebooting it worked according to how the tutorial said it should so I'll just go with .bashrc for now and hope that this mysterious .bash_profile will somehow become clear later down the road.

re: man touch...ha ha huh uh huh uh ha hah uh ha....ehhh. *hangs head*. Ok, I'll go read the page now.

---

### Post by th5th on 2010-05-04
> **no_ordinary_funace said:**
> I also tried your suggestion re: ls -a and found the .bash_profile, except that there are two of them.  .bash_profile and .bash_profile~.  When viewing both of them are exactly the same, no contents except for my trial script.  Oh well.

Tilda indicates a backup version. If you mess up the main one use:

```
cp .bash_profile~ .bash_profile
```

That will overwrite your messed up one with the back up.

> **no_ordinary_funace said:**
> [re: man touch...ha ha huh uh huh uh ha hah uh ha....ehhh. *hangs head*. Ok, I'll go read the page now.

Lol. I guess nobody told you about the "love" program. Run "man love" to find out what it does :P

---

### Post by no_ordinary_funace on 2010-05-06
> Lol. I guess nobody told you about the "love" program. Run "man love" to find out what it does

I just get a line saying "no manual entry for love".  I'm not quite sure how to interpret that and feeling more confused than ever. :|  

I suspect that is probably not the "find out what it does" that you were talking about.  Great, is this something ELSE I'm gonna have to download now?  sudo apt get install "man love joke".

---

