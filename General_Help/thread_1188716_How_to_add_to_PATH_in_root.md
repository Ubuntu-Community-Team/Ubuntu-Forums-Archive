---
title: "How to add to PATH in root?"
date: 2009-06-16
forum: General Help
---

### Post by pat13nc3 on 2009-06-16
Hi, I've been learning a bit about BASH lately
And like many others I put my scripts in /home/<myuser>/bin
And updated my PATH to read scripts from there

I have one particular script that requires I'm logged in as root
However, I realized that while logged into root, 
It doesn't recognize my edited PATH
And thus my scripts don't work without the full location

Is this because the PATH is different for root?
Do I need to edit the PATH for root?
And if so how would I go about doing this?

---

### Post by bigboy_pdb on 2009-06-16
Edit the '.bashrc' file under '/root'

You can add:
```

PATH="$PATH:dir"

```

---

