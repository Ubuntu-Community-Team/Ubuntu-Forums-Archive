---
title: "Help Firefox - Adobe"
date: 2009-04-09
forum: General Help
---

### Post by mortex on 2009-04-09
Hi
I have an IBM T23 30gb HD with 1g ram 
I installed 7.10 and was quickly on the internet
I did the update 8.4 LTS everything went quick and easy

went to youtube.com and it requested I download Adobe flash
I did and got an error 
tried many things with the help of a friend who uses ubuntu often and still no luck 

Tried Xubuntu and could not access the internet 
looked in tools / network etc... still nothing 

Switched to 8.10 and again no internet tried everything I could and questioned 3 others who use 8.10 often still no luck

Switched back to 7.10  (( internet up and running )) Updated 8.4 LTS -- Tried updating Firefox No good 
tried updating abobe No good 

I need help -- I am very new at linux so please be understanding
and help walk me through this thanks 
I am in NY and would be happy to talk over the phone 
[email]mortex43@yahoo.com[/email] 
Thanks for all your help

---

### Post by lavinog on 2009-04-09
I don't think you can install flash with the firefox plugin manager.
You can do it with apt or synaptic:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by acimmarusti on 2009-04-09
I suggest to get the ubuntu restricted extras which include flashplayer and a bunch of codecs for mp3 and video playback. Also DVD playback!

```

sudo apt-get install ubuntu-restricted-extras

```

---

