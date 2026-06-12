---
title: "Gaim with MSN"
date: 2006-06-14
forum: Desktop Environments
---

### Post by twopeak on 2006-06-14
Hello

Before updating to Ubuntu 6.06 I had Gaim beta 2.
After updating this gaim didn't allow me to use msn. So I have completely removed it from Synaptic and then reinstalled (the normal version from synaptic).
This version gave the error I need to configure SSL-support for MSN to work.

So I went and downloaded the .deb file (Gaim beta3) from [here]("http://http://people.ubuntu.com/%7Eseb128/deb/") but I get the same errors.
Now I've downloaded the source from the official Gaim site, and compiled it specifically WITH SSL support in the way the Gaim site says (*--enable-gnutls=yes*).

And I get this error again. :-x
So this is driving me completely nuts.
I believe ther emust be another thing that causes this problem, and Gaim just assumes that SSL is not suported.
Does anyone know how to make Gaim work? 
I've learned everything I could, tried everything I knew, but now I'm out of ideas...

---

### Post by morequarky on 2006-06-14
I have dapper running.   I upgraded without a CD.   I use Gaim.  Before and after upgrading I had no problems.

---

### Post by andrecasteliano on 2006-06-14
Did you check if SSL packages are installed ?
If not, install OpenSSL (libs). Use synaptic to search.

---

### Post by twopeak on 2006-06-14
[quote=andrecasteliano]Did you check if SSL packages are installed ?
If not, install OpenSSL (libs). Use synaptic to search.[/quote] I checked now, and it's installed:
* libssl 0.9.7 AND 0.9.8 
* openssl 0.9.8  
i've reinstalled both, just to be sure...
And it still doesn't work

I have the impression that it would be some kind of "standard" package like that that isn't installed here.
While doing the ./configure I get no errors of that kind, but it's only once I start Gaim it tells me it can't start.

---

### Post by twopeak on 2006-06-19
meanwhile I've done a complete remove of gaim from synaptic and removed all folders called gaim in my home directory.
And STILL gaim is in the applications list, and can start.
is it impossible to remove it completely?

And this wonderfull new search in Ubuntu now won't let you choose where to search, and doesn't find anything called gaim on my computer...
this is not good for my mental health anymore!

---

### Post by lamego on 2006-06-19
Your problem was that you have installed gaim both from apt and from the source, eventually when installing from the source it got installed into a diffrente place (depends if you have used the --prefix option from configure).
If the source makefile does not have a "uninstall" option (usually it does not) you will have to check for the files that were installed and removed them manually...

---

### Post by twopeak on 2006-06-19
That solved the issue. Seemingly, i've been opening this self-compiled beta all the time.
I located all Gaim files with "locate -i gaim",
used a root file browser to delete the files,
reinstalled the gaim from synaptic

And now i'm never going to compile anything again (*at least not for a week!*)

---

### Post by Lord Illidan on 2006-06-19
[quote=twopeak]That solved the issue. Seemingly, i've been opening this self-compiled beta all the time.
I located all Gaim files with "locate -i gaim",
used a root file browser to delete the files,
reinstalled the gaim from synaptic

And now i'm never going to compile anything again (*at least not for a week!*)[/quote] 
Perhaps you should consider Gentoo, then.. No compiling required. Or LFS.

:mrgreen::mrgreen:

---

