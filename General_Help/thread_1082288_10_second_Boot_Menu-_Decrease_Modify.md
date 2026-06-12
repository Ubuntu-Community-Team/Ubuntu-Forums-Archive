---
title: "10 second Boot Menu- Decrease /Modify"
date: 2009-02-27
forum: General Help
---

### Post by eBrY on 2009-02-27
Hi I don't have experience with Ubuntu/Linux. Just finished install of the latest version.

How do I adjust the rather long 10 second wait inside the Ubuntu boot after selecting Ubuntu it asks if I want to go into the menu, which I would never have a need to do. I would like to set it to like 2 or 1 second to decrease boot time. Where would I adjust this? I am totally new to Ubuntu/Linux so thorough step-by-step instructions needed. Would I have to use that Grub thing?

---

### Post by binbash on 2009-02-27
sudo gedit /boot/grub/menu.lst

Play with timeout : 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

make it 10 if you want 10 sec delay etc.

---

### Post by Tek-E on 2009-02-27
Now I am not completley sure about this.....
but I think you may need to edit the menu.lst file and change the time.

I am away from my actual computer right now so I cant be of any further asistence in giving you the exact instructions to do so. But If you havnt been helped  by the time I can get back to my own personal computer I would be more than happy to guide you through the steps. :)



-- Looks like binbash solved it.
   Best of Luck to you :)

---

### Post by jwbrase on 2009-02-27
You can also use synaptic to download startup manager if you want a GUI interface for dealing with that.

---

### Post by blackened on 2009-02-27
> **eBrY said:**
> Would I have to use that Grub thing?

You use "that Grub thing" every time you boot your computer. Granular control of the boot cycle is your friend, you've just been led astray.

> **binbash said:**
> sudo gedit /boot/grub/menu.lst

Play with timeout : 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

make it 10 if you want 10 sec delay etc.

This is the preferred method, but if you absolutely *need* a graphical frontend, then there is Startup Manager:

```
sudo apt-get install startupmanager
```

---

### Post by eBrY on 2009-03-03
Thanks I used the manual way. Good way to learn, thanks for the support appreciate it!

---

