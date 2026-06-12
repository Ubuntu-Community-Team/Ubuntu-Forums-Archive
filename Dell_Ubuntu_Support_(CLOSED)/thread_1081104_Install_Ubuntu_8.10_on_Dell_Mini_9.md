---
title: "Install Ubuntu 8.10 on Dell Mini 9"
date: 2009-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pipposanta on 2009-02-26
Hi,
I bought a Mini 9 with Ubuntu 8.04. Now  want to upgrade to Ubuntu 8.10. So I am downloading an Intrepid Ibex installation image from here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.10](http://linux.dell.com/wiki/index.php/Ubuntu_8.10). Is this the right file? This will run on my Mini 9 with all the correct drivers???

Thanks in advance for any answer!!!

---

### Post by dgoosens on 2009-02-26
... or you could simply go to [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading") where the whole upgrading process is indicated ...

---

### Post by pipposanta on 2009-02-26
Ok, I followed the instructions... but when I go to Update Manger it doesn't found updates.

---

### Post by sirebral on 2009-02-26
Funny.  I was doing the same thing to help you pipposanta.

maybe you want to try the server method.  What is it?

apt-get install update-core-manager


That might work as a Super User.  I am not sure if the Mini 9 allows it to be updated to 8.10 because of the way it is configured.

---

### Post by pipposanta on 2009-02-26
See the post down that I upped

---

### Post by dgoosens on 2009-02-26
to change Ubuntu version you can not simply update your system...
you should ask for this explicitly as it is clearly explained on the webpage I mentioned above

---

### Post by pipposanta on 2009-02-26
> **pipposanta said:**
> Ok, I followed the instructions... but when I go to Update Manger it doesn't found updates.

> **dgoosens said:**
> to change Ubuntu version you can not simply update your system...
you should ask for this explicitly as it is clearly explained on the webpage I mentioned above

I followed your instructions, as you can see, (i have enabled to download also normal release) but the problem remains.

---

### Post by sirebral on 2009-02-26
The update doesn't show up because it is a DELL modified version of Ubuntu.  I replied to your post below with a solid answer.

---

### Post by pipposanta on 2009-02-26
OK, thanks for the exhaustive responses!!

---

### Post by sirebral on 2009-02-26
Double post because - sometimes I just remember other ways to fix the problem.

Here is one way to get what you want.  Ask DELL on their IdeaStorm page.

It is my belief that DELL will stick to the LTS versions and their updates, but they do listen to the community and respond.

---

### Post by pipposanta on 2009-02-26
Only a last question: if I make a fresh install with the iso downloadable in this page ([http://linux.dell.com/wiki/index.php/Ubuntu_8.10](http://linux.dell.com/wiki/index.php/Ubuntu_8.10)) will all the hardware work?

---

### Post by sirebral on 2009-02-26
I think this is the web page with all of your answers: [http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html](http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html)

it took time to find.  I also thought someone else would eventually show up and help you, but meh.

---

### Post by anjilslaire on 2009-02-26
> **sirebral said:**
> I think this is the web page with all of your answers: [http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html](http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html)

it took time to find.  I also thought someone else would eventually show up and help you, but meh.

Yes, that is a perfect guide on installing the vanilla 8.10 on th mini, including the netbook remix if desired. I'm currently running that, and its great.

---

### Post by jaqrah on 2009-02-27
I would also recommend the site mentioned above.  Just as a reminder:

[http://www.ubuntumini.com/2008/10/ubuntu-810-intrepid-ibex-on-dell-mini-9.html](http://www.ubuntumini.com/2008/10/ubuntu-810-intrepid-ibex-on-dell-mini-9.html)

By the time my dell mini 9 had arrived (it was delayed), I had already prepared my usb drive with the iso image.  I went straight for 8.10 from the get go.  The site will help you get all of your issues worked out (like sound) and even help you load the Netbook Remix desktop theme.


Good luck

---

