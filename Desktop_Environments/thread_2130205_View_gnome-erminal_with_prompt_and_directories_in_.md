---
title: "View gnome-erminal with prompt and directories in color"
date: 2013-03-28
forum: Desktop Environments
---

### Post by c.pfarher on 2013-03-28
Hello, I would like to have the terminal prompt and directories in gnome-terminal in colors.... I configured the .bashrc and when I open with the nautilus script (right click in a folder in nautilus and select the option ¨open in terminal¨) was fine, it´s shown in color... but when I open other terminal (for example through ctrl+t or through the dash of unity), it isn´t showing in color? any idea? it is something like .bashrc don´t affect that 

Thank you.

---

### Post by markbl on 2013-03-28
You say you "configured the .bashrc", what did you do?

The default ubuntu installed ~/.bashrc includes a "force_color_prompt" variable but it is commented out. Remove the comment char. That default ~/.bashrc also sets up directory colors etc. If you have stuffed up your ~/.bashrc then copy back the default with cp /etc/skel/.bashrc ~

---

