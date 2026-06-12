---
title: "howto make subdomains"
date: 2008-12-09
forum: General Help
---

### Post by dxlwebs on 2008-12-09
hey all,

i own a few domains and i am thinking on making a network of sites and on each sitei will do a few thingsso i need sub-domains but i have no idea on where to start i have looked around and tried a few thingsbut nothinghas helped!

could some one let me know on how i am suppost to do this like astep by step guide 

also if i own 1 domain like example.com do i have to buy more domains like test.example.com as well for the sub domains ? i really don't know what to do so ifsomeone can help please doo!

thank you for your time

---

### Post by hyper_ch on 2008-12-09
(1) you can't "buy" test.example.com. if you register example.com it is in your liberty to create subodmains at will.

(2) how to create them... hmmm... what have you setup this far?

---

### Post by dxlwebs on 2008-12-09
i made a virtural host under the name of test.example.com and directed it to the folder needed but nothing changed i would really like to know how i would do it from scratch as i deleted itafter it was not working

thank you for your quick reply

---

### Post by hyper_ch on 2008-12-09
(1) depending on your dns entry you first will have to create one for the subdomain
(2) you will need to create a virtualhost in your webserver also

---

### Post by dxlwebs on 2008-12-09
ok so i set it up andthis is what i have done
i am doing through webmin so it doesnt show virtural host parts but the rest is normal
virtural host!
> ServerName blog.gamemasterx.com
DocumentRoot /home/dxlwebs/blog.gamemasterx.com
ServerAlias blog.gamemasterx.com [http://blog.gamemasterx.com](http://blog.gamemasterx.com)

and dns
Name Server:  	blog.gamemasterx.com. 	Default 	blog.gamemasterx.com.

Address (1):  	blog.gamemasterx.com. 	Default 	127.0.0.100

so im not sure what im doing wrong  but it still comes up with address not found

---

### Post by hyper_ch on 2008-12-09
I don't know webmin but first check the dns settings. What's the output of:

```

dig gamemasterx.com
dig blog.gamemasterx.com
nslookup gamemasterx.com

```

Then also check if you get errors in the apache log file.

---

