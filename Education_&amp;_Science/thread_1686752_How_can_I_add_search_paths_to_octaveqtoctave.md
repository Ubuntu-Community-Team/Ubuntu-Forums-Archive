---
title: "How can I add search paths to octave/qtoctave?"
date: 2011-02-12
forum: Education &amp; Science
---

### Post by KIAaze on 2011-02-12
Hi,

How can I add search paths to octave/qtoctave so that it finds scripts outside the current working directory?

edit: Also, how can I access the home directory? I tried "~" and "$HOME", but keep getting an error message.
reedit: Found "tilde_expand("~")" and "getenv("HOME")".

---

### Post by hugmenot on 2011-02-13
Add them to your .octaverc

addpath ("/home/hugs/Mod_2010/src/HeadMex", "-begin");

savepath works too:

```
octave:2> help savepath
`savepath' is a function from the file /usr/share/octave/3.2.4/m/path/savepath.m

 -- Function File:  savepath (FILE)
     Save the portion of the current function search path, that is not
     set during Octave's initialization process, to FILE.  If FILE is
     omitted, `~/.octaverc' is used.  If successful, `savepath' returns
     0.

     See also: path, addpath, rmpath, genpath, pathdef, pathsep
```

---

### Post by PC_load_letter on 2011-02-15
or from the Octave terminal (for some reason this never worked from QTOctave), say the directory I want to add is **/home/mike/mfiles**, then from gnome-terminal, type "octave", and you get the octave prompt type: ```
octave:1> addpath(genpath("/home/mike/mfiles"))
octave:2> savepath
```

Now, restart Octave and type:```
octave:3> path
``` to make sure the folder has been added. The gen path, IIRC, makes sure that the subfolders in .../mfiles (at the time the command was performed) are also included in the path. If you create any subfolders in the future, then you'll have to repeat the above instructions. 

Hope this helps.

---

