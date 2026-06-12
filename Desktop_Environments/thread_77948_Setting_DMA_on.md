---
title: "Setting DMA on"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Jens Willem on 2005-10-17
Hi.  I've been using Ubuntu (my first distro) for a month... yes, I am a newbie. :p  I play my DVD movies in the computer, so I have to enable DMA mode in order to get a smooth playback. No problem. What I do is executing...

```
sudo hdparm -d1 /dev/hdc
```

... in a terminal before start playing any DVD and it works fine. But I suppose maybe there is some way to enable DMA automatically in every boot of the computer. Maybe adding this command line to some kind of script or something like that? It would be very useful.

Thanks.

Great OS and great forum!

---

### Post by jamesford on 2005-10-17
yes there is. still pretty new myself so if im wrong hopefully someone will correct me but heres what ive done:
sudo gedit /etc/hdparm.conf

enter at the bottom:
/dev/cdrom {
       dma = on
}
/dev/hdc {
	dma = on		   
}
/dev/hdd {
	dma = on		   
}

---
not sure if all that is needed , maybe in your case
/dev/hdc {
	dma = on		   
}
will be enough

---

### Post by Stormy Eyes on 2005-10-17
Unless you've got a really exotic setup, **jamesford's** solution should be what you need.

---

