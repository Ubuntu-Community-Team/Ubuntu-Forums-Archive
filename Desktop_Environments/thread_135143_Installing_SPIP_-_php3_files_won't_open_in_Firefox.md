---
title: "Installing SPIP - php3 files won't open in Firefox"
date: 2006-02-23
forum: Desktop Environments
---

### Post by Garyu on 2006-02-23
I want to try out SPIP on my web server, but they have named their files ".php3" instead of ".php" and this makes Firefox confused, so when I enter the adress to a ".php3"-file to try and install SPIP I get a "Open with..." dialog box. 

I tried renaming the file to ".php" instead but then I also have to change all references in the file and remove the "3" from the file name. When I do this, everything works fine, but SPIP has 648 files (not all of them .php3, but still a lot of work). How can I make this work without changing file names?

NOTE: My domain is hosted on a server that is not mine. Hmm... Is this a server setting that needs to be fixed? I hope not, because that means trouble...

EDIT: Downloaded SPIP files from
[http://www.spip.net/en_download](http://www.spip.net/en_download)
I know it is available through the repositories, but as I said, my domain is hosted...

---

### Post by lamego on 2006-02-23
You can change the apache php module configuration to be able to identify .php3 as php files:
I am using php5 with apache2, you can change the configuration at:
```
/etc/apache2/mods-available/php5.conf
```

---

### Post by Garyu on 2006-02-23
So it is a server issue then? Because in that case I don't think I can change it... :(

---

### Post by lamego on 2006-02-23
Yes, it is a server configuration. If you can't ask the server admin to change this you will need to change all the files to .php and run some script to look for the #includes and replace inside the files...
I am not that much expert with scripting to help you on this...

---

