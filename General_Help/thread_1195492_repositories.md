---
title: "repositories"
date: 2009-06-23
forum: General Help
---

### Post by saskatchewan on 2009-06-23
I am doing a clean install and have forgotten where to find the repositories for Ubuntu 9.04.

It is on an AMD 64 so getting wireless is an issue and that is the main reason I want the repositories.

Any suggestions as to the location of the link?

---

### Post by hansdown on 2009-06-23
Hi saskatchewan.

Sorry, do you mean the download site?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by saskatchewan on 2009-06-23
No, I already have that.
I was thinking the extra repositories that can be downloaded
It includes things like GoogleEarth

---

### Post by synapsys on 2009-06-23
Ok... thing is..... you don't 'download' repositories. Repositories are kept on servers across the internet. The packages shown in synaptic represent what is available from the repositories you subscribe to. These packages are downloaded from the repositories when you choose to install them. So, basically, unless you want to download the tarball and install something from source, then you need to be connected to the internet to install packages.

---

### Post by saskatchewan on 2009-06-23
I am online with a wired connection but I can't get my wirless to work
So, I am trying to download what ever I can
None of the links I have tried thus far have made my wirless work

---

### Post by 3rdalbum on 2009-06-23
You want [www.medibuntu.org](www.medibuntu.org)

---

### Post by synapsys on 2009-06-23
Oh i get it now :D

---

### Post by Wiebelhaus on 2009-06-23
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

for multi media , [Ubuntu Tweak will help you with the rest.]("http://ubuntu-tweak.com/")

---

### Post by tommah04 on 2009-06-23
whenever I forget, I just google "things to do after install ubuntu"

it usually has things in a few of those sites that I tend to over look

---

### Post by saskatchewan on 2009-06-23
I tried the repository suggestions but I still can't get skype as a possiblilty to install from synaptic.

I have tried the instructions for installing skype on AMD 64 but have had no luck.

---

### Post by executorvs on 2009-06-23
while not a preferred method [www.getdeb.net](www.getdeb.net) has many packages which aren't found in synaptic. 

install the debs from there using synaptic and if a newer version is added to restricted, backports, or medibuntu it will auto-update.

first however, double check your medibuntu settings as I think I got skype from them.

---

### Post by saskatchewan on 2009-06-24
I did get a couple of versions of skype with the download that you suggested but both say they have problems with audio output when I try them.

What can I do to make it work?

---

### Post by synapsys on 2009-06-24
after you add a repository you must update xapian index in order to see new packages in synaptic.

```
sudo update-apt-xapian-index
```

---

### Post by executorvs on 2009-06-24
I normally have to tinker with the different audio settings in skype. they don't maintain the linux client very well. I would suggest going into the preferences settings in skype and changing the adapters apply the changes and try the corrisponding test button. there are three audio setting I believe. it should only take a few minutes.

also make sure the capture settings under the ubuntu volume control are activated for your mic. this has left me confused for hours in the past until I noticed it.
you can test your mic with cheese or the sound recorder.

---

### Post by saskatchewan on 2009-06-24
thanks for all the help

---

