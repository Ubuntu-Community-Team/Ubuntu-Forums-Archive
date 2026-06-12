---
title: "Thin client server"
date: 2009-03-01
forum: General Help
---

### Post by Comzee on 2009-03-01
I want to run a thin client server on my spare box I have laying around. Unfortunately I can't find any tutorials on how to do it. I don't care what Ubuntu based variant Linux distro I use for this.

Just to to clarify, I want to set it up so I can use the "network boot" option with any computer on my network to connect to the thin client server. Making any computer on my network a possible thin client.

If somebody could point me in the right direction that would be great. Thanks in advance for any reply's :-).

---

### Post by bodhi.zazen on 2009-03-01
Sweet :)

I suggest you take a look at Edubuntu. Their documentation will walk you through the set up. Later, if you want to change to another distro you will get a sense of what it entails.

Edubuntu is Ubuntu with a few (minor) modifications, so you can change the look and feel if you like.

[http://edubuntu.org/Documentation](http://edubuntu.org/Documentation)

If you get stuck or have questions post 'em here :)

---

### Post by Comzee on 2009-03-01
Since I already had a fresh install of Ubuntu 8.10 on my server-box I opted to try it instead of installing edubuntu. I followed a pretty old tutorial here [https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")  . I understood most of it except part 1.-3/4. Everything in the tutorial worked for me and all software installed correctly. I went to one of my box's and booted using PXE, and it found my dhcp server on my server box. IT loaded the Linux kernel, and the normal loading screen for Ubuntu came up and went for about 6 second than just went to a blank screen. It does this for all my computers when I network booted them.

It's apparently suppose to bring up a login screen, unfortunately it never does. I tested the ssh-server on my server-box too and it works. So I'm wondering if I need to set some graphics options or something for my thin-client-server. 


Any help would be more than greatly appreciated. There's so little documentation on this that it's hard to find information for troubleshooting this stuff. I don't even know where to start.

---

### Post by bodhi.zazen on 2009-03-01
Good work so far ;)

Well, as I indicated, one "advantage" of edubuntu is that installing edubuntu (on the server) will set all this up automatically.

Looking at the page you referenced, step 3 is used if you are running a firewall on the server. By default your firewall *should* be disabled. Did you enable ufw or some other firewall ? If so you need to allow the connections in step 3.

Step 4 is for NFS. Did you install / configure NFS on the server ?

The edubuntu documentation is IMO the best source of information.

They have changed the format a little and navigation through the pages is not intuitive , but ...

[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook)

And from that page, here is the page on thin clients:

[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient)

On that second page are several links to more specific information.

Your other option, as I indicated, is to simply install the edubuntu (server) and clinets on the desktop. edubuntu is designed to set up everything for you automatically.

You would then at least have a working system you can refer back to if needed.

---

