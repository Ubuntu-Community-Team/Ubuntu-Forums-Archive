---
title: "Lost .evolution directory"
date: 2009-02-27
forum: General Help
---

### Post by jorisctn on 2009-02-27
Before reformatting the disc of my wife´s PC I thought to secure here data by copying her /home directory to another PC in our home network (both PC´s running Ubuntu Intrepid). I didn´t check the precise contents of the copied /home but found the .evolution directory (and other .xxx dir´ s) missing from the copy :confused: (view hidden files is ON).
Since I´m new to Ubuntu I´m afraid I did something stupid and would be happy if anyone out there could explain to me where things went wrong.

Thanks in advance for your help.

---

### Post by geirha on 2009-02-27
How did you copy? With nautilus? terminal? 

If you copied using the terminal, do you remember what command you ran?

---

### Post by jorisctn on 2009-02-27
I copied with Nautilus. I just dragged the complete /home directory to a new empty directory on the target PC

---

### Post by geirha on 2009-02-27
As root (gksu nautilus) I assume? That should've copied all the hidden files and directories as well. I don't use evolution myself, but it might be it stores its configuration under ~/.config/evolution instead of ~/.evolution ... could that be the case?

---

### Post by jorisctn on 2009-02-27
I was working in the GNOME graphical environment, with administrator permissions, but didn´t start Nautilus as root from a terminal. 

On the target PC I searched for .evolution to make sure that it didn´t land somewhere else as you suggest. There were no .xxx directories at all copied (so .config wasn´t there either) but there were some files .xxx (not directories) in the copied /home.

---

### Post by geirha on 2009-02-27
You where running with her user when you copied then? so nautilus had read access to all files under her home folder...

I just tried creating a folder with a hidden folder and hidden file inside. Then I copied that folder to a new folder by Ctrl+dragging it, and both the hidden folder and file was copied in the process. I'm using Hardy, but I doubt they've changed that functionality for Intrepid ... try the same experiment in Intrepid and see if you get the same result.

---

### Post by jorisctn on 2009-02-27
I don´t remember if I used her ID in the proces, but I would expect a warning that I didn´t have permission for the action in case I used my ID.

I agree with you that it is unlikely that Intrepid differs from Hardy in this case.

Then I repeated your experiment and at first trial, with an empty hidden file in the hidden directory the system said  ¨operation not supported by backend¨ with the suggestion to skip this action. Then I entered some text in the file and after that everything went as it should.

In the proces of copying her home directory there might have been some instances where the system also reacted with ¨not supported..¨ and where I have skipped files without knowing what I was throwing away.

I want to thank you for paying attention to my silly problem and don´t think there is anything wrong with Intrepid in this case. Also I don´t want to waist more of your time.

At least I learned that nautilus can be run as root with gksu. Until now I only knew about sudo [command] ...

Thanks again,
Joris

---

