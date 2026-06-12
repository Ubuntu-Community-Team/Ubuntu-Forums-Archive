---
title: "How can I install kde environment on my installed ubuntu 10.04 ?"
date: 2010-11-06
forum: Desktop Environments
---

### Post by rshinde70 on 2010-11-06
I have Ubuntu 10.04 installed on my system and I have Kubuntu 10.04 live CD.

and I want to install kde environment on my current system with live-CD and without connecting to the Internet. 

Please guide me.

---

### Post by marin123 on 2010-11-06
open synaptic package manager and search for kubuntu-desktop, check it and click apply changes... downside of this is that will install all of the kde apps (konqueror, kopete, k3b etc) and uninstalling kubuntu-desktop wont remove that packages (if you decide to remove it)...
during the installation you will get asked what desktop you want to be default (gnome or kde), but you can always change that when you log in...

edit: sorry, i havent read the part about not connecting to internet... i dont know how to do that from live cd...

---

### Post by Jechem on 2010-11-06
just install the kubuntu live cd. its ubuntu with kde environment. i think you need internet if you want to install kde on your current ubuntu install.

---

### Post by arnavk007 on 2010-11-06
Rshinde70 yes it is possible
there are some things you'll need to do
in the sources list deselect all the ubuntu mirrors select the ubuntu live cd
there should be some way to add the kubuntu live cd to it
do that
then put the kubuntu cd in your cd drive   If you are able to make it a source type

sudo apt-get install kubuntu-desktop 
taraa

---

### Post by rshinde70 on 2010-11-07
I have tried it. Its just working to minimize my downloading size. Without CD, it'll require to get 360 mb of packages, but, with CD, I have to download nearly about 170MB of data.

So, It works in some extend, but actually, I have very slow connection, so I can't download it.

I thought, Its possible to install kde environment without Internet.

Anyway Arnavk007, Thanks.

---

### Post by arnavk007 on 2010-11-07
> **rshinde70 said:**
> I have tried it. Its just working to minimize my downloading size. Without CD, it'll require to get 360 mb of packages, but, with CD, I have to download nearly about 170MB of data.

So, It works in some extend, but actually, I have very slow connection, so I can't download it.

I thought, Its possible to install kde environment without Internet.

Anyway Arnavk007, Thanks.
What's the speed of your net connection anyways
what if you open the cd select all packages and then try to install them using the software center
just noticed you are from India
also try deselecting all ubuntu mirrors
try typing 
sudo apt-get install kde
also disconnect your net connection during that time

---

### Post by I'mGeorge on 2010-11-07
it's pretty much resumed to using synaptic or sudo aptitude install kde . By the way while installing kde new programs will be installed with it and because of GNOME you might have already some software installed that does the same things. So you might wanna manage your software a little bit so you won't have meaningless disk usage.

---

