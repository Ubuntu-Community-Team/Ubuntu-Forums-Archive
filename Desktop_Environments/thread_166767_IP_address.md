---
title: "IP address"
date: 2006-04-27
forum: Desktop Environments
---

### Post by vidak on 2006-04-27
Well, this might seem a lame question... How can I get my (real) IP address?
If I want to get it using ifconfig, or ControlCenter, I get a fake one.

Any ideas?
:confused:

---

### Post by derjames on 2006-04-27
Hi there

try this web adddress, it gives you useful information about your IP address

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

cheers

---

### Post by louis_nichols on 2006-04-27
[http://www.whatsmyrealip.com](http://www.whatsmyrealip.com)

is this what you're looking for?

---

### Post by vidak on 2006-04-28
[QUOTE=louis_nichols][http://www.whatsmyrealip.com](http://www.whatsmyrealip.com)

is this what you're looking for?[/QUOTE]

isn't there some command line-thing to solve the problem?

---

### Post by louis_nichols on 2006-04-28
Well... depends on what you think the problem is. If the IP you're seeing on the site I posted is different from the one ifconfig is showing you, it means you are behind a [NAT]("http://en.wikipedia.org/wiki/Network_address_translation"), and that's not something you can control, unless you are the administrator of the whole network.

What do you need all this info for? Perhaps we can find a workaround.

---

### Post by stoeptegel on 2006-04-28
[QUOTE=vidak]isn't there some command line-thing to solve the problem?[/QUOTE]

You could telnet or browse into your router yes.

---

### Post by vidak on 2006-04-28
The weird thing is that it used to work eg a month before. I mean, I could get my IP address with ifconfig. The interesting part is, that I get the _same_ address, no matter in what network the laptop is.

---

### Post by louis_nichols on 2006-04-28
[QUOTE=vidak]The interesting part is, that I get the _same_ address, no matter in what network the laptop is.[/QUOTE]

That's not weird at all, if your address is statically configured. It's actually stored in a file on your pc. IP only changes when it is assigned dinamically, through dhcp. What would be kind of weird is if you were able to access the internet from several networks using the same IP. Although that's doable, if the IP's are private and enabled in all networks.

---

### Post by vidak on 2006-04-28
[QUOTE=louis_nichols]That's not weird at all, if your address is statically configured. It's actually stored in a file on your pc. IP only changes when it is assigned dinamically, through dhcp. What would be kind of weird is if you were able to access the internet from several networks using the same IP. Although that's doable, if the IP's are private and enabled in all networks.[/QUOTE]

it's set to DHCP of course, that's why I called it weird :) 
If I use the SystemSettings dialog, and delete the IP address from the 'Manually' (configured network) field (it's still set to dhcp), after restarting network, I get back that fake number...
](*,)

---

