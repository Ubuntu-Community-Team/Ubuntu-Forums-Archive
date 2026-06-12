---
title: "Simple Apache question..."
date: 2006-08-29
forum: Desktop Environments
---

### Post by recklessray on 2006-08-29
hi, i installed drupal, php, and msql on my home sever yesterday. its all working fine but i need to make apache serve it up. currently it is making the /var/www/apache-default/ directory publicly accesable. i need to point it at localhost:/drupal? im not sure. also, i cant for the life of me find the right part of apache2.conf to edit  - am i missing someting? 

so, my question is: where in the apache2.conf is the bit i need to edit to make drupal the default site?

and, when i do find the right bit of the apache2.conf - what do i write?! is it /etc/drupal ? or something like that? ive checked the forum and there is a fantastic howto about drupal installation, but it doesnt mention the apache2.conf  file.

any help is very gratefully received :)

ray

---

### Post by az on 2006-08-29
Just change the document root in your
/etc/apache2/sites-available/default

Or leave it as is and then enable the reditect match to point to that drupal folder.

---

### Post by recklessray on 2006-08-29
great, thanks for the advice -thats where i was going wrong  - was looking in apache2.conf not the sites available. well, you learn something new every day ;)

cheers.

---

