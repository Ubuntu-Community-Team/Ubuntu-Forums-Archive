---
title: "Conky is Killed when I click on unity desktop"
date: 2012-05-17
forum: Desktop Environments
---

### Post by murderd2death on 2012-05-17
I have conky come up automatically as a startup program but anytime i click on the unity desktop the script kills itself and disappears. Its gotten so annoying that I have conky hotkeyed so that I can bring it back up again in case it falls down. I have 12.04, and this has not happened before with any previous distros.

---

### Post by Frogs Hair on 2012-05-17
If you open the .conkyrc there is a section near the top of the syntax that may read as follows.```
own_window_type normal
``` 

You can try some different options here.```
own_window_type conky
``````
own_window_type desktop
``` ```
own_window_type override
```

Remember to save the changes and conky will disappear and reappear after the change has been saved. Test the different options and see if one solves the problem.

---

### Post by jadtech on 2012-05-17
its not gone its hideing :)

i am no script expert by any means  how ever every conky script I have the frist three lines look like this ..

```

own_window yes
own_window_type normal
own_window_transparent yes

```

---

