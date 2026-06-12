---
title: "File opens in 2 buffers in gVim"
date: 2006-09-01
forum: Desktop Environments
---

### Post by seanf on 2006-09-01
On Dapper, when I open a file in gVim using the context menu, the file is opened in 2 buffers.

Buffer #1 shows the file as 'file:///home/user/myfile.txt'
Buffer #2 shows the file as '~/myfile.txt'

Any idea as to how I can get the file to open in a single buffer, preferably using the path in buffer #2 above?

---

### Post by obadiah on 2006-10-12
There's some sort of weird issue with the way GVim opens files from the graphical menu. You can get around this by making your own "opens with" entry as follows:

1. Right click on a text document and select properties from the pop-up window.

2. Remove the default GVim options

3. Click the Add button and select "Use custom commande"

4. Enter gvim in the use custom command text box then click add

Then when you go to open a text file use your new custom command to open up gvim.

---

### Post by seanf on 2007-07-17
Thanks, but that does nothing to address this problem.

---

