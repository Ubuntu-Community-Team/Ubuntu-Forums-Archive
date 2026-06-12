---
title: "Freezing"
date: 2009-04-10
forum: General Help
---

### Post by Alias1407 on 2009-04-10
Ok so i have Ubuntu 8.10 installed on my laptop, it was working fine until today.

Every so often it will completely freeze, the caps lock light is flicking on and off and i have to restart.

Is very annoying when your trying to download something and it cuts out half way. 


Any thoughts!!!

---

### Post by Kevbert on 2009-04-10
What are your system specs ?
Have you tried running memtest86+ from the grub boot menu ? It may be worth running this for a couple of passes.
Does the PC only freeze when downloading files ?
Go to Applications-Accessories-Terminal and run the following command
```
sudo apt-get install -f
```
This will check for damaged files/packages and try and fix anything that's broken. Please post back any errors.

---

### Post by Alias1407 on 2009-04-10
Intel Core 2 Duo,
2GB RAM,
Ubuntu 8.10


Will run memtest in a second

---

### Post by Alias1407 on 2009-04-10
Okay ran a memtest and it returned with no errors



Still freezing, oddly enough it only happens when i'm downloading, already tried....

```
sudo apt-get install -f
```

and...

```
sudo apt-get autoremove
```

---

### Post by Kevbert on 2009-04-10
Does it only fail on certain types of files ? Or on files greater than a certain size ? and at the same point each time ?

---

### Post by N_Nick on 2009-04-10
Could you elaborate on "downloading" ?

Are you using wget, Firefox?

---

### Post by Alias1407 on 2009-04-10
It happens when i am downloading anything, like using apt-get, firefox, synaptic......

And no not with any file size sometimes it just fails

---

### Post by Kevbert on 2009-04-10
How are you connected to the web ? If it's wireless, what's the output of ```
iwconfig 
```?

---

### Post by Alias1407 on 2009-04-10
The output of 

```
iwconfig
```

is.....


```
root@alias14-laptop:/home/alias14# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"DADS WLAN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:EE:A1:32   
          Bit Rate=60 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:77DE-483E-F438-5338-4D6C-8226-E65C-DB86-A482-C65D-382C-7835-8646-5C7D-48BB-72A9 [2]   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level:-39 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by N_Nick on 2009-04-11
You could try downloading something while on a wired connection and see if it still freezes

---

### Post by Kevbert on 2009-04-11
Wireless seems fine.Don't know what your problem is caused by. :confused::confused::confused:

---

### Post by 3rdalbum on 2009-04-11
After a crash, can you please check the Gnome System Log program, under the "kern.log" heading, to see if the kernel has given you any information about what caused the crash?

I suspect some naff wireless drivers; if you haven't already you should apply any pending kernel updates, and if you have manually compiled your wireless driver you should try recompiling it.

---

