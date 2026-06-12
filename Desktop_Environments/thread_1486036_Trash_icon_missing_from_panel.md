---
title: "Trash icon missing from panel"
date: 2010-05-17
forum: Desktop Environments
---

### Post by stoneage on 2010-05-17
Ubuntu 9.10 64 bit

I restarted and all my Desktop shortcuts were rearranged(I normally have 'Keep Aligned' unchecked) and the Trash icon was gone from the bottom panel. 

Now every time I restart the Desktop shortcuts default to 'Keep Aligned' and I can't re-add the Trash icon to the top or bottom panel.

Tried also adding a third panel, but can't add Trash icon to that either.....

Any suggestions?


EDIT - Configuration Editor for trashapplet:-
[ATTACH]157281[/ATTACH] [ATTACH]157288[/ATTACH]

If I select Deleted Items in Nautilus I get "Sorry, could not display all the contents of "trash": Operation not supported", and the situation is the same for my other user.
Places -> Computer = "Nautilus cannot handle "computer" locations."


Hmmmm..... this could be worse than I first thought, It also doesn't mount any external usb drives - now I'm worried.... Help...?




EDIT 2 - ok, I have found the cause. It is related to installing a non-repo version of glib while compiling Gimp. I don't know the easy way to fix it, but I should be able to sort it one way or another. 

 ```
sudo mv /usr/local /usr/local.old
``` 
```
sudo mkdir /urs/local
``` and restarting seems to have resolved everything. 

Suggestions still welcomed... :)

---

### Post by rahul_bhise on 2010-10-14
thanks. this solved my problem
i was having the same problem

---

