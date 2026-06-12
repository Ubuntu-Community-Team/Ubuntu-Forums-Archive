---
title: "copy paste problem in terminal"
date: 2006-10-30
forum: Desktop Environments
---

### Post by windstory on 2006-10-30
this is for ubuntu 6.10.

the problem happens when i open a terminal (either gnome-terminal, xterm, or konsole), cat a text file (e.g., a shell script file), select one line, and paste it in an editor (or in the terminal). If the line i selected is long, therefore is shown as two lines in the terminal window, the paste just split the line into two separate lines in the editor. But I just need them in a single line as it is in the file.

I confirmed that paste works as expected if text selected is from an editor or web browser, it is not editor's problem, it is not a particular terminal application problem. I have another ubuntu 6.06 box which doesn't have this problem. The settings for terminal applications are the same. Then I didn't know what to do.

Any suggestions?

---

### Post by windstory on 2006-10-30
Mostly solved!

The problem only happens when I use command "more" to list file content. There is no problem with "cat" or "less".

Still confused why my other ubuntu box doesn't have the problem with "more".

---

