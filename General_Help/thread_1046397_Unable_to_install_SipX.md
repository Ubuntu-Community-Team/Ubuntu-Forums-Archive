---
title: "Unable to install SipX"
date: 2009-01-21
forum: General Help
---

### Post by ssaes on 2009-01-21
I'm trying to install SipX on my ubuntu desktop system (Intrepid).

Following the instructions from:

[http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu]("http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu")

I modified the /etc/apt/sources.list file to ensure that the CD-ROM source was commented out, the "universe repository" was uncommented

[INDENT]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe [/INDENT]

and added the following lines specific to SipX

[INDENT]     deb [http://scm.calivia.com/pub/sipx/ubuntu](http://scm.calivia.com/pub/sipx/ubuntu) stable main 
     deb [http://scm.calivia.com/pub/sipx/ubuntu](http://scm.calivia.com/pub/sipx/ubuntu) unstable main [/INDENT]


After doing an "apt-get update" I tried to install SipX using the command "sudo apt-get install -t stable sipxpbx".  This command failed because there were several dependent packages that were not installed:

[INDENT]The following packages have unmet dependencies: sipxpbx: 

Depends: libcgicc1 but it is not installable            
Depends: libltdl3 (>= 1.5.2-2) but it is not installable        
Depends: libsipxcall1 but it is not going to be installed        
Depends: libsipxcommserver1 but it is not going to be installed 
Depends: libsipxmediaadapter1 but it is not going to be installed
Depends: libcgicc1 (>= 3.2.3) but it is not installable          
Depends: sipxregistry (>= 3.4) but it is not going to be installed
Depends: sipxproxy (>= 3.4) but it is not going to be installed            
Depends: sipxpublisher (>= 3.4) but it is not going to be installed            
Depends: sipxvxml (>= 3.4) but it is not going to be installed[/INDENT]

How can I resolve this?  For example, when I try to install "libcgicc1" the output indicates that there is a newer version of this library.  Is there another source that I need to include in the sources.list file that has links to these "older" libraries?  I am relatively new to Ubuntu so feel free to explain/educate.

Thanks

---

### Post by Michael Weston on 2011-07-21
Hi,
I think I can help! I recently found an SDK, which support a wide range of PBX. This SDK is called [COLOR="Red"]**Ozeki VoIP SIP SDK**[/COLOR], and it supports SipX ECS as well. The reason I recommend this, is that you can find a nice step-by-step guide on installation and configuration of SipX. Here is the website: [http://voip-sip-sdk.com/p_29-how-to-configure-ozeki-voip-sip-sdk-with-sipx-ecs-voip.html]("http://voip-sip-sdk.com/p_29-how-to-configure-ozeki-voip-sip-sdk-with-sipx-ecs-voip.html")

I hope this helps,
Michael

---

