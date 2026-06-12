---
title: "How to run .sh"
date: 2009-02-19
forum: General Help
---

### Post by necronzero on 2009-02-19
So i want to run my PS3 media server on Ubuntu, i already installed java, but now i can't get the .sh file to run, it just opens a notepad...
How do i get it to run?

---

### Post by emshains on 2009-02-19
You must make it executable. You can do that by right clicking the file, then selecting "Permissions". Then, check the box that are under "Execute".
You could also do that by running this command:
```
chmod +X [file]
```

I think it was the right command, but I can't tell for certain. 

Then you should be able to run it.

It should also be runnable by the command:
```
sh [file] 
```

Please remember, that if you have just started the terminal, you will be "located" at /home/[user]/.

---

### Post by mb_webguy on 2009-02-19
The correct command in the terminal for making it executable would be "chmod u+x *filename*".  This adds ("+") executable privileges ("x") for the user ("u").

---

### Post by overlord.gaurav on 2009-02-19
Open a Terminal. Navigate to the directory where the file is. (suppose the file is on the desktop)
```
cd Desktop
```

To run the file, just do:
```
sh filename.sh
```

---

### Post by punx45 on 2009-02-19
or ```
./script.sh
```   that way it will run in whatever shell the script calls for.   not sure what happens if you tell sh to run a script that is intended for a different shell.

---

