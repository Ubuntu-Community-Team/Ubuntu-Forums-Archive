---
title: "firefox-1.0.6"
date: 2005-07-22
forum: Desktop Environments
---

### Post by hydra on 2005-07-22
Hi ive just upgraded to new mozilla-firefox-1.0.6 because i was getting errors in 1.0.2 version....it always got stucked...anyways i succesfully installed the new version but as seen on the image i cant get my downloads into my desktop i get them in /root but i cant modify that option in the download window....any hint on how to change this to get all my downloads into my desktop...thnx

---

### Post by hydra on 2005-07-22
K thnx i think i solved it in Edit-->Preferences--->Downloads......thnx anyways

---

### Post by brian g on 2005-07-22
where should i install firefox to?
i want to replace the firefox install from the ubuntu package with 1.0.6 that i've downloaded from mozillas website.

---

### Post by manicka on 2005-07-22
[QUOTE=brian g]where should i install firefox to?
i want to replace the firefox install from the ubuntu package with 1.0.6 that i've downloaded from mozillas website.[/QUOTE]
 firefox 1.0.6 is now available in backports-staging

---

### Post by brian g on 2005-07-22
[QUOTE=manicka]firefox 1.0.6 is now available in backports-staging[/QUOTE]thank you.


Just incase anyoen else has trouble finding it right away.. 
add the following to /etc/apt/sources.list
## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

---

### Post by hydra on 2005-07-22
yep or from the mozilla.org page and then just 

```

 tar -xzvf firefox-1.0.6.installer.tar.gz
cd firefox-installer
./firefox-installer

```

voilá u got ur new firefox

---

### Post by brian g on 2005-07-23
[QUOTE=hydra]yep or from the mozilla.org page and then just 

```

 tar -xzvf firefox-1.0.6.installer.tar.gz
cd firefox-installer
./firefox-installer

```

voilá u got ur new firefox[/QUOTE]
i had done that but then stoped because i wasn't sure what directory to install it to.
i didn't want to end up with two installations of firefox

---

### Post by manicka on 2005-07-23
I think that you're better off sticking with the deb packages, unless of course you decide to always use this method to install firefox.

If you go ahead with this method and remove the old version before installation, then you shouldn't have to many problems with double installations.

I've always stuck with the packaged versions in ubuntu and other distro's and never had a problem with firefox.

---

### Post by Mr.Rogers on 2005-07-23
I just installed 1.0.6 in the same directory as 1.0.2, the installer said something about it having to delete the whole folder so I just clicked yes. It installed and it worked fine, all old FF icons and links call up the new one.

---

