---
title: "Need help running dvd's"
date: 2005-08-04
forum: Gaming &amp; Leisure
---

### Post by smoshe on 2005-08-04
Hey guys,
I started with a default instalation of Ubuntu this weekend, and have been wracking my brain, installing every package I could think of, and still no luck running dvd's on my system. 

Anyone know of any tutorials or howto's out there in regard to getting Ubuntu to read DVD's?

Thanks.

-Sam

---

### Post by codejunkie on 2005-08-04
[QUOTE=smoshe]Hey guys,
I started with a default instalation of Ubuntu this weekend, and have been wracking my brain, installing every package I could think of, and still no luck running dvd's on my system. 

Anyone know of any tutorials or howto's out there in regard to getting Ubuntu to read DVD's?

Thanks.

-Sam[/QUOTE]

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback) you should also install totem-xine you can do that through synaptic because the version of totem included with ubuntu doesn't support protected formats, also install these codec packages as well this guide will help with that [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) hope this helps.

---

### Post by smoshe on 2005-08-05
Thanks for the help.

Tried everything in the instructions.
I am able to play mpegs now :) which is nice, but dvd playback is still not working.

Installed Xine, and re-installed Totem.

Totem is giving me this error:

Totem could not play 'dvd://'.
Could not read from resource.

and Xine is telling me the source can't be read, and continues to expound on user rights. I should have the rights to the whole system. I'm logged in as my primary user.

If it helps, I'm using my copy of Elmo in Grouch Land as my test disk.

---

### Post by codejunkie on 2005-08-05
[QUOTE=smoshe]Thanks for the help.

Tried everything in the instructions.
I am able to play mpegs now :) which is nice, but dvd playback is still not working.

Installed Xine, and re-installed Totem.

Totem is giving me this error:

Totem could not play 'dvd://'.
Could not read from resource.

and Xine is telling me the source can't be read, and continues to expound on user rights. I should have the rights to the whole system. I'm logged in as my primary user.

If it helps, I'm using my copy of Elmo in Grouch Land as my test disk.[/QUOTE]

if you just reinstalled the package "totem" that comes with ubuntu it wont play dvd's install the package totem-xine in synaptic this will remove the default totem package that comes with ubuntu but if you have the packages totem-xine and libdvdcss2 installed it should play dvd's.

---

### Post by smoshe on 2005-08-05
Yep,
I've got all of it.
Totem has been re-installed per your suggestion.

I hate to ask an ignorant question,
but are there any dvd hardware settings or permissions that could be causing this problem? 

All of the software (and then some) is installed and working.

I should be logged in as root.
Do you think it could somewhow be disabled somewhere?

---

### Post by grofaz on 2005-08-06
I had the same hurddles to jump getting DVD playback with totem. I replaced the totem-gstreamer version with totem-xine and used apt-get to install libdvdcss2. Without libdvdcss2 totem-xine will not playback DVDs either. You need the extra-repositories list or libdvdcss2 will not be found. Good luck!

---

### Post by smoshe on 2005-11-17
Thanks for help guys.
Took your advice, and it works like a charm. Downloaded the latest libdvdcss and I have amazing clarity with dvds.

---

### Post by MemoryDump on 2005-11-18
[QUOTE=codejunkie]if you just reinstalled the package "totem" that comes with ubuntu it wont play dvd's install the package totem-xine in synaptic this will remove the default totem package that comes with ubuntu but if you have the packages totem-xine and libdvdcss2 installed it should play dvd's.[/QUOTE]

tried this method and I and I still get a prompt stating libdvdcss isn't installed. 
I doubt I have to reboot for these changes to be applied right? am I missing something?
thxs
-MD

---

### Post by smoshe on 2005-11-19
I really hate totem.
It's a terrible player. It doesn't work. Xine-ui is far superior. :)  Installing the libdvdcss should take effect instantly. But totem doesn't want to seem to work no matter what you do. Darned thing. Might want to try xine-ui, probably your best bet.

---

### Post by Nebutron on 2008-01-24
> **MemoryDump said:**
> tried this method and I and I still get a prompt stating libdvdcss isn't installed. 
I doubt I have to reboot for these changes to be applied right? am I missing something?
thxs
-MD

I'm in a similar boat.  Here is the output I get when I try to install libdvdcss from the terminal:

---

### Post by Nebutron on 2008-01-24
> **Nebutron said:**
> I'm in a similar boat.  Here is the output I get when I try to install libdvdcss from the terminal:

Okay,  trying again with the attachment.

---

### Post by Sandlst on 2008-01-25
Have you setup the medibuntu repository?  If not, follow this link: [http://www.medibuntu.org/]("http://www.medibuntu.org/")
Look under "Repository Howto."

---

### Post by Zack McCool on 2008-01-25
```

sudo apt-get install build-essential
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```

It is possible (likely, even) that the first 2 are already installed on your system.  I include them so that you make sure first.

The install-css.sh script will connect to the internet, download libdvdcss2 and install it.  After that, you should be all set.

---

