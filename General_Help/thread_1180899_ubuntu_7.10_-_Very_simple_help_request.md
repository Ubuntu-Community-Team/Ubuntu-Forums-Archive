---
title: "ubuntu 7.10 - Very simple help request"
date: 2009-06-07
forum: General Help
---

### Post by ikick on 2009-06-07
Hi there guys,

I own a dedicated server. I installed hypervm on it as i am not an expert when it comes to linux. I like the ideas of having a virtual machine for the different things that i do. Getting to the point...

Tonight i downloaded ubuntu 7.10 from the openvz website, it works like a charm except the apt-get functions.

I'm always getting something along the line of:

```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/ANYFILE/  404 Not Found [IP: 91.189.88.31 80]
```

No matter the file or anything, i still seem to get that and it's really starting to get on my nerves since i need the server properly configured within the next 2 hours.

Could anyone provide me with some help?

Thanks a heap guys!

ikick

---

### Post by Sidewinder1 on 2009-06-07
First, Welcome!
7.10 (Gutsy Gibbon) is no longer supported, hence the error.
Why not download, burn, and install the current LTS version 8.04.2 (Hardy Heron)?

HTH,

Side

---

### Post by ikick on 2009-06-07
I would be more then happy to do that but i simply don't know how, lol. Plus the upload speed here in Australia is simply ****, would take hours and hours.

I am on the hunt for a premade os template i can simply wget to my node... would that work?

---

### Post by albinootje on 2009-06-07
> **ikick said:**
> 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/ANYFILE/](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/ANYFILE/)  404 Not Found [IP: 91.189.88.31 80][/code]

No matter the file or anything, i still seem to get that and it's really starting to get on my nerves since i need the server properly configured within the next 2 hours.

You can use this : [http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/) in your /etc/apt/sources.list (Read the words in red color!)

But.. since you're using OpenVZ, why don't you use a newer template for the containers ? [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)
Or is this on your OpenVZ HardwareNode ?

---

### Post by ikick on 2009-06-07
albinootje, Thanks for the help.

I didn't realise there was a link to premade OS templates :P

I am installing ubuntu 8.04 as we speak and will post the results when im finished.

Thanks again guys ;)

---

