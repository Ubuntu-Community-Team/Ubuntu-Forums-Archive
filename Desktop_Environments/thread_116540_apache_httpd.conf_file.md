---
title: "apache httpd.conf file"
date: 2006-01-12
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-12
i know were it is well i think i do

ect/apache2/httpd.conf

but wen i do try and edit it all it has is this

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

thts it and i also tried

sudo gedit ect/apache2/httpd.conf

but that made no diff so were is the proper 'httpd.conf' file cuz it realy shuld have 100's of lines of stuff in it

---

### Post by amohanty on 2006-01-13
I believe Apache2 uses the apache2.conf file which includes the httpd.conf file via an include directive.

It should be in the same directory as httpd.conf

HTH

---

### Post by ESPOiG on 2006-01-13
thx ill have a look

---

