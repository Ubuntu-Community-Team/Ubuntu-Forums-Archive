---
title: "pidgin 2.5.8 install help"
date: 2009-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sir_Hellraiser on 2009-07-11
so i had a old version of pidgin installed try to update because yahoo wouldnt work  but now when i try to install the  version i get  this error and cant find away to fix

The following packages have unmet dependencies:
  pidgin: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
          Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
          Depends: libpurple0 (>= 1:2.5.8-1ubuntu2~pidgin1.8.10) but it is not going to be installed
          Depends: perl (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is to be installed
          Depends: perlapi-5.10.0 but it is not installable
E: Broken packages

 i have tried the follow command the sudo update didnt work could someone post the steps with commands please

---

### Post by gbrainin on 2009-07-12
It's a little difficult to find on the Pidgin page, but if you look at [http://pidgin.im/download/ubuntu/]("http://pidgin.im/download/ubuntu/") there are instructions for adding a PPA so that Pidgin is automatically updated along with your other automatic updates.

I don't know what version of Ubuntu you're using, but I was able to successfully set up the PPA in 8.04 and 8.10 to update Pidgin to 2.5.8, which works fine with the Yahoo changes.

---

### Post by Sir_Hellraiser on 2009-07-12
> **gbrainin said:**
> It's a little difficult to find on the Pidgin page, but if you look at [http://pidgin.im/download/ubuntu/]("http://pidgin.im/download/ubuntu/") there are instructions for adding a PPA so that Pidgin is automatically updated along with your other automatic updates.

I don't know what version of Ubuntu you're using, but I was able to successfully set up the PPA in 8.04 and 8.10 to update Pidgin to 2.5.8, which works fine with the Yahoo changes.

I have tried that and I cant get it to work correctly i have 8.04 that is why if someone could step byt step  here   

Ubuntu ships Pidgin but does not update it after a release (except for security issues and high-severity bugs). For those users who desire new releases of Pidgin, we have packaged Pidgin in a PPA. If you encounter problems with these packages, try building from source and report the bug.

To setup the PPA, copy-and-paste these commands into a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. The PPA will need to be re-setup only after upgrading Ubuntu.

This PPA is maintained by one developer, so please be patient. It often lags behind the source releases a couple of days.

so here is what i did i copy and paste
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
then i went into the update managewr and  there is nothing to be updated

---

### Post by GMachine_24 on 2009-07-12
Try uninstalling pidgin via synaptic and mark everything for removal and then install the latest version, which might only be available from the Web site. If the default settings don't work, search for Yahoo and Pidgin and you will find the fix.

---

### Post by Sir_Hellraiser on 2009-07-12
> **GMachine_24 said:**
> Try uninstalling pidgin via synaptic and mark everything for removal and then install the latest version, which might only be available from the Web site. If the default settings don't work, search for Yahoo and Pidgin and you will find the fix.

i been googling for 3 days
david@david:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com  67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: "Launchpad PPA for Pidgin Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
david@david:~$ 
david@david:~$ echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \ `lsb_release --short --codename` main | \
> sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu)  hardy main
david@david:~$ 

here is what i get in terminal and when i try to do it via systme update package manager i get unresolved dependicas

pidgin:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
 Depends: libpurple0 but it is not going to be installed
  Depends: perl (>=5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is to be installed
 Depends: perlapi-5.10.0  but it is not installable

---

### Post by Sir_Hellraiser on 2009-07-13
bump

---

### Post by gbrainin on 2009-07-13
If you uninstall and reinstall via synaptec, that should resolve any dependencies.  Then you can try adding the PPA again.  If you prefer to do it via graphical interface, you can try the instructions here: [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml]("http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml").

Although it doesn't specify how to work with 8.04, if you insert the codename ("hardy") it works, at least for me.

---

### Post by gbrainin on 2009-07-13
One other thing you could try is pressing the "check" button in the update manager.  It may not be showing Pidgin because it hasn't updated the list yet.  However, your earlier attempts to install may be preventing the update manager from realizing it needs to update, so you might need to uninstall Pidgin first.

---

### Post by Sir_Hellraiser on 2009-07-13
> **gbrainin said:**
> One other thing you could try is pressing the "check" button in the update manager.  It may not be showing Pidgin because it hasn't updated the list yet.  However, your earlier attempts to install may be preventing the update manager from realizing it needs to update, so you might need to uninstall Pidgin first.
i did the uninstall and reinstalled last night and no updated were avaiable i will  do the check thing and the others you have mention tonightwhen i get home

---

### Post by Sir_Hellraiser on 2009-07-13
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91...46 80]
Some index files failed to download, they have been ignored, or old ones used instead. 

i get  this error when i do check for updates

---

### Post by gbrainin on 2009-07-13
Hmm.  You may need to go through and reinstall each of the packages that is marked as a failed dependency.  I'm not sure why they don't work for you, as I know I successfully installed the Pidgin PPA in an 8.04 system.

Also, it's odd and disturbing that you can't get the package list to download correctly.  That may explain some of your broken dependencies, as you aren't getting updates on other packages because your list isn't updating.  You could try it again later, hoping that it was just the server being flaky, but if it does this all the time there's probably something wrong with your setup.

Perhaps if you posted the output of:

```
cat /etc/apt/sources.list
```

we could see something that's wrong in there.

---

### Post by Sir_Hellraiser on 2009-07-14
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron

---

### Post by Sir_Hellraiser on 2009-07-14
i did try installing the dependincuaes and  it installed version 2.4  for some reason

---

### Post by snowpine on 2009-07-14
I see that you are running the lpia "Dell Remix" version of Ubuntu 8.04. You will need to find an lpia version of the package; you can't just install an i386 package as it's the wrong architecture. (Edit: you are in luck; I just checked the Pidgin PPA for you, and they do indeed include an lpia port. Now the question is fixing those broken dependencies.)

Frankly in your case I would recommend simply installing the current Ubuntu release, 9.04. It will give you a newer version of Pidgin, and solve your "failed to fetch" problem too.

---

### Post by gbrainin on 2009-07-14
Aha!  It appears you are using a netbook.  (Perhaps a mini 9?)

That sort of explains why your repositories are behaving differently from what I've seen.  Unfortunately, I have no experience with those alternate repositories, so I'm kind of out of my depth here.  Compared to what I've seen, your sources.list is strangely small and has no comment lines--it's also missing the Pidgin PPA that should have been installed earlier.

So at this point, I'm just kind of guessing at best.  Perhaps someone with a similar system can chime in, here.  But as long as I'm guessing, when you say version 2.4 was installed when you tried to reinstall the dependencies, that's version 2.4 of what?

Edit: Or you can do what Snowpine suggested, and switch to the vanilla version of Ubuntu.  You might want to search the forums regarding the costs and benefits of doing so, but I know many people have done it successfully.

---

### Post by Sir_Hellraiser on 2009-07-14
yeah i have a dell mini 9  that this is on with no external cd rom yet so i wouldnt be able to upgrade it

---

### Post by snowpine on 2009-07-14
> **Sir_Hellraiser said:**
> yeah i have a dell mini 9  that this is on with no external cd rom yet so i wouldnt be able to upgrade it

You can install Ubuntu Netbook Remix 9.04 without an external CD ROM. All you need is a 1gb (or larger) USB flash drive.

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by GMachine_24 on 2009-07-14
Hi:

Well, so you've had lots of advice that hasn't helped. Hmmm.

I had to d/l Pidgin from the Web site to get the latest version as it was not available via synaptic or the regular sudo apt-get install thing.

Actually, the very first time I tried to install Pidgin 2.5.8 I had to compile it from source - I think it had just been released. That was a disaster. If you want to get rid of everything related to Pidgin you might try:

```


sudo apt-get purge pidgin


```

Even after downloading 2.5.8, I had to muck around with the settings (after searching the Net.) If I remember correctly - which is probably a 50-50 chance - I had to delete some files from the latest install to get rid of conflicts. Of course, it would be helpful if I'd saved this information. But, alas...

Ok, so I guess this was it:

"If you upgraded by compiling Pidgin yourself, make sure you removed your distribution's existing libpurple package (for Ubuntu and Debian users this is libpurple0; for RedHat/Fedora users it should be libpurple). Then run 'sudo ldconfig' (or 'ldconfig' if you have a root shell already) and try again."

Of course this applies to the self-compiled version. But who knows, maybe it's worth a try.

Otherwise, I'm sure you've ready everything here.

[http://planet.pidgin.im/](http://planet.pidgin.im/)

I just kept mucking around until it worked. I know that's not very helpful; but .....

good luck.

---

