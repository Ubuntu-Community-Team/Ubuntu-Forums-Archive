---
title: "Firefox won't start after upgrade"
date: 2005-07-23
forum: Desktop Environments
---

### Post by lassel on 2005-07-23
For the last few days synaptic has been telling me that it couldn't upgrade firefox automatically and that I needed to do a "Smart upgrade". 

Failing to understand what that was I navigated to the firefox package and picked "upgrade" from the menu.

After that I got this error:
E: /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox

-- that means nothing to me.

I then found that firefox wouldn't start anymore. I restarted my system (old habbit)

I tried searching a bit around and asked at IRC. I was told that I get this "because I enabled the backports".

Now if I launch synaptic it tells me that I have a broken package.
That package is the "firefox-gnome-support" package.

I don't know how to proceed from here. I guess I want to either up or downgrade firefox so it will work again.

I tried downgrading firefox with: 
sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

that gave me:
but I get: firefox-gnome-support: Depends: firefox (= 1.0.4-1ubuntu3~5.04ubp5) but it is not going to be installed

I am totally stuck here ... 
Thank you for reading.

---

### Post by jesse on 2005-07-23
1. Uninstall every package you have containing the word "firefox"
Note: before you do this you might want to have another browser installed on your system such as galeon or konqueror. If you have to uninstall all firefox packages in order to get synaptic to work again, then print this how to before you do.) 

2. Then add the following line to the file /etc/apt/sources.list

deb [ftp://packages.debian.org/debian/](ftp://packages.debian.org/debian/) unstable main contrib non-free

and save the new version of sources.list (You'll have to open it as root by typing "sudo gedit /ect/apt/sources.list" at a terminal to have write priveliges.)

3. Open Synaptic (if it's not already running) and reload the package list.
(or, without synaptic running, type "sudo apt-get update" at a terminal)

4. In synaptic do a search for "firefox." You should not have any firefox packages installed at all, so install "mozilla-firefox" and "mozilla-firefox-gnome support" which are in the debian unstable repository. These are the only firefox packages you really need at all. You do not need "firefox" and "firefox-gnome-support" from the backport repository (which do not contain the word "mozilla" and which depend on "mozilla-firefox" and "mozilla-firefox-gnome-support" anyway.

5. IMPORTANT! Once you've installed these two mozilla-firefox packages, comment out the debian unstable repository. (Put a # symbol in front of the line in your file /etc/apt/sources.list)

#deb [ftp://packages.debian.org/debian/](ftp://packages.debian.org/debian/) unstable main contrib non-free

It's a good idea to keep it in your list of disabled repositories, just in case you ever need the newest version of a debian package, but it's not a good idea to have it enabled as a source unless you need such a specific newer package. E.g. if you want to use gtkpod with an Ipod shuffle, you have to the use version from the debian unstable repository, as the older versions of gtkpod found in the ubuntu repositories (including backports and breezy so far) and the stable debian repositories don't work with the shuffle. (Sorry for going slightly off on a tangent.)

---

### Post by lassel on 2005-07-24
Ok,

Good explaination. Thanks. But before I go ahead i have one more question;

If I do that I get prompted that I will also uninstall the "ubuntu-desktop" package.

That got me really nervous. Will I break anything by doing that? I want my system to be as mainstream as possible to avoid upgrade issues in the future.

Thanks

---

### Post by lassel on 2005-07-24
Just for the record. Here's what I did.

I commented the backports out of /etc/apt/sources.list:

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Then I did a sudo apt-get update.

I removed all packages i found via synaptic that had firefox in the name. That prompted me to also uninstall ubuntu-desktop.

When that was done I located the ubuntu-desktop in synaptic and installed that. That has dependencies to firefox so I got that along with it and kept my "standard" install.

Now I have a potentially unsafe firefox 1.0.2. I don't know if I should:
a) reenable the backports and try another upgrade. 
b) enable the debian unstable repository and get a new firefox from that
c) Wait for the official ubuntu repo to offer an updated firefox.

-- I think I'll go with the last option...

---

### Post by jesse on 2005-07-24
The same thing happened to me when I used the debian unstable repository to upgrade firefox. 

I think when I uninstalled the Ubuntu version of firefox it told me it told me ubuntu-desktop and yelp would both be uninstalled. 

According to the package description in synaptic, ubuntu-desktop is safe to uninstall without breaking the system, but they recommend it is installed. 

What I did was 

1. let it uninstall ubuntu-desktop and yelp when I uninstalled the Ubuntu version of firefox

2. then install the debian unstable packages mozilla-firefox and mozilla-firefox-gnome-support

3. then, after that, comment out the debian unstable repository and reinstall ubuntu-desktop and yelp. 

It worked for me.

---

