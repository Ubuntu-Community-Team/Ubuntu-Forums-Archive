---
title: "Xubuntu 64Bit - Smart Package Manager - Adding Hardy Channels"
date: 2008-07-24
forum: Desktop Environments
---

### Post by ### puhleez ### on 2008-07-24
Hello all,

Forgive me if I should have posted this in another area of the Ubuntu forums. Perhaps it belongs in "General"?

I have searched the forums here and googled until my fingers became bloody stumps for the last couple of days but I cannot find any clear explanation on how to do this.

I've used Ubuntu exclusively for over 2 years now and just recently decided to try Xubuntu because I wanted to try a distro that had Xfce as default. Upon discovering the Smart Package Manager while getting the medibuntu repositories I have grown to prefer it over Synaptic. 

But I, for the life of me, cannot figure out how to add the standard Ubuntu repositories (main, restricted, universe, etc) to Smart PM (they are called 'Channels' on Smart. I would like to do this so I can do everything from one package manager.

The last Q in the FAQs at the Smart homepage ([http://labix.org/smart/faq](http://labix.org/smart/faq)) reads:
------------------------------------

How do I convert a sources.list from APT into Smart channel info?

Smart is able to do synchronize channels from APT automatically. To enable that, run the following command:

smart config --set sync-apt-sources=yes

You can also try a script called aptosmart. The site is in german, but the script is in english, and it's pretty simple to use. (This is a contributed 3rd party script, not related to Smart development).

There is also another one coded by Pascal Blesser. 
------------------------------

I ran the command as root and I think it was successful because I got my root prompt back without any error messages. 

I also tried the Pascal Blesser Script by: 1)downloading it to my Desktop, 2)making it executable using "sudo chmod +x file-name.sh" and finally, 3)executed it using "sudo ./file-name.sh" This also returned me to the root prompt without any error message.

My questions are:

A) What does that first command do? (what does mean to 'sync channels from APT?) Did it convert the deb information from Synaptic and save it in a file somewhere that I need to find and uncomment something? If so, where is that file?

B) Regarding the shell script. Is there a problem with executing the shell script from my Desktop as root or should I have moved it to a protected system file first (which is what I have had to do the few other times I needed to deal with making a .sh file in the past)?

I guess I was hoping that one of these methods would have converted the package information from Synaptic-ese and plopped it into my Smart PM Channel list.

C) There is a method for manually adding each repository the fields to enter data are:
Alias
Name
Priority
Base URL
Distribution
Components
Fingerprint

I am pretty sure that "Alias" and "Name" are not critical in the sense that I just have to use exact terminology on the other hand, I would suspect that "Base URL" would be critical (eg. [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/)). What about the remaining fields... are they critical?


Sorry for the novelette.... just trying to provide enough info to help you help me.

Thanks.

Oh yeah... one more thought: The only good thing about current gasoline prices is that every time I fill up my tank my vehicle doubles in value!!

---

### Post by bgerlich on 2008-07-24
The easiest way to get it to work with hardy repos is, as you mentioned, to synch it with apt. The program simply reads apt config files, sources.list too, and adds the repositories found there as Smart channels. The scripts do exactly the same. Second script simply runs 'smart channel --add' with parameters extracted from sources.list . The first one creates .channel file in the smart config dir with the content extracted form sources.list. If for some reason it doesn't work for you there is an off chance that you have all repos commented out in sources.list. Other than that I can't say anything more - I'm not so keen on using Smart, tried once some time ago.

---

### Post by ### puhleez ### on 2008-07-25
Hey bgerlick..... thanks for the info. I thought the scripts would convert and add the Synaptic repos as Smart Channels but they never showed up there. Oh well, I guess I'll just stay with Synaptic.

Thanks again

---

