---
title: "Automatically updated websites using Screem"
date: 2006-08-09
forum: Desktop Environments
---

### Post by not_cool on 2006-08-09
I don't know if this is the right place for this, if so, please move it, or if ubuntuforums isn't the right place could you please tell me a better place.

I have files (.odt) that I would like to save in the /var/www folder and have them automatically linked in my index.html file (which is in the same folder). It would allow me to visit the site and have the files ready for download without doing any html, a big timesaver. Thanks for any help possible. ;)

---

### Post by heikki on 2006-08-09
Well, I think that this isn't right forum to ask this kind of questions but I answer anyway, somebody can move this thread to an another forum.

If I understood your problem correctly, screen isn't good tool to do that. Cron is. I would do a simple cron script that copies these odt-files to /var/www for example daily. Like this:

sudo crontab -e   #We use sudo because we must have write permissions to /var/www
And add something like the following line to the file:
@daily cp /home/you/Documents/file.odt /var/www/ && cp /home/you/Documents/file2.odt /var/www/

And you don't need any kind of automatic linker, just don't make any index-file and you'll see Apache's file list where you can pick the file you want. Or you can make that index.html manually, filenames won't change.

---

### Post by not_cool on 2006-08-09
Thanks! I completely forgot about cron. I'll try that out. And yes, I do know that I don't need to use the index.html file, I just like the looks.

---

