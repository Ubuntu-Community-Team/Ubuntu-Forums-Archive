---
title: "SSH server and windows myentunnel help please :D"
date: 2009-03-31
forum: General Help
---

### Post by jigglywiggly on 2009-03-31
Ok so I have a ssh server that I setup in ubuntu(Runs in a virtualbox vm). It's pretty basic but anyway, it works and all I can connect to it and it's all great. But howcome on a windows pc I use myentunnel does not seem to work with IE? Like ok, so I have internet explorer 8 on a windows computer, with myentunnel running, I enable dynamic socks proxy and I connect to my server, it works and everything great. I go on a windows computer > I go to internet options > connections > lan settings > use a proxy server for you lan, I put 127.0.0.1 and I put the port as 7070. It should work right? Well it doesn't D:
When I go to a website all I get is Internet explorer cannot display the weppage. Any ideas?

Btw all I did to start the ssh server was # sudo apt-get install openssh-server openssh-client
[img]http://img5.imageshack.us/img5/9469/12869339.jpg[/img]

---

### Post by jigglywiggly on 2009-03-31
Firefox seems to work, just not IE and chrome because chrome uses ie's bs.

---

### Post by jigglywiggly on 2009-03-31
Oh wait I got it in IE, had to delete everything except SOCKS, http and all of those I had to leave blank.

---

