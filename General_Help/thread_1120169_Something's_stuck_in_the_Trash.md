---
title: "Something's stuck in the Trash"
date: 2009-04-08
forum: General Help
---

### Post by sidewalkcynic on 2009-04-08
I got a folder in my Trash that I cannot remove to change the permissions to delete it from Trash. It was a sub-folder of ndiswrapper.

Anyway, when I navigate as Root, I cannot find the Trash to change the permission.

Anybody know where the Trash is?

---

### Post by benj1 on 2009-04-08
yeah its at

~/.local/share/trash/files

---

### Post by coffeecat on 2009-04-08
For an ordinary user:

/home/username/.local/share/Trash

There are two folders in there: 'files' and 'info'.

---

### Post by aysiu on 2009-04-08
You can use coffeecat's suggestion to change the permission there.

Or you can also paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.local/share/Trash
```

---

### Post by sidewalkcynic on 2009-04-08
The Terminal script didn't work, but the directory charts did.

Thanks, I been putting it off for a couple of months, and forgot about it, and finally, I decided to empty my trash after three months, and it was still there.

But not any more....

---

### Post by coffeecat on 2009-04-08
> **sidewalkcynic said:**
> The Terminal script didn't work

How exactly did it not work? aysiu's terminal code would have reset the permissions for everything in your Trash folder to your ownership. It wouldn't have deleted anything.

---

### Post by rage9 on 2009-04-09
Whenever I have run into that problem I just open the terminal, and navigate to the directory:

```
cd ~/.local/share/Trash/files
```

And then use sudo rm -r fileORfolderName

---

