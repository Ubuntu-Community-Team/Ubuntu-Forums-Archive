---
title: "update local repository"
date: 2009-01-24
forum: General Help
---

### Post by aboud on 2009-01-24
hello ! 
i'm taking ubuntu with me to place where this no internet connection, and i need to install it on several computers. i have all the packages on external hard, but they are six month old, i'm thinking about "wget -c" all the /var/lib/apt/lists, but i'm wondering if this the best way, i know the dpkg-scanpackages will allows me to use them with synaptic but will this help update the new ubuntu on new computer ?

---

### Post by aboud on 2009-01-25
bump!

---

### Post by mb_webguy on 2009-01-25
You might want to check out [Keryx]("http://keryx.betaserver.org/").

---

### Post by Alterax on 2009-01-25
> **aboud said:**
> hello ! 
i'm taking ubuntu with me to place where this no internet connection, and i need to install it on several computers. i have all the packages on external hard, but they are six month old, i'm thinking about "wget -c" all the /var/lib/apt/lists, but i'm wondering if this the best way, i know the dpkg-scanpackages will allows me to use them with synaptic but will this help update the new ubuntu on new computer ?

> **aboud said:**
> hello ! 
i'm taking ubuntu with me to place where this no internet connection, and i need to install it on several computers. i have all the packages on external hard, but they are six month old, i'm thinking about "wget -c" all the /var/lib/apt/lists, but i'm wondering if this the best way, i know the dpkg-scanpackages will allows me to use them with synaptic but will this help update the new ubuntu on new computer ?

I have to keep a local mirror handy myself, so I think I can help you out here.
First, install **apt-mirror **and **AptOnCD**.

Configure apt-mirror by editing the **/etc/apt/mirror.list** file.  Mine contains the following; just change it to the location you prefer.

```
deb http://www.gtlib.gatech.edu/pub/ubuntu intrepid main restricted
deb-src http://www.gtlib.gatech.edu/pub/ubuntu intrepid main restricted
clean http://archive.ubuntu.com/ubuntu

```
Once that is done, open a terminal and type:

```
sudo apt-mirror &
```
and give it a day or so to download a local copy.  It'll put the mirror copy in the **/var/spool/apt-mirror/mirror/www.gtlib.gatech.edu** directory.

Once that is done, use the AptOnCD utility to burn the mirror to disc.  I recommend DVDs for this if you have that capability.

Then once you get those finished, just take the discs to your target computer and use this command to have the target recognize them:

**sudo apt-cdrom add**

Finally, when the discs have been added, start the automated upgrade process with:

```
sudo apt-get dist-upgrade
```

And that's it!






Afterthought:  (Having gone this far, milk the mirror for its worth)

Now if you can afford to keep the mirror on your machine, you may want to add Universe and Multiverse to the lines in mirror.list.  Install **apache2** on your machine and add a symbolic link to the /var/www/ directory that points to the apt-mirror location. I did mine like this:

```
sudo ln -s /var/spool/apt-mirror/mirror/www.gtlib.gatech.edu /var/www/repo

```
Then change your **/etc/apt/sources.list** to point to this web location:

```
deb http://192.168.0.27/repo intrepid main restricted multiverse universe
deb-src http://192.168.0.27/repo intrepid main restricted multiverse universe

```

(swap the IP address I mocked up here for your own IP address).

save it and open the **/etc/cron.d/apt-mirror **file (using sudo)
and knock off the # in front of the 0 4 * * * apt-mirror entry.
save that.  It just says at four AM every day, check to see if the mirror has anything to update.

Update your software list with apt-get update, and enjoy VERY fast program installs without bogging down your network.

---

### Post by EXCiD3 on 2009-01-25
[Keryx]("http://keryx.betaserver.org") would work perfect for this. You can run it off your harddrive and gather the updates and any new software easily for the computers and since it does not need to be burned off you can make changes easily such as adding packages to your hdd later on.

---

### Post by aboud on 2009-01-30
many many thanks.. 
both works, but i think i'll go alterax, i fell more in control. 
where did they take that thank button ?

---

