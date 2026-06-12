---
title: "How: Gnome terminal always in front?"
date: 2009-05-18
forum: General Help
---

### Post by O-pos on 2009-05-18
Hello,

How could I make it so that gnome terminal always remains in front of all the other windows?

Thanks in advance,

O-pos

---

### Post by mikewhatever on 2009-05-18
Open a terrminal window, right click on the title bar and select 'Always on top'.

---

### Post by O-pos on 2009-05-18
Thanks, wow, I did not thing about that.

Gnome terminal has a function to retrieve older commands with pressing buttion "up". I would like to keep some of the really usefule ones, but delete the otheres (especially after trying to do something unsuccessfully, lot of trash gets saved in the terminal). How is it possible to delete them?

---

### Post by Confuseling on 2009-07-16
I guess just type 'history' and copy out the ones you want to keep.

Does anyone know how to make gnome-terminals open with the always on top attribute set?

[EDIT - solved - see below]

I've tried using devilspie

```

~/.devilspie$ cat gnome-terminal.ds 
(if
  (is (application_name) "gnome-terminal")
  (begin
    (above)
  )
)

```

but it doesn't appear to do anything - I'm running compiz, which may well be why.

Any ideas please?

EDIT:

Aha! Barking up the wrong tree - it's doable in compizconfig, 'window rules' plugin.

Cheers.

---

