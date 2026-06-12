---
title: "$HOME/.drmc ignored"
date: 2008-12-20
forum: General Help
---

### Post by krayak on 2008-12-20
When I log into Ubuntu, I get an error message (after I put in my password and press enter)
It says
```

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```

I can just press Enter and continue as normal but is there anyways to fix this ?

I tried running these
```
sudo chown -R $USER:$USER $HOME
sudo chmod 644 $HOME/.dmrc
chmod -R u+rwX $HOME
```

but after I put in the 1st one it says
"chown: cannot access '/home/funboat/.gvfs': permission denied"

When I try the 2nd one
"chmod: cannot access '/home/funboat/.drmc': No such file or directory"

and I don't get any message back when I type the last one

---

### Post by cdtech on 2008-12-20
Typo:
> When I try the 2nd one
"chmod: cannot access '/home/funboat/.**drmc**': No such file or directory"

---

### Post by krayak on 2008-12-20
nice catch haha :S
well the last 2 commands worked (1st one still giving me the same error).
and i'm still getting the same error msg when i log in

---

### Post by Nepherte on 2008-12-20
Explanation + solution: [http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

