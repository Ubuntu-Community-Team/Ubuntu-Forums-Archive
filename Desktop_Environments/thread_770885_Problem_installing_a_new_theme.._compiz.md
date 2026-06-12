---
title: "Problem installing a new theme.. compiz"
date: 2008-04-27
forum: Desktop Environments
---

### Post by JZeFF on 2008-04-27
I went here [http://www.gnome-look.org/content/show.php/Gray+Dark+Ice+Emerald+Theme?content=73173](http://www.gnome-look.org/content/show.php/Gray+Dark+Ice+Emerald+Theme?content=73173)

And downloaded that theme to my desktop.. when i try to extract it, it gives me this message  "Could not open "GrayDark-Ice.emerald"

Archive type not supported."

Any ideas?

---

### Post by isaacj87 on 2008-04-27
I'm assuming you have Emerald properly installed...so with that...

Just go System->Preferences->Emerald Theme Manager

Then click "Import" and choose the file. Let me know how it goes :)

---

### Post by JZeFF on 2008-04-27
hmm... i guess i do not have Emerald installed?

I know for a fact i have compiz fusion set up and running properly.. but can someone please give me the code to install emerald?  maybe that will fix the problem...

---

### Post by isaacj87 on 2008-04-27
> **JZeFF said:**
> hmm... i guess i do not have Emerald installed?

I know for a fact i have compiz fusion set up and running properly.. but can someone please give me the code to install emerald?  maybe that will fix the problem...

I'm assuming...

```
sudo apt-get install emerald
```

should do the trick!

---

### Post by fk4n on 2008-04-27
> **JZeFF said:**
> hmm... i guess i do not have Emerald installed?

I know for a fact i have compiz fusion set up and running properly.. but can someone please give me the code to install emerald?  maybe that will fix the problem...

Here is the command to install emerald:

sudo apt-get install emerald
sudo apt-get install emerald-themes

You may need to install one of the compizconfig-setting-manager as well.

sudo apt-get install compizconfig-settings-manager

---

### Post by newbreed on 2008-04-27
whats better? compiz fusion or Emerald? and do they work on Hardy? Also what is sudo command to get these set up? sorry, noob here.

---

### Post by fk4n on 2008-04-27
as far as I know, emerald is just a theme loader. sudo is a command to help none root user to do work as a root. Basically you put "sudo" infront of the command you want to use, and it will execute as you are the root of this machine.

---

### Post by newbreed on 2008-04-27
ok.. getting some where, thanks 
So your saying that I need Emarld?...and Compiz is a a group, sort of, themes?.. any idea what commands I need to get these two to work together?

---

