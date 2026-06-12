---
title: "installation in general"
date: 2008-12-23
forum: General Help
---

### Post by garrynigel on 2008-12-23
hi
iv been a windows user for a year now.... just installed linux ubuntu 8.10
and its workin gr8...here in linux i heard dat u can not go next..next..next as in a windows software to install it.. some commands have to be run thru the terminal.. i mean other dan d synaptic packet manager.. is der a way to install softwares dat u download from other sites..like say softpedia.com ,etc to install dem.. is der like one command to install these softwares or dey differ from software to software...and if dey differ wer can i find des commands dat i neeed to install.. i checked that linux help.. starting with terminal .. but in vain...
dat day i downloaded a theme from gnome look.org.. but dese themes cant get installed. saying dat its not a valid theme..i mean i downloaded for linux rite den y not... and dat wines a headache wanted to run photoshop but wine keeps shutting down evrytime.. dont knw wat to do.. i start it..the application runs for some time and den it just closes on its own automatically.. des are just egs.. im givn.. need some help for all....
please be specific in ans ,.. coz im new to linux dnt knw much about it
thanx

---

### Post by SuperSonic4 on 2008-12-23
huh? We don't use text speak on the forums ;)

From what I gather there is no universal installer such as .msi or .exe, most package installation is done automatically via the repos and apt-get. Synaptic is a graphical package manager which you can use to search, you can either use synaptic or apt-get in the terminal there is no difference. With this you don't need to keep pressing next it will just be done at the end. .deb files are the next best thing because you can just double click and it should install although there can be dependency problems. Lastly you can compile the source code, extract the tarball and there should be a readme.txt or install.txt with instructions on.
What you type depends on the package you want ```
sudo apt-get install <package>
``` is a good start. For example ```
sudo apt-get install firefox
```.

I've no idea about theme installation since I am a kubuntu/kde user. Photoshop and wine don't get on very well from what I hear. Does the gimp satisfy your needs. I know it does for me but photoshop is better for the professional, it'd be better to use a VM with windows in or dual boot.

The multimedia how to is a good start IMO, you can get codecs and such there [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by howefield on 2008-12-23
Aye, der is de way.

but if you want a specific answer, ask a specific question.

---

### Post by garrynigel on 2008-12-23
alrite .. but der are kde themes on gnomelook.org i tried installing one once den realised it was for kde..thanx .. i knew about apt-get install .. and specify d name of d software but all dose softwares are just for the ones available.. sometimes we have to add new locations in third party softwares dey are calld as apt link...somtin like dat..
anyway thanx maan 
 dude i gave u two examples der in dat post ones for d theme d others for wine... illustrate please

---

### Post by mastergoomba on 2008-12-23
do you mind typing so people can understand you?

---

### Post by oilchangeguy on 2008-12-23
> **garrynigel said:**
> hi
iv been a windows user for a year now.... just installed linux ubuntu 8.10
and its workin gr8...here in linux i heard dat u can not go next..next..next as in a windows software to install it.. some commands have to be run thru the terminal.. i mean other dan d synaptic packet manager.. is der a way to install softwares dat u download from other sites..like say softpedia.com ,etc to install dem.. is der like one command to install these softwares or dey differ from software to software...and if dey differ wer can i find des commands dat i neeed to install.. i checked that linux help.. starting with terminal .. but in vain...
dat day i downloaded a theme from gnome look.org.. but dese themes cant get installed. saying dat its not a valid theme..i mean i downloaded for linux rite den y not... and dat wines a headache wanted to run photoshop but wine keeps shutting down evrytime.. dont knw wat to do.. i start it..the application runs for some time and den it just closes on its own automatically.. des are just egs.. im givn.. need some help for all....
please be specific in ans ,.. coz im new to linux dnt knw much about it
thanx

make sure you have enabled the multi universe repos. and most everything you'll need can be found in add/remove, or synaptic package manager. also please correctly spell all words. there are many in here whose first language is not english. and therefore may not be able to understand your post because of all of the silly slang you're using. i had to read it several times myself to understand it. this is a ubuntu forum. not the homeboy forum. so please use proper english in here. thanks!

---

