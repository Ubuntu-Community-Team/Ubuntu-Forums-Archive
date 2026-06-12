---
title: "incorrect chars in man pages..."
date: 2008-07-04
forum: Desktop Environments
---

### Post by Michael G Nielsen on 2008-07-04
my setup is:
- dedicated ubuntu server 8.04 dk keyboard set up to use uk language.
- winxp with putty ssh login. 

Normally i use putty and ssh to login. So I have not checked if the same problem is on the server terminal window, but I expect it to be. 

when I type man cvs (example):

5 pagedown writes:

admin
   Administration
       Â· Requires: repository, working directory.

       Â· Changes: repository.

       Â· Synonym: rcs

it should be:

admin
   Administration
       o Requires: repository, working directory.

       o Changes: repository.

       o Synonym: rcs

does anyone know how to correct this? Other man xxx have the same problem.

regards Michael

---

### Post by Michael G Nielsen on 2008-07-04
I have corrected the error when using putty by exporting:

export LANG=danish
export TERM=linux

this is added to the file ~/.bash_aliases

for some reason when using putty, the TERM=xterm is set.

I have checked the terminal on the dedicated server which works fine before the 2 exports above. It has the TERM=linux set by default.

regards Michael

---

