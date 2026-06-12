---
title: "Cannot install nant"
date: 2009-01-30
forum: General Help
---

### Post by makosanders on 2009-01-30
I need to install nant to compile SDL.NET, anyway, this is what happens;

I say;```

mako@windEEE:~$ sudo apt-get install nant
[sudo] password for mako: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nant: Depends: libmono-dev (>= 1.1.6) but it is not going to be installed
E: Broken packages
```


So then I say, and I don't know if this is right but I try it;
```
mako@windEEE:~$ sudo apt-get install libmono-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmono-dev: Depends: libglib2.0-dev but it is not going to be installed
E: Broken packages
```


And so on;
```
mako@windEEE:~$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.16.3-1) but 2.16.4-0ubuntu3 is to be installed
E: Broken packages
mako@windEEE:~$ sudo apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


What's wrong here? :(
I've looked around for help and all I found was a bug report on this but it got closed for no observable reason.

I'm using Ubuntu-EEE by the way.

---

