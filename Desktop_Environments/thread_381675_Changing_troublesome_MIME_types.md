---
title: "Changing troublesome MIME types"
date: 2007-03-11
forum: Desktop Environments
---

### Post by thrope on 2007-03-11
I have a trouble with mime types - but I'm not sure how to rectify it (which files to change etc.) in a stable way (that I won't have to repeat after updates etc.)

The problem is I use Matlab a lot... .m is the extension used for MATLAB source files, but it also seems to be used for objective-c source files. 

Now there is also a Magic for Matlab function files that correctly identifies them as x-matlab. However the magic for normal matlab scripts doesn't seem to identify those.

So I have the situation where Matlab scripts show up as x-objsrc, which is fine, and I can have them open in gVim on a double click. However Matlab functions show up as x-matlab (because of the magic looking for function definition) and when I try to double click I get the following error:

> The filename "recloop.m" indicates that this file is of type "Objective-C source code". The contents of the file indicate that the file is of type "MATLAB script/function". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MATLAB script/function", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

How can I fix this, either by removing Objective-C mime type from the system (I don't need it), making magic override the filename or something else?

Any advice greatfully received.

I did try commenting out the .m filename suffix for the objective-c type in  /usr/share/mime/packages/freedesktop.org.xml and then running update-mime-database, but it didn't seem to make any difference.

Thanks,

---

### Post by thrope on 2007-03-11
Resolved this - removing/commenting the x-objsrc glob did work, I just had to restart Nautilus! Doh!.

---

