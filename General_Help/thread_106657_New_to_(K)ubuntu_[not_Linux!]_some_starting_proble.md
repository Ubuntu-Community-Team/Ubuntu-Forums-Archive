---
title: "New to (K)ubuntu [not Linux!] some starting problems"
date: 2005-12-21
forum: General Help
---

### Post by seppelrockt on 2005-12-21
I wanted to setup a test box to evaluate Kubuntu 5.10 a little before I install it on my parents box. Install worked fine, now I have to get wpa_supplicant working to get Inet access.

Therefor I installed wpa_supplicant-4.5.0 ubuntu deb file (downloaded on another box) and copied over my working wpa_supplicant.conf.

wpa_supplicant -i eth0 - D wired -c /etc/wpa_supplicant.conf gave me something about can not read configuration file :-( Doublechecked the file, changed permissions to rwx for all, put it on different places, no luck ...

Then I uninstalled wpa.supplicant with adapt and installed it again. But now I doesn't install its own config file to /etc anymore (I want to have a look if something changed but overwrote the file with my own previously). apt-get install /path/to/the/wpa-supplicant.deb told me it can't find the file ... 

 ~ # cat /etc/wpa_supplicant.conf.wired
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
ap_scan=0
network={
        key_mgmt=IEEE8021X
        eap=MD5
        identity="mylogin"
        password="mypassword"
        eapol_flags=0
}

And yes I used sudo and tried it without too - must say I like sudo very much!

Did I miss something important? Can somebody help me please - maybe pointing to some ubuntu docs that might help?

---

### Post by Rackerz on 2005-12-21
So your internet isn't working and your trying to install a driver for it? Im confused, sorry if im wrong.

---

### Post by seppelrockt on 2005-12-21
[QUOTE=Rackerz]So your internet isn't working and your trying to install a driver for it? Im confused, sorry if im wrong.[/QUOTE]

Sorry, I did not thought about the fact that internet usaly JUST WORKS (tm) for people - but not in Germany and exspecially not for me ;-)

In my students apartement I am connected to the university intranet that routes me to the internet. Therefor I have to do some authentification stuff (AEP-MD5) that works great with wpa-supplicant (note: this is over ethernet aka wired lan). Right now I am typing from my Gentoo Linux notebook which has wpa-supplicant working.

On a test box I installed kubuntu and now need to get internet working. Installed wpasupplicant_0.4.5-0ubuntu1_i386.deb and copied my working config with the results I posted above.

I hope now things are clear and somebody is willling to help me.
Thanks in advance!

---

### Post by seppelrockt on 2005-12-21
OK, after turning debug on it turns out to be the ctrl_interface_group line in my config. Kubuntu doesn't have a group called wheel I think cause they use sudo. Commenting out the line solved my problem.

---

