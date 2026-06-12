---
title: "chmod question"
date: 2009-06-01
forum: General Help
---

### Post by lucifuge on 2009-06-01
When I installed Ubuntu i made my 2nd HD  have a mount point of /mydata. I now want to make a  symbolic link this but i noticed that that the "link" option is greyed out. I took this as a permissions issue.
I entered the following in terminal hoping to fix it but it didn't anyone tell me why?

sudo chmod -R 777 /mydata

---

### Post by mcduck on 2009-06-01
> **lucifuge said:**
> When I installed Ubuntu i made my 2nd HD  have a mount point of /mydata. I now want to make a  symbolic link this but i noticed that that the "link" option is greyed out. I took this as a permissions issue.
I entered the following in terminal hoping to fix it but it didn't anyone tell me why?

sudo chmod -R 777 /mydata

What link option is greyed out? If you mean the one in Nautilus right-click menu that would create the link in the same directory whre the original is (and you definitely don't have permission to write anything into /).

If you want to do that from Nautilus, drag the directory with middle mouse button into where you wish to create the link, and you'll get a popup menu asking if you want to copy, move or link.

Or use the "ln -s"-command to create the link from command line:
```
ln -s /mydata /path/to/link
```

---

### Post by lucifuge on 2009-06-01
I've been @ssing around in desperation and I've somehow changed the group permission to me, 'brett', when it should be 'root'  How do i change the group back to 'root'?

---

### Post by oakdeveloper on 2009-06-01
Use the below command to change the group to root:

```
sudo chgrp root <filename or directory>

sudo chgrp -R root <directory>
```Use the second option if you want to recursively change the group permission to root

---

### Post by lucifuge on 2009-06-01
Thanks oakdeveloper.
-----------------------------------------------------------------------------
The syntax is throwing me, specifically the usage of '/path/to/link'

ln -s /mydata /path/to/link
if i understand right, would this work:

ln -s /mydata /home/brett/mydata

(...or is /mydata appended automatically and it should be

 ln -s /mydata /home/brett  

and it will create   /home/brett/mydata)

---

### Post by oakdeveloper on 2009-06-01
Where have you mounted the 2nd HD ?  Is it directly under root as your have mentioned, i.e., /mydata or is it mounted under /media directory? Check that and issue the command as follows

```
ln -s /mydata /home/brett/mydata           #for the first option
ln -s /media/mydata /home/brett/mydata     #for the second option
```

---

### Post by mcduck on 2009-06-01
> **lucifuge said:**
> Thanks oakdeveloper.
-----------------------------------------------------------------------------
The syntax is throwing me, specifically the usage of '/path/to/link'

ln -s /mydata /path/to/link
if i understand right, would this work:

ln -s /mydata /home/brett/mydata

(...or is /mydata appended automatically and it should be

 ln -s /mydata /home/brett  

and it will create   /home/brett/mydata)

if you want the link to appear as /home/brett/mydata then the command would be this:
```
ln -s /mydata /home/brett/mydata
```

---

### Post by lucifuge on 2009-06-01
yes, it was the first option!  and it works cheers all!

if I ever want to remove the symbolic link, does the data residing in /mydata remain safe ?

---

### Post by oakdeveloper on 2009-06-01
Of course! You can remove the link and still have the data residing in /mydata safe.

---

