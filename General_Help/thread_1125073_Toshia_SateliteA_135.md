---
title: "Toshia SateliteA 135?"
date: 2009-04-14
forum: General Help
---

### Post by msohn88 on 2009-04-14
My sister won't need her Toshia Satelite A135 anymore so I decided to buy it from her, but I am wondering if this machine would support Ubuntu flawlessly.

The keyboard seems like it's designed for Windows Vista.

Processor: Genuine Intel(R) CPU T2080 @ 1.73GHz
Memory (RAM): 1014 MB
System Type: 32-bit Operating System

I hate Windows Vista, should I keep it or I can install Ubuntu and work flawlessly?

---

### Post by Zack McCool on 2009-04-14
Ubuntu should work fine on it.  I have an A215, and there isn't a single hardware problem with Intrepid...

The closest you might come to a problem is getting wireless to work, which might require the addition of the backports and the blacklisting of the ath_pci module.  

That is, of course, assuming that the A135 has an Atheros wireless chipset...

---

### Post by msohn88 on 2009-04-14
> **Zack McCool said:**
> Ubuntu should work fine on it.  I have an A215, and there isn't a single hardware problem with Intrepid...

The closest you might come to a problem is getting wireless to work, which might require the addition of the backports and the blacklisting of the ath_pci module.  

That is, of course, assuming that the A135 has an Atheros wireless chipset...

Some people said that the sound is not working though...

How did you fix the wireless problem? ath_pci module? What is that?

---

### Post by Zack McCool on 2009-04-14
I have not had a problem with sound since Hardy.  This is a different model, though, so your mileage may vary.

As for the wireless, it's pretty simple.

First, add the proper backports repo in /etc/apt/sources.list by uncommenting the line

```
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse 
```

(If you are using intrepid, replace hardy with intrepid throughout this message...   ;) )

Then, install the backports modules
```

sudo apt-get update
sudo apt-get install linux-backports-modules-hardy

```

Now, check to see if wireless is working.  If not, disable the ath_pci module:

```

sudo modprobe -r ath_pci

```

Then, edit the file /etc/modprobe.d/blacklist , go to the end of the file, and add the following line:

```

blacklist ath_pci

```

Try again.  You may need to reboot your PC at this point (I never have, but some have reported that they did).

If it's still not working at this point, let me know.

Also, this is only if the machine is using an atheros chipset.  If it's not, this won't help you at all...

---

### Post by msohn88 on 2009-04-14
> **Zack McCool said:**
> I have not had a problem with sound since Hardy.  This is a different model, though, so your mileage may vary.

As for the wireless, it's pretty simple.

First, add the proper backports repo in /etc/apt/sources.list by uncommenting the line

```
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse 
```

(If you are using intrepid, replace hardy with intrepid throughout this message...   ;) )

Then, install the backports modules
```

sudo apt-get update
sudo apt-get install linux-backports-modules-hardy

```

Now, check to see if wireless is working.  If not, disable the ath_pci module:

```

sudo modprobe -r ath_pci

```

Then, edit the file /etc/modprobe.d/blacklist , go to the end of the file, and add the following line:

```

blacklist ath_pci

```

Try again.  You may need to reboot your PC at this point (I never have, but some have reported that they did).

If it's still not working at this point, let me know.

Also, this is only if the machine is using an atheros chipset.  If it's not, this won't help you at all...

Thanks, but I have a few more questions before I install Ubuntu on this machine.

How did it work with converting MP3 files through your CDs? For me, AmaroK did not worked, so I used Grip.

I don't know if the software's program or not.

The reason I want to install Ubuntu is that Windows is not safe and can get virus easily and whatever I have in this machine can be easily looked by Microsoft company, from that's what I heard.

---

### Post by Zack McCool on 2009-04-16
I've never had a problem converting CD's to mp3's.  Amarok works for me, but you may not have all of the right codecs installed...

There are several programs that can do this, though.  I like command-line tools myself...

rip the music, then run lame...

---

