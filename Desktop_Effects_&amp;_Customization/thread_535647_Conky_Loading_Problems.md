---
title: "Conky Loading Problems"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by sekazi on 2007-08-26
I have tried to find a solution but couldnt. The problem I am having deals when Ubuntu starts. I have 3 scripts which I want to start but it seems only 1 starts. The command I am using on the startup programs is 

conky && conky -c .conkyrc2 && conky -c .conkyrc3

When ubutnu starts only .conkyrc3 starts and the rest does not.

The other issue I am having is when the 1 starts it has a shadow and it shouldnt. I have tried to set conky to start 10 seconds after but it does not work.

My .conky_start.sh has the following

#!/bin/bash
sleep 10 && conky && conky -c .conkyrc2 && conky -c .conkyrc3'

I have already run chmod a+x on it and it does not seem to work.


Any solutions?

---

### Post by sekazi on 2007-08-27
I forgot I had to load the script at the startup and fixed that. Now I have another issue.

When the script loads it only loads the first item from the list and nothing else until I exit out of that program. I have 4 embedded terminals and 3 conky items loading.

My first script I did for this was 

```
#!/bin/bash
sleep 20 && gnome-terminal --window-with-profile=trans1 && sleep 1 && gnome-terminal --window-with-profile=trans2 && sleep 1 && gnome-terminal --window-with-profile=trans3 && sleep 1 && gnome-terminal --window-with-profile=trans4 && sleep 1 && conky -c .conkyrc && sleep 1 && conky -c .conkyrc2 && sleep 1 && conky -c .conkyrc3;
```

my second was

```
#!/bin/bash
sleep 20 && gnome-terminal --window-with-profile=trans1;
sleep 1 && gnome-terminal --window-with-profile=trans2;
sleep 1 && gnome-terminal --window-with-profile=trans3;
sleep 1 && gnome-terminal --window-with-profile=trans4;
sleep 1 && conky -c .conkyrc;
sleep 1 && conky -c .conkyrc2;
sleep 1 && conky -c .conkyrc3;
```

If I run the script from a terminal it works perfect but on startup it refuses to load everything but the first item on the list.

---

### Post by MrNormS on 2007-09-01
I think you're using && instead of &.  && means "run this next thing if the last one returned successfully" whereas & means "Start that last thing then immediately go on and start this thing too.

---

