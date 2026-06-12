---
title: "download webpages"
date: 2006-09-21
forum: Desktop Environments
---

### Post by azleam on 2006-09-21
hello 

lets say I have a list of urls 
I want to open them in a web browser one by one 
then click ctrl+s and save the full webpages 

but this procedure is time consuming ofcourse

do you know any program that can do that? 

it must support cookies, form logins or whatever else, and just save them as if I saved them manually in the web browser 

PS:
I have tested wget but cant make it work 
I set it to download a list of urls, but it didnt saved the full webpage, some files (graphics and who knows what else) are missing, using wget -i urlist 

thanks

---

### Post by lagagnon on 2006-09-21
wget should do it. You probably forgot to use the -r switch which recursively gets all subdirectories. Read man wget.

---

### Post by Tomosaur on 2006-09-21
You'll need a browser extension if you want to get web-pages only accessible after a login. Wget does not have this capability (as far as I know). Firefox may have an extension capable of doing what you want, but I am unaware of any.

---

### Post by martal on 2006-09-21
Take a look at the Fx extension Scrapbook.

---

