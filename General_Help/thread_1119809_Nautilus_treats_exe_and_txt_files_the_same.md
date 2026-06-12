---
title: "Nautilus treats exe and txt files the same"
date: 2009-04-08
forum: General Help
---

### Post by mojiz on 2009-04-08
Hi

I have a problem with Nautilus with some filetypes.
Nautilus uses same program to open/execute none related files.

When I choose to open .exe or .bat files using wine, Nautilus changes the .txt and .ini and some other files with wine too.

Now if I try to revert the txt files back to gedit, then Nautilus uses gedit to launch bat and exe files.

I thought it's a problem with /etc/mime.types but it wasn't there.

How should I fix this?


Thanks
Mojiz

---

### Post by 3Miro on 2009-04-08
That is odd, there is a menu under KDE that lets you manipulate the "file association", however, I don't seem to be able to find that under Gnome. It should be somewhere.

Probably .txt and .exe are considered in the same "group" so they are associated with the same program.

---

### Post by matrixblue on 2009-04-08
Right-click the exe file and go to properties. Under the Open with Tab select Wine Program Loader.

This should make wine open all exe files from now on.

---

### Post by mojiz on 2009-04-08
> **matrixblue said:**
> Right-click the exe file and go to properties. Under the Open with Tab select Wine Program Loader.

This should make wine open all exe files from now on.

I know but wine will be used to open txt files too. THAT is the problem :(

---

### Post by mojiz on 2009-04-09
Any more ideas?

---

### Post by pbpersson on 2009-04-09
> **mojiz said:**
> Any more ideas?

Would you not go through the same steps to define Gedit to open all files with the TXT file extension?

---

### Post by chriskin on 2009-04-09
if you care to install ubuntu tweak from [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads) it has a way to give specific commands to each file type

---

### Post by mojiz on 2009-04-09
> **pbpersson said:**
> Would you not go through the same steps to define Gedit to open all files with the TXT file extension?

Maybe I haven't explained it correctly.
I do the exact steps to define for gedit for txt files and wine for exe files but each time I change the default program for each file, It changes the same program for other file type too.

So actually I have to use the same program to open txt and exe files.(Either gedit or wine)

---

### Post by mb_webguy on 2009-04-09
> **mojiz said:**
> Maybe I haven't explained it correctly.
I do the exact steps to define for gedit for txt files and wine for exe files but each time I change the default program for each file, It changes the same program for other file type too.

So actually I have to use the same program to open txt and exe files.(Either gedit or wine)
What is the mimetype given for the exe files?  Right-click an exe and go to Properties, and on the Basic tab, look at the Type entry.  The mimetype will be the part in parentheses.  Linux looks at the mimetype and not the file extension when determining the filetype and what to do with it.

---

### Post by mojiz on 2009-04-09
> **chriskin said:**
> if you care to install ubuntu tweak from [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads) it has a way to give specific commands to each file type

This one seems to help

Thank you Chriskin :)

---

### Post by mojiz on 2009-04-09
> **mb_webguy said:**
> What is the mimetype given for the exe files?  Right-click an exe and go to Properties, and on the Basic tab, look at the Type entry.  The mimetype will be the part in parentheses.  Linux looks at the mimetype and not the file extension when determining the filetype and what to do with it.

Before installing the Ubuntu Tweak exe files had the same mime types as txt files. They both had either the plain/text or the application/x-ms-dos-executable type.
Now each one have a different mimetype

---

### Post by chriskin on 2009-04-09
> **mojiz said:**
> This one seems to help

Thank you Chriskin :)



glad to help, tell us if it worked :)

---

### Post by mojiz on 2009-04-09
Yes it did. 
Thank you for your help

---

### Post by chriskin on 2009-04-09
glad to have been able to help :)

check the rest of the app as well, it can make some miracles happen:)

---

