---
title: "Laptop - ATI Chipset 200m"
date: 2009-03-08
forum: General Help
---

### Post by RudolfMDLT on 2009-03-08
Hi there,

Busy reformatting from a failed fglrx driver install.

Hardware Spec:
[Sahara Laptop]("http://www.sahara.co.za/Product_notebooks2.html?id=556637")
System running an ati chipset - [ATI 200M Series]("http://ati.amd.com/products/radeonxpress200mintel/index.html")
(Originally I thought it an intel board with an ati card on. to my horror *lspci -v* flooded my screen with ati devices!)
1 Gig of DDR2 Ram

Running Ubuntu 8.04 on the laptop with all restricted drivers and updates installed. The sound doesn't work, the fglrx driver failed completely and the system hangs every now and then - specifically when I try to play music or when I try to copy something off the network. 

I have been able to find a guide on the alsa web page to fix my sound issues.
I will leave the ati card in peace running the open source drivers! :)
I need help getting the system stable. Does anybody have experience with ati chipsets in general or more specifically, this chipset? Any advice on which log files to watch? Tweaks and other tips welcome!

Thanks for your time and any replies,

Rudolf

---

### Post by misfitpierce on 2009-03-08
All I can say is I have that chipset and had no problems on 8.04. Am on 8.10 and still having no problems with that chipset using the built in restricted driver for the ATI card. I made sure to update the updates before installing restricted drivers and it worked fine. So I am not sure exactly why you are having problems with it.

---

### Post by RudolfMDLT on 2009-03-08
I'm glad you have no issues! There is hope! ;)

How did you install the ati drivers? From the ati website or using the restricted driver tool?

If you could spare a minute - what sound card do you have?
*lspci -v* - what does the output say you have as a sound card?

Thank you for your time,

Rudolf

---

### Post by arunthopil on 2009-03-19
> **RudolfMDLT said:**
> Hi there,

Busy reformatting from a failed fglrx driver install.

Hardware Spec:
[Sahara Laptop]("http://www.sahara.co.za/Product_notebooks2.html?id=556637")
System running an ati chipset - [ATI 200M Series]("http://ati.amd.com/products/radeonxpress200mintel/index.html")
(Originally I thought it an intel board with an ati card on. to my horror *lspci -v* flooded my screen with ati devices!)
1 Gig of DDR2 Ram

Running Ubuntu 8.04 on the laptop with all restricted drivers and updates installed. The sound doesn't work, the fglrx driver failed completely and the system hangs every now and then - specifically when I try to play music or when I try to copy something off the network. 

I have been able to find a guide on the alsa web page to fix my sound issues.
I will leave the ati card in peace running the open source drivers! :)
I need help getting the system stable. Does anybody have experience with ati chipsets in general or more specifically, this chipset? Any advice on which log files to watch? Tweaks and other tips welcome!

Thanks for your time and any replies,

Rudolf




Hi

 i think i cud help you...................   read my blog......... i fixed the same kind of issue with my ATI radeon chipset......... i am sure this will help you to fix with an ease effort

[http://thopilismaakan.blogspot.com/:D](http://thopilismaakan.blogspot.com/:D)

---

### Post by RudolfMDLT on 2009-03-31
> **arunthopil said:**
> Hi

 i think i cud help you...................   read my blog......... i fixed the same kind of issue with my ATI radeon chipset......... i am sure this will help you to fix with an ease effort

[http://thopilismaakan.blogspot.com/:D](http://thopilismaakan.blogspot.com/:D)

Hey - sorry man, been writing exams. I just looked in on the blog now and BlogSpot tells me that it can't find the blog? Could you maybe paste the info here?

Thanks,

Rudolf

---

### Post by orethrius on 2009-03-31
The blog is here, smilies may have interfered with a bad URL tag.
```
http://thopilismaakan.blogspot.com/
```

---

