---
title: "VPN woes - no repository anymore for pptpconfig and I need to use VPN conection"
date: 2005-12-13
forum: Desktop Environments
---

### Post by tentimes on 2005-12-13
Hi,

I'm pretty new and finding it impossible to set up VPN to findnot.com using ubuntu. Main reason is I cannot get a working version of pptpconfig! The repository links given at the bottom of this post have missing Quzl repositories. The pptp installed by default has no front end, and I just cannot figure out how to get this VPN tunnel working on my new linux box.

I would be really really grateful if someone could point me in the right direction here.

The address for the VPN connection is vpn11.findnot.com, I have my username and password. I simply want to be able to setup a VPN stream for amule/bitorrent (or the whole box if thats simpler) so I can download stuff encoded.

Please note it is sensitive stuff for me personally, it's not pron!

Thanks for any help :)

---

### Post by alamba on 2005-12-14
One way can be to install webmin from symantec and then use that to configure and use pptp vpn connections. I'm doing that to manage pptp vpn connections both on my ubuntu server end and on my ubuntu laptop.

Akshay

---

### Post by gilgongo on 2005-12-14
Do you mean James Cameron's PPTP GUI? If so I'm using that no problem with Breezy. Put the following in your /etc/apt/sources.list file:

# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

Then do "sudo apt-get refresh" then "sudo apt-get install pptpconfig" and you've got it.

To set it up on the desktop (or as a App in the menu bar) give the launcher command as "gksudo pptpconfig" 'cos is needs to be run as root.

---

### Post by alamba on 2005-12-14
Sorry...I meant synaptic and symantec.

Akshay

---

### Post by schilcha on 2005-12-14
There's a short but sufficient howto at the [pptp-project-page]("http://pptpclient.sourceforge.net/howto-debian.phtml")

---

### Post by tentimes on 2005-12-14
I've already put the line ino for James Camerons thingy, there are actually two lines, one is for php stuff. It won't ibnstall - says missing files.

I've gone through the guide as well, all the way to editing chap_secrets ppp stuff, etc.

I have a lot of repsitories enabled (univers etc), but only JAmes Camerons site has the gui. This is where I can no longer get it from, so really I was hoping for an alternative.

I will try the webmin thing - was looking at it but didn't realise that it was client too - that's good :)

I'm in work now, but will write a reply when I have tried it out. Thanks for the helpful replies!

---

### Post by gilgongo on 2005-12-14
When you say "only JAmes Camerons site has the gui. This is where I can no longer get it from" what do you mean? I got it from his repostory, and installed it no problem, not 36 hours ago.

BTW: pptpconfig edits the required lines for chap_secrets etc. itself. You should not need to screw with them at all - in fact doing so will probably lead you to madness.

Also - I assume you have the pptp-linux package installed, yes? If not, nothing will work, obviously.

---

