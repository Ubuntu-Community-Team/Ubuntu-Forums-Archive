---
title: "Ubnuntu Applications Crashed Due Installation of Ubuntu Tweak"
date: 2010-10-31
forum: Desktop Environments
---

### Post by kartikjagdale on 2010-10-31
My  all ubuntu Apllications crashed and Dosen't open Due to insatllation of ubuntu-Tweak

and now I am not able to Uninstall it.

It Gives a fatal Error for the application\Applets in Ubuntu when I try to open them

[U][COLOR=Black]For Update-Manager


[/COLOR][/U][COLOR=Black]'E:Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.lst(dist parse)'



_For Synaptic-Package-Manager_[/COLOR]

[COLOR=Black]'E:Malformed line 1 in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.lst(dist parse)'
E:the list of sources could not read.
Go to the repository dialogue to correct the problem
E:_cache->open()failed,please report.

and also many application close without informing the error like 
"Ubuntu Software centre"
"Computer Janitor" etc..

Please Help Me to solve the problem.

[/COLOR]

---

### Post by kartikjagdale on 2010-10-31
I solved the problem, in case anyone else runs into this as well -

First I removed ubuntu-tweak by using
code:

sudo dpkg -r ubuntu-tweak

I right clicked on the Update Manager and went into Preferences >  Software Sources, and unchecked the Ubuntu-Tweak source. It closed out,  then I reopened Update Manager, and it worked :grin:

I'm thinking it's because Ubuntu-tweak isn't supported for Meerkat?

---

### Post by cpmman on 2010-10-31
Ubuntu-tweak is supported in Maverick Meerkat - you had a corrupted source listing for some reason.  Try again and it should work.

---

