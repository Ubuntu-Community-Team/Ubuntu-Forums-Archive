---
title: "Mixing distros"
date: 2009-03-23
forum: General Help
---

### Post by KJoFan on 2009-03-23
I am wondering if there is some way to run a mixture of Eeebuntu and Xubuntu on my machine. I installed Eeebuntu on my HP Mini, which worked fine except the wireless card. I couldn't any fix to work that I found for it. I switched to Xubuntu and wireless works flawlessly. The only problem with this is that obviously Xubuntu is not configured for the small screens of the netbooks. Is there any way to either alter Xubuntu to fix the resolution/display to fit the netbook or alter Eeebuntu so that I can use the drivers apparently included with Xubuntu for my wireless card?

---

### Post by chriskin on 2009-03-23
i post to subscribe because i am interested in this idea as well

---

### Post by snowpine on 2009-03-23
> **KJoFan said:**
> I am wondering if there is some way to run a mixture of Eeebuntu and Xubuntu on my machine. I installed Eeebuntu on my HP Mini, which worked fine except the wireless card. I couldn't any fix to work that I found for it. I switched to Xubuntu and wireless works flawlessly. The only problem with this is that obviously Xubuntu is not configured for the small screens of the netbooks. Is there any way to either alter Xubuntu to fix the resolution/display to fit the netbook or alter Eeebuntu so that I can use the drivers apparently included with Xubuntu for my wireless card?

My guess why Eeebuntu doesn't work right on your HP Mini is that Eeebuntu uses the special eeepc kernel, which is tweaked specifically for the eee. Since you don't have an eee, your hardware is not supported.

I can think of two solutions, depending on which install you want to use as your starting point:

1) With eeebuntu installed, replace the eeepc kernel with the generic kernel. You can do this by going into Synaptic and installing the linux-generic package. Then, edit your /boot/grub/menu.lst file to boot the correct kernel.

2) With xubuntu as the starting point, install the netbook remix launcher: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by KJoFan on 2009-03-23
I realize that Eeebuntu isn't optimized to run on my machine but it's the best distro for netbooks I've found so I'm trying to make it work. :)

I will give your suggestions a go and see what I can come up with.

Thanks!

---

### Post by KJoFan on 2009-03-23
I tried the suggestion of installing the remix to the standard Ubuntu install and get the following error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE 
W: You may want to run apt-get update to correct these problems

However, running update doesn't correct whatever the problem is.

Suggestions?

---

### Post by chriskin on 2009-03-25
follow this quide, always worked every time i got this error 


> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
``````
gpg --export --armor 0c713da6 | sudo apt-key add -
```Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

as said , use the 8 last digits instead of the ones in the example above

---

