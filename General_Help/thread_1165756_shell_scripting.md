---
title: "shell scripting"
date: 2009-05-21
forum: General Help
---

### Post by Elviswind on 2009-05-21
Okay, I tried running the following script as a work around for an issue in World of Warcraft:

```
#!/bin/bash
xset r on
wine wine /home/myname/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
xset r off

```

This script starts up wine and world of warcraft just fine, but the xset commands don't execute.

Then I found another example and it worked perfectly:

```
#Wow.sh
xset r on
wine wine /home/myname/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
xset r off

```

In this case, I understand that the first line isn't anything other than a comment.

Well, I've just been reading about shell scripting to get this thing to work and it seems like every example out there has some variation of #!/bin/bash as the first line.  So why didn't it work correctly in this case?

Links to tutorials or detailed explanations of this situation would be appreciated.

Thanks.

---

