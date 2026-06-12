---
title: "Help with permisions"
date: 2009-04-14
forum: General Help
---

### Post by TravisthePirate on 2009-04-14
I have a external hard drive and im trying to transfer movies on to it but it says i don't have permision..ive tried chmod +x ~/home/brightjoker/Videos -R but it didnt do anything and now i can't even access the folder because i think i locked it up

---

### Post by bhishan on 2009-04-14
did you try 
sudo nautilus
and then copying it from there

---

### Post by TravisthePirate on 2009-04-14
im doing that now for my music, but i locked my videos folder and it says i can view anything in it....how do i unlock it

---

### Post by JC Cheloven on 2009-04-14
May be a matter of ownership of the folders or files. Try

chown -R <your_user_name> <your_destination_folder>

(please read in chown --help if you're in doubt)

Note: you can check who is the owner of a file simply with ls -l.

---

### Post by Primefalcon on 2009-04-14
> **bhishan said:**
> did you try 
sudo nautilus
and then copying it from there
it'd probably be better to graphical sudo
```
gksudo nautilus
```

---

### Post by TravisthePirate on 2009-04-14
once i type in those the window opens but i cant find any of the files that i want to move...and my videos folder is still blocked

---

### Post by TravisthePirate on 2009-04-15
so i got all my files ready and are able to transfer..it think but now when i try to put something on my external HD it says it is  "read only" any ideas how to change it??

---

### Post by Primefalcon on 2009-04-15
I'm guessing your not a cli person so I'll say this in the graphical way

right click said files and select permissions and adjust the permissions for yourself/others/all

---

