---
title: "Starting ubuntu with a script"
date: 2009-06-07
forum: General Help
---

### Post by stevetorrefranca on 2009-06-07
How do I accomplish the following 

1. At startup the server downloads some libraries from a remote repository (scp)
2. after downloading, the server fires up the web server (/etc/init.d/tomcat start)

BTw this is an Ubuntu Server Edition on a public cloud.  we want to turn on and off cloud servers on demand.  But first it has to update itself with the current lib/jars

I was thinking of using user-data ([http://alestic.com/2009/06/ec2-user-data-scripts](http://alestic.com/2009/06/ec2-user-data-scripts)) but maybe there is a simpler way. 


- Steve
[http://www.brewsoftcorp.com](http://www.brewsoftcorp.com)

---

