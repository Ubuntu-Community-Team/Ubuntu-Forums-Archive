---
title: "setting up virtual host with apache"
date: 2009-04-19
forum: General Help
---

### Post by cyclobs on 2009-04-19
hey guys, 

no clue if this is the right place not quite sure on where to go for this.

ok so i want to set up a web server with virtual host so i can run more then one website off my pc. i've looked around on the net but gets confusing and didn't really work.

ok i want to set up my apache so that it has 2 virtual host.

1 is the normal localhost thing where it will go to /var/www where i want to keep all of my sites (if it's possible)

and the other is atm is something i'm working on and want to host to the rest of the world. i already have a domain name which is distorted-mentality.kicks-***.net and i want people to be able to access that without seeing the /var/www directory (so when someone types in the name it will go to the virtual host where the folder is /var/www/distorted mentality)

if you understand that....

so i've looked around on the net and i followed this little guide but for anyone on the outside world it would show /var/www where for me it showed "/var/www/distorted mentality". i also tried to just use localhost to see if it would go to /var/www but it kept going back to the distorted mentality site.

so if anyone still follows me at this point.... how can i set apache up to do what i want? is it possible?

---

### Post by aaronp on 2009-04-19
> **cyclobs said:**
> hey guys, 

no clue if this is the right place not quite sure on where to go for this.

ok so i want to set up a web server with virtual host so i can run more then one website off my pc. i've looked around on the net but gets confusing and didn't really work.

ok i want to set up my apache so that it has 2 virtual host.

1 is the normal localhost thing where it will go to /var/www where i want to keep all of my sites (if it's possible)

and the other is atm is something i'm working on and want to host to the rest of the world. i already have a domain name which is distorted-mentality.kicks-***.net and i want people to be able to access that without seeing the /var/www directory (so when someone types in the name it will go to the virtual host where the folder is /var/www/distorted mentality)

if you understand that....

so i've looked around on the net and i followed this little guide but for anyone on the outside world it would show /var/www where for me it showed "/var/www/distorted mentality". i also tried to just use localhost to see if it would go to /var/www but it kept going back to the distorted mentality site.

so if anyone still follows me at this point.... how can i set apache up to do what i want? is it possible?

The default setup of apache will look straight into /var/www whenever someone access the machine via http on the correct port.
Someone having their request for a website routed to your IP address sees exactly the same as you see when you type localhost - that is, whatever is in /var/www.

Essentially, where you have your 'second' site setup (as a sub-directory of /var/www) is [http://localhost/foldername](http://localhost/foldername).
So from the outside world with apache set up like this you would need someone to type [http://www.xxxxxx.net/foldername](http://www.xxxxxx.net/foldername) to get to your '2nd' site.

With only one public ip address (essentially your WAN IP address) it seems like it may be difficult to serve two separate pages off the same server because no matter what routing rules you can set up inside your machine or LAN, when someone types your public IP they get the default page depending on your config.

---

