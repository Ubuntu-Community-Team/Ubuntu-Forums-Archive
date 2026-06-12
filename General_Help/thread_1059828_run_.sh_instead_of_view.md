---
title: "run .sh instead of view"
date: 2009-02-04
forum: General Help
---

### Post by Andreas1 on 2009-02-04
hi there...
i have a .sh script in my home folder and in the properties of the file i already checked "run as program"
when i want to start that script from the ALT+F2 dialog it is opened in gedit instead of being run. how can i change that behavior?

---

### Post by binbash on 2009-02-04
chmod +x filename.sh

then at alt f2 or terminal  : 

sh /home/username/aasdasdasd.sh

---

### Post by Andreas1 on 2009-02-04
> **binbash said:**
> chmod +x filename.sh

then at alt f2 or terminal  : 

sh /home/username/aasdasdasd.sh


i think the checkbox to run as program did the chmod +x, repeated it anyway

what i made different is i simply typed "script.sh" and nothing else.
i am sure this already worked on a previous install. it was very useful because the name was auto-completed.
now that i think of it the thing that was different and always made me wonder was why the first entry in the context menu of a .sh script would be "open with wine", why is making having wine installed a difference how shell scripts are treated?

btw if i had to do it by typing the full path it wouldn't be of much use, so should i install wine(!) again or is there another way?

---

### Post by mb_webguy on 2009-02-04
The "Open With" settings in the desktop environment don't have any effect on the console, except the command "gvfs-open", which opens a file or folder with the default application.

If a file is executable, typing the name of the file should be sufficient to run it, *providing* that your user account has permission to execute the file and the file is in the current directory or in the user's path (which is why it's common to create a bin directory in a user's home directory to store scripts, since that is in the default path).  And of course it helps if the file is a script or otherwise something that *can* execute...

---

### Post by Andreas1 on 2009-02-04
> **mb_webguy said:**
> The "Open With" settings in the desktop environment don't have any effect on the console, except the command "gvfs-open", which opens a file or folder with the default application.

If a file is executable, typing the name of the file should be sufficient to run it, *providing* that your user account has permission to execute the file and the file is in the current directory or in the user's path (which is why it's common to create a bin directory in a user's home directory to store scripts, since that is in the default path).  And of course it helps if the file is a script or otherwise something that *can* execute...

the file is in my home directory, i created it there, i own it, i marked it to be executeable and if i click on it in nautilus it is executed.

if i put it in ~/bin it is not found, or did i get this wrong about having a bin directory in my home directory?
i dont want to type the full path, only "script.sh", which works if it is in my home directory, but it opens it in gedit

Edit: if the "Open with" settings don't affect this i have no idea what is different from my previous install where i just created the file, marked it executeable and ran it the way i am trying to now. :(

---

### Post by mb_webguy on 2009-02-04
Could you post the script itself, as well as the output of "ls -lsa ~/bin" (assuming the file is in the bin directory)?

---

### Post by Andreas1 on 2009-02-04
online.sh

```
#!/bin/sh

skype &
pidgin &
mail-notification &
```

i use this instead of autostart apps because i have to manually connect to the internet first, just to explain

and about the ~/bin directory, i created /home/andreas/bin, put the script there, then ALT+F2 "online.sh": dialog box saying "file:///home/andreas/online.sh" could not be found, so such file or directory
anyway, here is ls of ~/bin:
```
insgesamt 12
4 drwxr-xr-x  2 andreas andreas 4096 2009-02-04 20:51 .
4 drwxr-xr-x 43 andreas andreas 4096 2009-02-04 20:52 ..
4 -rwxrwx--x  1 andreas andreas   48 2009-01-09 18:35 online.sh

```

but as i had it before, it worked out of /home/andreas anyway

---

### Post by mb_webguy on 2009-02-04
Ah...  Try removing the file extension.  For some reason the run dialog wants to open .sh files rather than run them, but removing the extension results in them being executed as intended.

---

### Post by Andreas1 on 2009-02-04
> **mb_webguy said:**
> Ah...  Try removing the file extension.  For some reason the run dialog wants to open .sh files rather than run them, but removing the extension results in them being executed as intended.

didn't work. gedit again ](*,)


Edit: it works if i type ./online.sh

still, i find that some weird behavior: if i run "online.sh" i can view it in gedit and if i run "./online.sh" it is executed.

---

### Post by mb_webguy on 2009-02-04
After you removed the .sh extension, did you try running it with "online" or "online.sh"?  Also, do you have the script in your home directory and your bin directory, or just the bin directory?  I put the script, with the .sh extension removed and the correct file permissions applied, in my bin folder, and I could run it from the run dialog with "online" just fine.

---

### Post by Andreas1 on 2009-02-04
so far i tried
```
online    in home, run "online"     resulting in gedit
online.sh in home, run "online.sh"  resulting in gedit
online.sh in bin,  run "online.sh"  resulting in error no such file
```

now i tried
```
online    in bin, run "online"      script is executed!
```

although i find that behaviour a bit weird i am glad i have what i want now, thank you for your patience!

---

### Post by Andreas1 on 2009-02-04
um, shouldn't i be able to mark this thread as solved? i can't find the option under thread tools...

---

### Post by anjilslaire on 2009-02-04
Jst an FYI,
its normal behavior to have to use
```

./

```
in front of .sh files to run them

so ```

./online.sh

```
isn't strange behavior in any sense.

Weird about the Solved issue. "Thanks" disappeared a while back too...

---

### Post by mb_webguy on 2009-02-04
> **Andreas1 said:**
> so far i tried
```
online    in home, run "online"     resulting in gedit
online.sh in home, run "online.sh"  resulting in gedit
online.sh in bin,  run "online.sh"  resulting in error no such file
```

now i tried
```
online    in bin, run "online"      script is executed!
```

although i find that behaviour a bit weird i am glad i have what i want now, thank you for your patience!

It doesn't look to me like you're actually removing the .sh extension from the file.  Try "mv online.sh online" in the terminal from the directory in which the file is located (or just rename it in nautilus), then just type "online" to run it.

---

### Post by Andreas1 on 2009-02-05
> **mb_webguy said:**
> It doesn't look to me like you're actually removing the .sh extension from the file.  Try "mv online.sh online" in the terminal from the directory in which the file is located (or just rename it in nautilus), then just type "online" to run it.

oh, sorry, i just used code tags to have a table with fixed font here, this is not code, i did remove the extension in nautilus.

---

### Post by alhague on 2010-01-31
I have had the same issue. 
Andreas1, You helped me a lot in resolving that!
AFAIK it's enough to call the script like this: ```
./script-name
```
Sounds like SOLVED to me.

---

