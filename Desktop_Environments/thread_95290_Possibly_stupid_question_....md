---
title: "Possibly stupid question ..."
date: 2005-11-26
forum: Desktop Environments
---

### Post by painreliever on 2005-11-26
... I'm very, VERY new to Linux, so apologies if I come across as a complete ignoramus.

I upgraded to Ubuntu 5.1 from Windows 98 three days ago at the recommendation of a friend, as he was amused at my frustration with Win98 and my refusal to upgrade to XP (I HATE Windows).

I have to say, overall I'm very impressed with my first exposure to Linux - very clean and Mac-like. Works quick even on my relatively slow computer (Pentium III 733mhz overclocked to 840mhz, 384MB RAM), I'm liking it a lot.

I am, however, fairly bemused by the 'Terminal' interface.

Basically, I'm having a hell of a time getting my modem installed. It's a Sagem Fast 800 USB ADSL modem, and luckily the install CD comes with Linux drivers for it and a (quite) helpful PDF file giving step-by-step instructions (and screenshots) of what to type into Terminal to get these drivers installed. 

However, I can only get about halfway through. After installing the patch (which I presume contains the drivers), I'm told to enter the command "./configure", which I presume configures the drivers (see, I'm catching on!). It's at this point that it throws a spaz and tells me that "No acceptable C compiler was found in $PATH".

Now, the PDF file says that I must have GCC Compiler installed, which I have. It was installed along with Ubuntu and lives in /usr/lib/gcc. However, it can't seem to recognise that, so I'm left without internet access at home.

I'd really like to keep Ubuntu as I really like it, but unless anyone can help with this I may as well bite the bullet and put Win98 back on.

Cheers!

---

### Post by GeneralZod on 2005-11-26
There are no stupid questions in Linux :) 

To get a compiler installed, do

```

sudo apt-get install build-essential

```

If the problem still persists, try

```

sudo apt-get install gcc-3.4

```

Breezy is unique in that you actually need *two* separate versions of the compile; one for ordinary apps, and the other for drivers.  This will hopefully be fixed in time for Dapper.

Hope this helps,
Simon

Edit:

Oh bugger - I guess you don't have internet access under Ubuntu at the moment...? That might be someone awkward, I'm afraid :/ build-essential is actually stored on the CD itself so requires no net access, but I'm not sure if this is the case for gcc-3.4.

---

### Post by GrumpyBob on 2005-11-26
I think what's needed here is to install build-essentials:
sudo apt-get install build-essentials

However, unless these are on the CD, you are still stuffed since you'd need a functional modem.
Probably some wiser person than me can advise further.

Robert

---

### Post by squidward on 2005-11-26
I know it's not the answer you asked for (you want to get your modem running):  if serious about LX, you should consider a external modem.

Economical options: [http://search.ebay.com/search/search.dll?from=R40&satitle=linux+modem]("http://search.ebay.com/search/search.dll?from=R40&satitle=linux+modem")

Or if money (and customer service) is not a factor, take a trip down to CompUSA.

Good luck.

---

### Post by akiro.yamamoto on 2005-11-26
Actually BOTH GCC 3.4 and 4.0 are on the CD.
I can't remember if it's done when you install build-essential but I think you will also need the kernel headers for your system.
Try This :   Click ON ==>>

System >> Administration >> Synaptic Package Manager

And do a search or browse for what's installed and whats available from the Install CD

Regards
:smile:

---

### Post by stalefries on 2005-11-26
Actually, ./configure has to do with configuring the source code so that one can compile it, or something along those lines. It'd be nice if you could give us the output of 
```
echo $PATH
```
as that should give us some clue of what your problem might be.

---

### Post by painreliever on 2005-11-26
Thanks everybody for your help!

As it turns out, it was a couple of problems at the same time:

sudo apt-get install build-essential helped get me further, but it turned out I still had the wrong version of GCC as I hadn't downloaded the correction to v3.4 for Ubuntu 5.1 from here. Got on the phone to the girlfriend, got her to download it, installed it and it worked like a charm!

I'm on it now, and it's fair zipping along ... much faster than under Win98 - I always knew my 1Mb connection should've been faster than it seemed!

Cheers again! :D

---

