---
title: "mime-type is only being (incorrectly) inferred by file extension."
date: 2008-04-19
forum: Desktop Environments
---

### Post by BrownCoal on 2008-04-19
Hi. I have a second partition that I mount only every so-often. When I browse through a folder with mixed contents, the 'Type' column only changes to the correct type when I highlight a file. This means that before I can sort by the type column I must first highlight over every file one-by-one by holding the down arrow. This doesn't seem right. In addition, when I leave the folder and then return to it, the 'Type' column data has not been retained, and I must go over them again. 

Basically it is inferring a files mime-type based on its extension. When the file is selected the file is then assessed based on its actual *content*, but then it isn't stored anywhere, so the next time I visit the folder it goes back to inferring its mime-type by its extension.

This has a nasty little side-effect of changing what you have highlighted when you sort by the 'type' column, as it changes when you select it, but nautilus only tracks the highlight position, not the the name of the file. Here is a separate post detailing the issue (sadly from way back in 2005!): [http://ubuntuforums.org/showthread.php?p=290562#post290562](http://ubuntuforums.org/showthread.php?p=290562#post290562)

I am finding this to be a particularly bad usability problem. Can anyone help with this problem?

---

