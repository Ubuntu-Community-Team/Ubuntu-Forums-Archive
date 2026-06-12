---
title: "How to setenv, unsetenv, set path in ubuntu 8.10"
date: 2009-01-05
forum: General Help
---

### Post by lecycliste on 2009-01-05
I'm not an ubuntu or Linux geek (used to use unix about 25 years ago, and used Red Hat a little last year), but need to install an app in 64-bit ubuntu 8.10.

In ubuntu 8.10:

How do I access a bashrc file?

What are the equivalents to setenv and unsetenv?
In other words, how do I set and unset environment variables?

I tried to run this script using   source ./gsim_setup.csh:
#
setenv GEMINI_ROOT ~/gsim_release/gemini-root
# Gsim needs to use nptl libpthread library
unsetenv LD_ASSUME_KERNEL

set path=($GEMINI_ROOT/bin $path)
if !($?LD_LIBRARY_PATH) then
  setenv  LD_LIBRARY_PATH $GEMINI_ROOT/lib
else
  setenv  LD_LIBRARY_PATH $GEMINI_ROOT/lib":$LD_LIBRARY_PATH"
endif

I got these errors:
bash: setenv: command not found
bash: unsetenv: command not found
bash: ./gsim_setup.csh: line 6: syntax error near unexpected token `('
bash: ./gsim_setup.csh: line 6: `set path=($GEMINI_ROOT/bin $path)'

How do I make this work?

Thanks.

---

### Post by Ahadiel on 2009-01-05
.bashrc resides in your home folder.

---

### Post by lecycliste on 2009-01-07
OK, found bashrc by unhiding all files in my home dir (just like Windows - YUCK!). 

Now, how do I add setenv command to bash?

And what's a good resource for figuring out scripts like the one in my original post? 

I'm somewhat familiar with Python and C.

This script has commands and syntax not recognized by bash in ubuntu 8.10.

---

