---
title: "Ekiga install Newby problem"
date: 2009-02-16
forum: General Help
---

### Post by bobritter on 2009-02-16
Trying to install Ekiga - Nwby to Linux I'm sure it's me.
During setup get to page for NAT detection and get message:
Ekiga detected Symmetric NAT.The most appropriate method, if your .....is to forward the required ports to your internal machine in......etc"
I suppose to a Linux guru that all means something but not to me at this stage of the learning curve.
I continued on anyway and got to the Ekiga GUI. Entered sip:500@ekiga.net like the confirmation email said for an echo test. At first I did get a sexy womens voice telling me about the test but nothing ever played back. I suspected the mic. Tried SoundRecorder and no go in fact when I hit Record the record time went crazy. Fooled around with the sound preferences until I found an Input Source setting that worked with SoundRecorder Went back to Ekiga and now it won't even connect to sid:500... 
I really want to learn a bit about Linux and Ubuntu and really like Ubuntu as it was installed but have had bad experiences trying to change anything. I'm aware of the "stigma" Linux has about not being to user friendly and would like to overcome that.

I've been a Windows developer ( don't hold that against me ) for many, many years and don't really like Windows so I want to try Linux. Any help appreciated. Thanks, Bob Ritter, Pensacola, FL

---

### Post by mikewhatever on 2009-02-16
Hi and welcome,
the message about NAT and port forwarding is quite common in networking and doesn't have anything Linux specific. It simply means that if you are behind, for example, a router, you need to specify an incoming port for Ekiga, or to forward a port. Your router manual is the best place to look for the way to do it, another good place is [http://portforward.com/](http://portforward.com/).

Here are some more useful links;
[http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga](http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga)
[http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router)

I forgot to ask, what version of Ubuntu do you have? Why did you have to install Ekiga, isn't it installed by default?

---

### Post by bobritter on 2009-02-18
I misspoke. I didn't have to install Ekiga, just set thing up. I'm on Cox cable thru a wireless router so I'll look into that.

As of this morn I CAN connect to the sip:500 echo test and hear the voice but the mic is dead

While I have your attention the next problem seems to be recognising my USB web cam. In the setup it recognised QCM USB Camera but when I connected to sip:500 I get a popup mesg "Error while openig device QCM USB Camera".

Thanks again for your help. Bob Ritter

---

### Post by _violet_ on 2009-02-27
Hi there,
I was wonder if you can help with this. I am having pretty much the same problem as bobritter because, when I try to configure the Akiga, a pop up window comes up with the NAT detection and it tells me to forward the ports to change to Cone NAT. Now, I tried Portforward but the Akiga is not listed among the applications. What am I supposed to do then? I don't know what the required ports are and I don't know how to forward them. Any help appreciated
Cheers
Violet

---

