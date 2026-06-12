---
title: "How to tell Nautilus that realplayer files are not text files"
date: 2005-12-17
forum: Desktop Environments
---

### Post by patis on 2005-12-17
Hello,

I installed realplayer on my Ubuntu 5.10. It runs well. However, from Nautilus I notice the following:

1. Realplayer files, with name extension .rm, are automatically associated with the icon of a speaker with music notes around it. That's pretty good.

2. Double-clicking on the .rm files gives me the following warning (following which all I can do is cancel the operation):

    The filename "ayed051209.rm" indicates that this file is of type
    "RealAudio broadcast". The contents of the file indicate that the
    file is of type "plain text document". If you open this file, the file
    might present a security risk to your system.

    Do not open the file unless you created the file yourself, or 
    received the file from a trusted source. To open the file, rename
    the file to the correct extension for "plain text document", then
    open the file normally. Alternatively, use the Open With menu
    to choose a specific application for the file. 

3. I right-click on the .rm file, select properties->Open_With and it gives me the option:

   Select an application to open ayed051209.rm and other of type
   "plain text document"

If I select "Realplayer 10" then .rm files are opened with Realplayer, as expected, but also *all* text files, even those with extension .txt!
And of course, if I select the text editor then the .rm files are opened
with it :???: 

So, how do I "train" Nautilus to do the proper thing with .rm files? How do I modify the MIME-type definitions for this file type?

Thanks,

---

