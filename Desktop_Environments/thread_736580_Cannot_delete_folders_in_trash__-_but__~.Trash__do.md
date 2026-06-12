---
title: "Cannot delete folders in trash://  - but  ~./Trash  doesn't exist?"
date: 2008-03-26
forum: Desktop Environments
---

### Post by marcadams on 2008-03-26
Hi All;

I'm running Heron Beta.

When I open the trash folder from the desktop, I see several folders.

I cannot delete them via the GUI (empty deleted items, nor delete the folder directly) - I get permission denied.

I tried 
sudo rm -rf ~/.Trash/* 

Only to realise, the ~/.Trash folder, doesn't actually exist.
When I look at the location of the files, it just tells me there are in trash://

How can I remove these???

Much appreciated !

---

### Post by marcadams on 2008-04-01
Any ideas - I still haven't found a solution to this?

Many thanks

---

### Post by jon9314 on 2008-04-04
i have the same problem could it be a bug?

---

### Post by marcadams on 2008-04-06
FYI - I eventually tracked down where the trash folder in Heron is :

~/.local/share/Trash/files$ 

Deleting the files from here, solved the problem.

---

### Post by kwaanens on 2008-04-12
I've been beating myself over the head on this. I couldn't anything with the locate command either.
I consider this a step back with regards to the user experience.
Thanks for finding my cure anyway!

---

### Post by vgrisham on 2008-04-12
> **kwaanens said:**
> I've been beating myself over the head on this. I couldn't anything with the locate command either.
I consider this a step back with regards to the user experience.
Thanks for finding my cure anyway!

The relocation of the trash file messed up the trash applet in Avant Window Navigator as well. I guess we have to keep in mind that Hardy is still a beta.

---

### Post by magnusbb on 2008-04-12
Has anyone heard an explanation for this change? I find it pretty counter-intuitive, but if there is a good reason...

And a big thanks for providing a solution.

---

### Post by gertdorn on 2008-05-13
I have now the same problem.
Ubuntu 8.04  - the Hardy Heron - released in April 2008.
I see trash:/// but i have no rights to delete. But i cant find the folder in filesystem.
 All folders and files inside have 40777 or 41777 as oktal and i can't change it with chmod as su.

What can is do ist now 10gb  and i need the space.

thanks Gert

---

### Post by meganox on 2008-05-13
```
# rm -rf ~/.local/share/Trash/files
```

I don't know what ~/.local/share/Trash/info is for.

I believe I read somewhere that the empty trash command is non-functional in 8.04 LTS.

Personally I always really delete files using the "Include a Delete command" preference in nautilus.

---

