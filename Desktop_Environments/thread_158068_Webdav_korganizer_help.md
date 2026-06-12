---
title: "Webdav korganizer help"
date: 2006-04-10
forum: Desktop Environments
---

### Post by mfyahya on 2006-04-10
I'm trying to set up korganizer to work with webdav on an ubuntu server. I've set up the server with ssl and webdav modules after reading howtos on this forum. So far I have it working when I download from a cal.ics file in the webdav directory, but I get an 'Access was denied while attempting to upload ' error when I attempt to save the calendar.  I looked at Apache's access log and it shows 500 status for PUT requests:

63.227.107.193 - yahya [10/Apr/2006:16:04:08 +0000] "GET /webdav/yahya/cal.ics HTTP/1.1" 200 666 "-" "Mozilla/5.0 (compatible; Konqueror/3.4; Linux) KHTML/3.4.2 (like Gecko)"
63.227.107.193 - yahya [10/Apr/2006:16:10:48 +0000] "PUT /webdav/yahya/cal.ics HTTP/1.1" 500 675 "-" "Mozilla/5.0 (compatible; Konqueror/3.4; Linux) KHTML/3.4.2 (like Gecko)"

I tried setting 777 permissions recursively to my webdav directory but still get that error. I can't figure out what is wrong. Thanks for any help.

---

### Post by mfyahya on 2006-04-11
Never mind, figured it out. It was because I hadn't made a symlink inside /etc/mods-enabled pointing to /etc/mods-available/dav_fs.conf

---

