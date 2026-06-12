---
title: "how do i connect to another router?"
date: 2009-06-04
forum: General Help
---

### Post by chriskin on 2009-06-04
a friend of mine needs help with some options in the router's page and i can't get to his house to see what he means (i mean, i am in a different town)
i know that one can connect to another router if he knows the ip, yet i don't know which ip to ask him for. he gave me the external ip, which i thought to be the more logical choice, but firefox just won't load the page, am i missing something here?

---

### Post by john183 on 2009-06-04
Yes it is possible to connect to a router across the internet, but the option must be enabled on the router first. Most routers ship with this option disabled by default for security reasons. Have you friend make sure that it is enabled and then try again. Also, most routers also require that the default password be changed before you can enable the remote access feature. And you were correct when using the external IP of his router. if you try to use one of the internal ones (192.168.*.*) you won't be able to connect. The IP that you need is the one that his ISP provides to his router.

---

### Post by Legace on 2009-06-04
His router probably has NAT (firewall), which is blocking you for secuirity reasons.
You could download the manual for that router, and it should contain images to help you.
Or you could ask him to send screenshots of the configuration pages.

You could also ask your friend to enter **your** external IP into "Remote Management" if he has such an option [so that NAT won't block you] :)

---

### Post by chriskin on 2009-06-04
i guess i will go with the "send screenshots" solution, it is just not worth the trouble 

thanks for the answers :)

---

