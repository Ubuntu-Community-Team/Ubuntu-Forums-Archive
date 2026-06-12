---
title: "Konsole history problem"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Peter Alien on 2005-05-11
Hello,

I'm having a problem with Konsole v1.5 in Ubuntu 5.04.

The problem is that i cant clean Konsole's history, even when i click in the Clear History or Clear all Histories options in the Konsole Menu.

Does anyone know how to clean it ?

When i enter History command it gives me 173 for me as a user and 212 as Root.


Many thanks in advanced.

---

### Post by wwwolf on 2005-05-11
[QUOTE=Peter Alien]Hello,

I'm having a problem with Konsole v1.5 in Ubuntu 5.04.

The problem is that i cant clean Konsole's history, even when i click in the Clear History or Clear all Histories options in the Konsole Menu.
Many thanks in advanced.[/QUOTE]

Find the file .bash_history and rename it to .bash_history.bak
This should give you a clean fresh start. If you just change the permissions of that file instead it will still not allow Konsole to clear it. Better to just rename or delete it and be done with it.

HTH,

---

### Post by Peter Alien on 2005-05-11
Ok it's clean :) many thanks


So... the Clear History and Clear all Histories options in the Konsole Menu doesnt work ?

Is it a bug ?

---

### Post by wwwolf on 2005-05-11
[QUOTE=Peter Alien]Ok it's clean :) many thanks


So... the Clear History and Clear all Histories options in the Konsole Menu doesnt work ?

Is it a bug ?[/QUOTE]

Well, if it hasn't been reported yet, it has now...
Bug 105502: konsole does not clear history

EDIT: Well, aparently i was mistaken...or misled:

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
------- Additional Comments From thiago kde org *2005-05-12 04:37 -------
Sorry, you've been misled. The Clear (All) History is to remove the buffer of lines output to Konsole, the one you can scroll on using the scrollbars.

It does not and cannot affect shell history.

You can re-file this as a wish, if you want.
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Oh well   :?  ](*,)  :?

---

