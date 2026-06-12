---
title: "I have to tell you"
date: 2005-09-11
forum: Desktop Environments
---

### Post by AC0H on 2005-09-11
[RANT]The documentation for these distributions is in terrible shape.
I have read no fewer than 5 different FAQ's on getting the flash and java plugins installed. None work but that's to be expected when entire repositories are shuffled around like playing cards for no better reason than it might be Wednesday. GET YOUR S*** TOGETHER!
Also ran through the "setting up repositories" FAQ. My installed version of Synaptic doesn't look ANYTHING like the one in the FAQ. Whoever is in charge of keeping the docs up to date needs firing. And before you get all upity and call me a newby I'll let you know I've been doing this longer than a lot of you have been alive.[/RANT]

Looks like it's back to Gentoo.

---

### Post by Leif on 2005-09-11
well, at least you took the logical step of asking for clarification and help on this forum instead of going on a rant... good for you !

---

### Post by escuchamezz on 2005-09-11
sack mark shuttleworth, sign bill gates

---

### Post by tseliot on 2005-09-11
[QUOTE=AC0H][RANT]The documentation for these distributions is in terrible shape.
I have read no fewer than 5 different FAQ's on getting the flash and java plugins installed. None work but that's to be expected when entire repositories are shuffled around like playing cards for no better reason than it might be Wednesday. GET YOUR S*** TOGETHER!
Also ran through the "setting up repositories" FAQ. My installed version of Synaptic doesn't look ANYTHING like the one in the FAQ. Whoever is in charge of keeping the docs up to date needs firing. And before you get all upity and call me a newby I'll let you know I've been doing this longer than a lot of you have been alive.[/RANT]

Looks like it's back to Gentoo.[/QUOTE]
1) Avoid drinking too much coffee please.  :razz: 
2) If you have a question we are here to help
3) How come an expert like you can't manage to make synaptic work even after reading Ubuntu Starter's Guide(which is just a matter of "copy and paste")? Did you read it, did you?

---

### Post by snarkout on 2005-09-11
I do have to agree that putting badly needed package fixes in the kubuntu.org repositories, which are absolutely not common knowledge, is very bad form.  Is there some reason these fixes weren't put in regular repositories?  It becomes very difficult to run a system, and by extension help other people run their systems, when the fixes could best be described as obfuscated.

---

### Post by AC0H on 2005-09-11
> How come an expert like you can't manage to make synaptic work even after reading Ubuntu Starter's Guide(which is just a matter of "copy and paste")? Did you read it, did you? 

Yep sure did. DIDN'T WORK! The document is clearly out of date which is no surprise when stuff gets moved on a whim. The guy/gal who does the moving needs to update the docs or make sure it gets done before going live with the changes. Thats how the real world works.

As an example this entire page is useless as tits on a boar,[]Linkage](HTML=https://wiki.ubuntu.com/AddingRepositoriesHowto) . Open up Synaptic, go to seetings menu, select repositiories and then tell me exactly where the "settings" button is.


> I do have to agree that putting badly needed package fixes in the kubuntu.org repositories, which are absolutely not common knowledge, is very bad form. Is there some reason these fixes weren't put in regular repositories? It becomes very difficult to run a system, and by extension help other people run their systems, when the fixes could best be described as obfuscated. 

Exactly although obfuscated isn't the word I'd choose to describe it.

---

### Post by Leif on 2005-09-11
[QUOTE=AC0H]As an example this entire page is useless as tits on a boar,[]Linkage](HTML=https://wiki.ubuntu.com/AddingRepositoriesHowto) . Open up Synaptic, go to seetings menu, select repositiories and then tell me exactly where the "settings" button is.[/QUOTE]

I'm sorry but we clearly have different versions of synaptic. I see Settings clearly where you describe it - at the bottom, second from the left. Are you sure you're running synaptic and not kynaptic ?

---

### Post by rjwood on 2005-09-11
Who do you think you are acoh. Maybe you can speak to your grandchildren or children like that and get away with it. Maybe the first thing you need to learn is communication skills. The people involved in this dist. are pretty hard working people. You think that carrying on like a hard ass sports coach is going to get people doing what you want them to do. If you have suggestions then go to the appropriate forum and document it. People like you show up someplace and just want all the attention. GROW UP!!:smile: And speak to people with respect.
Thanks for the oportunity to say that...

---

### Post by tseliot on 2005-09-11
[QUOTE=AC0H]Yep sure did. DIDN'T WORK! The document is clearly out of date which is no surprise when stuff gets moved on a whim. The guy/gal who does the moving needs to update the docs or make sure it gets done before going live with the changes. Thats how the real world works.

As an example this entire page is useless as tits on a boar,[]Linkage](HTML=https://wiki.ubuntu.com/AddingRepositoriesHowto) . Open up Synaptic, go to seetings menu, select repositiories and then tell me exactly where the "settings" button is.


 

Exactly although obfuscated isn't the word I'd choose to describe it.[/QUOTE]
As I said before, please crack down the amount of cups of coffee you drink. And I suppose (and HOPE) it's only caffeine that makes you behave in this in this way. This means: calm down please.

About synaptic: I don't think the document is out of date (as it also deals with Breezy, the unstable version of Ubuntu).

This is Ubuntu starter guide
URL: [http://ubuntuguide.org](http://ubuntuguide.org) 
Mirror: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

If you wanted to enable or add the repositores

This is a quotation from the guide

Q: How to add extra repositories?
Read General Notes

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
Find this section 

...
## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
Replace with the following lines 

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Save the edited file (sample)

sudo apt-get update

Go and see the entire instructions

---

### Post by matthew on 2005-09-11
[QUOTE=AC0H][RANT]The documentation for these distributions is in terrible shape.
I have read no fewer than 5 different FAQ's on getting the flash and java plugins installed. None work but that's to be expected when entire repositories are shuffled around like playing cards for no better reason than it might be Wednesday. GET YOUR S*** TOGETHER!
Also ran through the "setting up repositories" FAQ. My installed version of Synaptic doesn't look ANYTHING like the one in the FAQ. Whoever is in charge of keeping the docs up to date needs firing. And before you get all upity and call me a newby I'll let you know I've been doing this longer than a lot of you have been alive.[/RANT]

Looks like it's back to Gentoo.[/QUOTE]
May I politely remind you that in society one does not curry favor with others by behaving in such a rude manner. You are obviously frustrated and I find that regrettable as it is not the goal of anyone here to cause such feelings. However, speaking in such a way as you have does not elicit from me feelings of symapthy nor a desire to assist you. On the contrary, you are far more likely to either provoke angry words from some and cause others to simply ignore you. In either case you do not receive the help you need.

Please try again. Ask your question in a calm, civilized manner as a very welcome and desirable member of the community--treat others with the same kindness and respect as you would like and you will find this group to be an incredibly able and friendly resource. Or, you can follow your own suggestion and go "back to Gentoo" or anywhere else you like. Don't treat people poorly and expect respect.

---

