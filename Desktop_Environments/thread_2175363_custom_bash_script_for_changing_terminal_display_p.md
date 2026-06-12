---
title: "custom bash script for changing terminal display parameters"
date: 2013-09-18
forum: Desktop Environments
---

### Post by captainentropy on 2013-09-18
I recently figured out how to change the features of the bash terminal (e.g. changing the color of the font, alias, prompt, etc.) so I created this script, customBash.sh which I could use to change the display

```
#!/bin/bash
#This script changes the prompt for the session. 
export PS1="\[\033[36m\][\u@\h:/\W]$ "
echo $PS1
```

It used to work, sort of. The color was a nice shade of green and the info before the prompt just showed the last part of the directory path (sometimes the path would be really long pushing the prompt to the far right side of the window. But it doesn't work at all any more. Well, the echo part does because it displays the PS1= part of the script after I run the script, but the color and path part doesn't work. I haven't upgraded the OS if that matters (I'm using 12.04 LTS).

Any ideas why this stopped working?

---

### Post by VMC on 2013-09-18
Edit ".bashrc" file instead. Somewhere around line#57 is the PS options.

---

### Post by steeldriver on 2013-09-18
I think the issue is that *export *sets the value for *sub*shells - to set the value in the parent shell you need to **source** your script - either

```
source ./customBash.sh
```
or
```
**.** ./customBash.sh
```

FYI, if you just want to limit the length of the path that's displayed, you can set the PROMPT_DIRTRIM environment variable

```
export PROMPT_DIRTRIM=2
```

```

       PROMPT_DIRTRIM
              If set to a number greater than zero, the value is used  as  the
              number of trailing directory components to retain when expanding
              the \w and \W  prompt  string  escapes  (see  PROMPTING  below).
              Characters removed are replaced with an ellipsis.

```

---

### Post by captainentropy on 2013-09-19
@VMC, I forgot to mention that the only reason I didn't edit the .bashrc file was I wanted to retain the ability to easily switch to other schemes if I wanted to. I have another script that reverts the terminal back to the default setting.

@steeldriver. D'oh. That's what I forgot to do (source ./customBash.sh). Now it works again. I just hadn't closed the terminal I was working in for so long I forgot that part, hahaha. Thanks for the PROMPT_DIRTRIM suggestion too. That will be handy.

---

