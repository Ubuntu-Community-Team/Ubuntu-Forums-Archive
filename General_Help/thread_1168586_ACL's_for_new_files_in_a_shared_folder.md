---
title: "ACL's for new files in a shared folder"
date: 2009-05-24
forum: General Help
---

### Post by SlugSlug on 2009-05-24
Hi 

I have /home/shared with folders and symbolic links that I share with users in the goup 'shared' via ssh. 
My problem is when I add new files or sub directory's they don't inherit the ACL's so i need to keep doing a

$cd /home/shared
$setfacl - R - m g:shared:rx * 

is there a way to make /home/shared always add the ACL to new files and folders? 

Thanks,

---

### Post by bodhi.zazen on 2009-05-24
[http://74.125.155.132/search?q=cache:lQKvhBv-oRQJ:https://tier2.ucsd.edu/t2/index2.php%3Foption%3Dcom_content%26do_pdf%3D1%26id%3D29+linux+shared+directories+with+acl&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.155.132/search?q=cache:lQKvhBv-oRQJ:https://tier2.ucsd.edu/t2/index2.php%3Foption%3Dcom_content%26do_pdf%3D1%26id%3D29+linux+shared+directories+with+acl&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)

or as a PDF : [https://tier2.ucsd.edu/t2/index2.php?option=com_content&do_pdf=1&id=29](https://tier2.ucsd.edu/t2/index2.php?option=com_content&do_pdf=1&id=29)

---

### Post by SlugSlug on 2009-05-24
I tried it again with the -d flag but still not 100% if I create a new folder / file in /home/shared it picks up the g:shared:rx, but if I move a file/folder from /done to /home/shared it doesn't pick up the new ACL's

---

### Post by SlugSlug on 2009-05-25
worked around this with a crontab job 

30 11 * * * setfacl -R -d -m g:shared:rx /home/shared/*

---

