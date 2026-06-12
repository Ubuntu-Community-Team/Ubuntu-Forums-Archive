---
title: "A lightweight webkit-based browser for Ubuntu?"
date: 2009-04-20
forum: General Help
---

### Post by Guillaumeb on 2009-04-20
Hi all,

Now that I have everything up and running, I am looking for a browser based on webkit.
On windows I used to use Chrome. On my Mac I have Safari 4

From what I read I understand that Webkit is based on KDE... but I much prefer GNOME Is there a solution for me ?

thanks

---

### Post by FluffyElmo on 2009-04-20
The Gnome Epiphany browser can be configured to use either Gekko or Webkit as it's rendering engine. To install the webkit version run the following from a terminal...

```
sudo apt-get install epiphany-webkit
```

---

### Post by LoloftheRings on 2009-04-20
There are more than just epiphany (I think epiphany is the best though).
Just go to Applications -> Add / Remove software
enter "webkit" as search term and install one!
Arora might show up, but as it is a KDE program, it will run slower.

---

### Post by Guillaumeb on 2009-04-20
getting this error:

[INDENT]root@guillaumeb:~# sudo apt-get install epiphany-webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package epiphany-webkit is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package epiphany-webkit has no installation candidate[/INDENT]

---

### Post by paradigm2 on 2009-04-20
> **Guillaumeb said:**
> Hi all,

Now that I have everything up and running, I am looking for a browser based on webkit.
On windows I used to use Chrome. On my Mac I have Safari 4

From what I read I understand that Webkit is based on KDE... but I much prefer GNOME Is there a solution for me ?

thanks

Chromium (which is what chrome actually is only Chrome is repackaged for Google) is in development for Linux right now.  It is pre-alpha.  It does generally work decently but features like choosing options, proxies, flash, etc don't seem to work yet.  Thoguh tabbed browsing does work or me.

I'm going to avoid giving out the url again because it seems the development team does not want people using the unstable pre-alpha version as it might give a bad first impression.  However, if you search here you will find it. :)  There is a PPA for it which will pull the nightly build.  I have been starting it up each day and noting the progress and using it for my browsing until it crashed.  Lately I've been getting longer and longer use out of it before it crashed....

---

### Post by FluffyElmo on 2009-04-20
Regarding the error, just try installing the regular Epiphany package.
```
sudo apt-get install epiphany
```

They were planning on moving to Webkit as the default and as you are running Jaunty this may have happened already. I had tested the line on Intrepid...

Not sure how you can be certain that it's using Webkit but maybe Google will turn up a test:)

---

### Post by chriskin on 2009-04-20
Arora is really good, better than chromium , since it is early on its development
i haven't tried epiphany yet

---

### Post by namegame on 2009-04-20
Check out Midori.

I've used it on Arch and it's fairly good.

---

### Post by chriskin on 2009-04-20
> **namegame said:**
> Check out Midori.

I've used it on Arch and it's fairly good.


my opinion, even if i seriously doubt that it matters at all :P, is that midori is not good enough for everyday use, not yet at least. it lacks usability

---

### Post by namegame on 2009-04-20
> **chriskin said:**
> my opinion, even if i seriously doubt that it matters at all :P, is that midori is not good enough for everyday use, not yet at least. it lacks usability

I used it as my only browser for about a month and I never had a problem with it. Then again, our systems are probably vastly different so that could contribute to it.

Did you use it on Ubuntu? Perhaps the versions in the Arch repos and the Ubuntu repos are significantly different.

---

### Post by chriskin on 2009-04-20
> **namegame said:**
> I used it as my only browser for about a month and I never had a problem with it. Then again, our systems are probably vastly different so that could contribute to it.

Did you use it on Ubuntu? Perhaps the versions in the Arch repos and the Ubuntu repos are significantly different.


ah, don't remind me of arch :S
it has this strange idea, just like debian does, that i have no screen :P

yes i have only tried it on ubuntu

---

### Post by namegame on 2009-04-20
> **chriskin said:**
> 

yes i have only tried it on ubuntu

Probably a difference in Version, the midori version in the Arch repos looks to be more recent than the midori version in the ubuntu repos.

---

### Post by LoloftheRings on 2009-04-21
Epiphany is still Gecko in Jaunty. The package description tells me the following:
This dummy package installs Epiphany with the Gecko backend by default.

---

### Post by chriskin on 2009-04-21
> **LoloftheRings said:**
> Epiphany is still Gecko in Jaunty. The package description tells me the following:
This dummy package installs Epiphany with the Gecko backend by default.


the one we mentioned was the epiphany-webkit one 
it says that it installs epipahny with webkitGTK+ backend, or i understood something wrong?

---

### Post by cyran on 2009-04-21
'epiphany' is a game; technically 'apt-get install epiphany-browser' is what you want.

> **chriskin said:**
> the one we mentioned was the epiphany-webkit one 
it says that it installs epipahny with webkitGTK+ backend, or i understood something wrong?

Like Guillaumeb said, the 'epiphany-webkit' package just *isn't* in the repository for Jaunty. It's only in Intrepid. Check it: [http://packages.ubuntu.com/jaunty/epiphany-browser]("http://packages.ubuntu.com/jaunty/epiphany-browser"). -gecko's there, but -webkit isn't. Weird.

---

### Post by FluffyElmo on 2009-04-21
Have you enabled all the repositories? Just poking around, and on Intrepid epiphany-webkit is in universe while epiphany-gecko and epiphany-browser are in the main repository. Odd, but try enabling universe, update and then see if it appears in Jaunty.

---

### Post by FluffyElmo on 2009-04-21
Or based on the page below maybe not. Have you tried downloading the Intrepid package from the page below and just installing that?

[http://packages.ubuntu.com/search?keywords=epiphany-webkit](http://packages.ubuntu.com/search?keywords=epiphany-webkit)

---

### Post by chriskin on 2009-04-21
> **cyran said:**
> 'epiphany' is a game; technically 'apt-get install epiphany-browser' is what you want.



Like Guillaumeb said, the 'epiphany-webkit' package just *isn't* in the repository for Jaunty. It's only in Intrepid. Check it: [http://packages.ubuntu.com/jaunty/epiphany-browser](http://packages.ubuntu.com/jaunty/epiphany-browser). -gecko's there, but -webkit isn't. Weird.


eh..actually it is . i have enabled no other repository than those of ubuntu (multiverse, universe included) and i have the webkit one. the package is named epiphany-webkit

---

### Post by 3rdalbum on 2009-04-21
Epiphany-webkit is broken on Intrepid - the form buttons on web pages do not work.

---

### Post by nortexoid on 2009-04-30
> **Guillaumeb said:**
> getting this error:

[INDENT]root@guillaumeb:~# sudo apt-get install epiphany-webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package epiphany-webkit is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package epiphany-webkit has no installation candidate[/INDENT]

Same, after adding

```
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
```

to my source list. I can't access the OpenPGP key. The server keeps timing out.

---

### Post by nortexoid on 2009-04-30
> **nortexoid said:**
> Same, after adding

```
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
```

to my source list. I can't access the OpenPGP key. The server keeps timing out.

Oh, I know why this happened. I didn't add

```
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
```

as well. After adding it to my sources a "sudo apt-get install epiphany-webkit" did the trick. Too bad the browser ended up being unbearable to use. Password saving didn't work, couldn't access the about:config page, loading times (oddly) seemed slow, etc. etc.

---

