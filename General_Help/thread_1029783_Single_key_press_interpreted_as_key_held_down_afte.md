---
title: "Single key press interpreted as key held down after Intrepid upgrade"
date: 2009-01-03
forum: General Help
---

### Post by james_mcl on 2009-01-03
I've just installed Intrepid, and now have a dual-boot system with Gutsy being the other OS. (Just plain Ubuntu, not Kubuntu or any of the other variants, in both cases)

A couple of times now, when I've been typing something, I will press a key and the system seems to think I'm still holding it down after I've let go - so if I've got a textfile open and I highlight a block of text and press delete, the cursor can be seen marching backwards through the rest of the file deleting everything in its path. Or I'm typing 192.168.0.1 and suddenly Firefox's address bar is being filled with 1s.

The problem only occurs in Intrepid, not Gutsy. I've observed this happening in gedit and one other application, although I can't now remember if that was Synaptic, Firefox, or something else altogether.

After it happened in the other application, I had to reinstall (for a different reason), however the problem has persisted in spite of this.

I'm using a laptop, so the keyboard layout isn't *absolutely* standard, for instance I have to be holding down a [FN] key to make Print Screen work, but I don't know if that could have anything to do with it.

Thanks for any help,

James McLaughlin.

PS. I'm planning to get a triple-boot set up so that I can see if this problem occurs in Hardy.

---

### Post by Def13b on 2009-01-03
Could be something else entirely but just in case, I had what sounds like the same problem on my laptop, I tried with both Ubuntu and Xbuntu 8.04. 

Eventually I narrowed it down to only occurring if I was connected to my wireless router via DHCP (laptop is using a PCMCIA card), if I connect with a static IP no problems at all, change it back to DHCP and I get the keyboard issues you mentioned. 

I don't know why this is or if it's something else and the wireless thing is just a freak coincidence but having moved to static IP I've not once seen the problem again.

---

### Post by theozzlives on 2009-01-03
adjust the repeat time in keyboard under preferences on the system menu

---

### Post by james_mcl on 2009-01-03
This is interesting. I'm connected to a wireless network, and while I don't have a static IP on either install, they do both handle wireless differently. My Gutsy installation's using ndiswrapper, and my Intrepid install's using b43-fwcutter.

(I've now given myself a static IP in Intrepid to see if that solves the problem, btw)

Thanks,

James.

> **Def13b said:**
> Could be something else entirely but just in case, I had what sounds like the same problem on my laptop, I tried with both Ubuntu and Xbuntu 8.04. 

Eventually I narrowed it down to only occurring if I was connected to my wireless router via DHCP (laptop is using a PCMCIA card), if I connect with a static IP no problems at all, change it back to DHCP and I get the keyboard issues you mentioned. 

I don't know why this is or if it's something else and the wireless thing is just a freak coincidence but having moved to static IP I've not once seen the problem again.

---

### Post by james_mcl on 2009-01-04
No luck so far, in fact an even worse version of the problem just happened. While I was in Firefox, without my even pressing anything the system suddenly acted like I was holding down the Enter key. Closing Firefox didn't affect this, my documents in gedit began to be filled with line breaks - and because it's the enter key, when I closed the documents gedit thought I'd said yes to saving these changes!

---

