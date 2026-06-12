---
title: "No internet after installing"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Trinity24 on 2005-06-04
Distro is up and running successfully, except for that I have no internet. Only other distro I've had running with DSL was FC3 and in that case I just set the modem up and running along with the account that Verizon gave me and I was on the 'net. 

I've set everything up just like normal, except when I try to pull Verizon.com or google.com I recieve a timeout error. 

Are things different with ubuntu? Do I have to do a config somewhere else to set up dsl with a Westell Versalink modem?

I'd be greatful for any answers as I'm w/o internet at the moment and am at the public library right now :D.

I'm very much happy with this product, I'd like to continue with it... just need some internet here...

Thanks,
Trinity

---

### Post by Curlydave on 2005-06-04
There's a command that lets you set up a PPPoE connection. I was surprised myself that it's not in the menus.

Just note that because you can't set up PPPoE on install, there will be no connection, and Ubuntu will write some files wrong and not set things up right. (eg your hosts file will be bugged up)

---

