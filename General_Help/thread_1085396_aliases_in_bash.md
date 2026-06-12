---
title: "aliases in bash"
date: 2009-03-03
forum: General Help
---

### Post by erichlund on 2009-03-03
At work, my primary shell is csh, and I use the following to start nedit in the background, opening the list of files I give as a parameter (e.g. n .bashrc .profile):

```
alias n "nedit \!* &"
```

It took a long time to find this in the BASH man page:  

```
There is no mechanism for using arguments in the replacement text.  If argu&#8208;
       ments are needed, a shell function should be used (see FUNCTIONS below).
```

Who knew...

Anyway, this works:

```

function n()
{
   LANG=en_CA.ISO-8859-1
   nedit $@ &
}

```

I've seen others that seem to be experiencing similar problems with parameters in bash.  Hope it helps...

---

### Post by handy on 2009-03-03
I asked the mod's to move your thread into the how-to's sub-forum, as that is where it should be.

Maybe you could come up with a more appropriate title for the how-to OP?

---

