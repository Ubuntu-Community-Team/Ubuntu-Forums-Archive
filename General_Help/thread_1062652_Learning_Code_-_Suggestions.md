---
title: "Learning Code - Suggestions?"
date: 2009-02-07
forum: General Help
---

### Post by horizonuser on 2009-02-07
I am still fairly new to Linux and still trying to find my way around things. However, I would like to start learning a programming language and I would specifically like to write an application that does the following:

- Redirects all network traffic to a web page for authentication
- Have the authentication page authenticate against a very usually backend source (I will need to write this myself as this doesn't exist in the wild!)
- If validated write the MAC address and allow a couple of ports access through iptables.
- Log all this info.

I know a lot of this can be done already with various other solutions, but the authentication does not exist in open-source.

Having said all of that, would anyone recommend the best language to look at to write this? This is a side project for me so if it takes my 5 years to write it, so be it. Also, I don't want to "lift" anyone else's code as I would like to write it all myself. 

I am thinking PHP cause it seems to be able to deal with sockets and also manipulate iptables.

---

### Post by mb_webguy on 2009-02-07
I think PHP would be a good choice.  It integrates easily and well with web servers and html, it's easy to learn and easy to use, and I know that it is capable of doing everything you just said.

Other languages would work as well, and in fact you may end up using more than one language to get the job done.  At least some of your code is going to be running as an independent application.  Many people would use something like Python for that, but PHP can do it as well with the PHP CLI (command-line interpreter).

---

