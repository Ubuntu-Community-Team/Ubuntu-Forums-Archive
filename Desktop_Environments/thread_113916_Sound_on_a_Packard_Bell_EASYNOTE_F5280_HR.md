---
title: "Sound on a Packard Bell EASYNOTE F5280 HR"
date: 2006-01-07
forum: Desktop Environments
---

### Post by grandmaster on 2006-01-07
For those of you that have installed breezy on a EASYNOTE F5280 HR and the sound has not worked..
After trawling loads of forums and websites i have finally fixed it for me and thought i would share this info...

This may also apply if you have a sis southbridge sound card chip...

First download the alsa drivers,libs & utils  from the site.

[http://www.alsa-project.org](http://www.alsa-project.org)

I created a folder in my home directory and extracted the files from each into a seperate sub folder,

then follow the guides from this page

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+southbridge+HD-audio+and+modem.&chip=SIS966&module=hda-intel]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+southbridge+HD-audio+and+modem.&chip=SIS966&module=hda-intel")

i did this as root!

there are other guides on here that tell you how to log in as root on a gui.

after following the guides and a reeboot hey presto it worked.

I also made sure that systems,preferences,multimedia audio selector was set to alsa..

I really hope the guide works for you as it did for me..

Ubuntu Rocks!!

---

### Post by 47th_Ronin on 2006-01-07
Well done mate!

Altrough I have not used your guide, it's good too know there're people who post the solution, even after they didn't find the answer the normal way (searching forum, wiki, net etc...)

---

