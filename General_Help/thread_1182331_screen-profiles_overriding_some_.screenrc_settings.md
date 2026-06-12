---
title: "screen-profiles overriding some .screenrc settings?"
date: 2009-06-08
forum: General Help
---

### Post by Zxaos on 2009-06-08
I was hoping for some help with screen and the screen-profiles packages. Since installing 9.04, I've been happily using screen with the new profiles (after some tweaking). However, since beginning to use screen-profiles, I've found that my .screenrc is being ignored. Specifically, in my .screenrc I have a line
```
term screen-256color
```
This lets screen play nicely with vim. However, if screen loads a profile, this line does not run (or if it does run, it then gets replaced) since $TERM gives me 'screen' and not 'screen256'. If I rename the .screen-profiles folder, my $TERM is set correctly but I (obviously) don't get the functionality provided by the profiles.

The final line in the profile is
```
source $HOME/.screenrc
```

How do I get screen to continue using profiles but to not ignore my .screenrc file?

---

### Post by justleen on 2009-06-09
I think you need to edit the actual profiles? there are some symlinks in your home dir, pointing to the screen-profiles profiles.

---

