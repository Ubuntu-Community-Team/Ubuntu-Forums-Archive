---
title: "Firefox Failed to Connect Error"
date: 2009-04-19
forum: General Help
---

### Post by Prospero2006 on 2009-04-19
Hello All,
I am fairly good at configuring Ubuntu, but right now I am seeing this error fairly often, maybe 1 out of every 8-10 webpages:

Failed to Connect

     Firefox can't establish a connection to the server at  XXX.XXX.XXX.

It jumps to this error almost instantly after I click a link sometimes. I've done some configurations to speed up firefox, like increasing the network.pipelining, but I'm not sure if this would be causing it. 

If I refresh, it usually loads the page.

Any ideas where I might start or what settings I might look for in about:config?

Thanks!

---

### Post by codeseer on 2009-04-19
Are you on a wireless connection?

If you have a modem, are you watching the lights?

Are you using your ISP's DNS servers?

Have you tried a new profile?

---

### Post by Prospero2006 on 2009-04-19
I use a DNS server that is on a local machine on my network. I've never had an issue with it before, but I can try to change that setting. Good idea there.

It's definitely not a connectivity issue. THe network is stable. I've made several firefox configurations in about:config, and restore defaults doesn't seem to work.

How about this:
Is there a solid way to restore the about:config defaults?

Thanks again,

---

### Post by codeseer on 2009-04-19
Well you can scroll down through the about:config area and change anything that's in bold back to the defaults by right-clicking it and clicking Reset from the menu.

I'd try a new profile and see if the issue persists; if it doesn't then you know it's something to do with your configurations of addons or about:config. If it persists, then you can start looking at other things.

You can test a new profile out by typing this into the terminal:

```
firefox -profilemanager -no-remote
```

When it comes up, just create a new profile and name it whatever you want, then click on it and fire it up to test.

Edit:

I think if you click the little button under the 'Show All' button on the about:config page and click 'Restore Defaults' from the drop menu, it will restore all the defaults; I'm not 100% sure on that. If it works, you'll see the bolded entries turn plain again.

Those pipelining configurations aren't going to affect you that much, unless you set them extremely high. Setting them to like 8, 16 or maybe 20 should be ok.

---

### Post by Prospero2006 on 2009-04-19
Much appreciated. Just the info I was looking for.

---

