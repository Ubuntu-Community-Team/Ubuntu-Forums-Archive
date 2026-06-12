---
title: "Wolfenstein: Enemy Territory"
date: 2009-08-14
forum: Gaming &amp; Leisure
---

### Post by Sticks_uk on 2009-08-14
Where can I download this game please lads ?

It is free right ?

---

### Post by Gregz on 2009-08-14
Yes totally free here's a few

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=4cm&q=enemy+territory+linux&revid=633729615&ei=Zv2FSr-4JcHClAf2muWCBQ&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=3](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=4cm&q=enemy+territory+linux&revid=633729615&ei=Zv2FSr-4JcHClAf2muWCBQ&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=3)

or here

[http://returntocastlewolfenstein.filefront.com/file/;14408](http://returntocastlewolfenstein.filefront.com/file/;14408)

---

### Post by Jpardue on 2009-08-14
Wolfestein rocks I can't get enough of this game, a classic

---

### Post by Perfect Storm on 2009-08-15
...and here's a guide; [http://gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gwos.org/doku.php/guides:64bit:et_wolfenstein) Just ignore "before installation" section if you're using 32-bit

---

### Post by Sticks_uk on 2009-08-15
EDIT: How do I uninstall this game please ? I think I know what I did wrong :)

---

### Post by Perfect Storm on 2009-08-15
Depends how you install it.
If you did like in theguide;

```
cd /usr/local/games
sudo rm -rf enemy-territory
cd /usr/local/bin
sudo rm -rf et

```

Note you might want to delete the $user settings/folder of ET for complete removal. (check hidden files in your home directory)

---

### Post by Sticks_uk on 2009-08-15
> **Artificial Intelligence said:**
> 
[/code]Note you might want to delete the $user settings/folder of ET for complete removal. (check hidden files in your home directory)

where would I find that folder please ? 

and yeah I followed that guide to the button but think I clicked play on the installer :( 

thanks btw :)

---

### Post by Perfect Storm on 2009-08-15
Open your file-browser and set it to see "hidden files". Hidden files are files/folders with **.** (dot) infront of their names. These files save your personal settings etc.
Just find the ET one and delete it. It might have superuser permission as you started ET up with the installtion launcher. If you delete thsi folder you don't need to erease ET from your computer.

---

### Post by Sticks_uk on 2009-08-15
yeah this is the problem I was having before you mean the .etwolf folder ? 

it has a padlock over it and says cannot be deleted to wastebasket

---

### Post by Perfect Storm on 2009-08-15
It's due to permission problem made by launching the game with superuser do (sudo) - launching the game from the installtion window.

To delete it;

```

cd
sudo rm -rf .etwolf
```

NOTE: be careful with the **rm** commands, using it wrong can do great damage.

---

### Post by Sticks_uk on 2009-08-15
thanks just restarted the machine after all that.

will start again and let you know how it went. :)

I am still stuck in windows mode and just follow pictures :confused:

EDIT: All is well thanks AI just dunno what server to play on now :)

---

