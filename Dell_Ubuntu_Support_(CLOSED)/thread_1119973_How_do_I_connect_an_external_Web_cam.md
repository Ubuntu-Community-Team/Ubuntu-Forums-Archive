---
title: "How do I connect an external Web cam"
date: 2009-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Blanchard on 2009-04-08
I bought a new Dell Mini 9 and I have an external webcam I want to use with it.  Plan to connect it when I get home from work.

Does anyone experience issues with an external usb webcam being used with Ubuntu?  When I tried using an external HD it was as if Ubuntu could not work with it.  

Then I found the solution in here.  Thanks Halfling!!!  So I thought I would see what I can find about using an external usb webcam with my Dell Mini 9.

---

### Post by armandh on 2009-04-09
plug in 
turn on app

It just worked [for me using 8.10]

---

### Post by Blanchard on 2009-04-09
I had to download something from the ubuntu website.  So a package could be installed on my Dell Mini 9.  

I think either I did not understand hw to activate the driver or something.  Anyway once I performed the install of the package the webcam began working like a charm.

I performed the following; (I pasted it below)
[http://packages.ubuntu.com/dapper/i386/build-essential/download](http://packages.ubuntu.com/dapper/i386/build-essential/download)

If you are running Ubuntu, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://•ubuntu.mirrors.tds.net/ubuntu](http://•ubuntu.mirrors.tds.net/ubuntu) dapper main

---

