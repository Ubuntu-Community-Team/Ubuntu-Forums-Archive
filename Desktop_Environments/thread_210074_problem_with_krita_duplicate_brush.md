---
title: "problem with krita duplicate brush"
date: 2006-07-06
forum: Desktop Environments
---

### Post by the slayer on 2006-07-06
Ive just installed krita, and damn it looks good!
But ive got a problem with the dublicate brush!! 
When i use it i shift click on the place to clone form, but when i left click to start the clone, it only paint in white! No cloning!
Using krita 1.5

Any idea why?

---

### Post by the slayer on 2006-07-07
No one?

---

### Post by the slayer on 2006-07-09
Damn ive googled, looked in hundreds of forums, talked over irc, no one NO ONE has problem with the dublicate brush!

---

### Post by clarencel on 2006-11-16
I have the same problem, and I'm using Kubuntu Dapper on an IBM thinkpad R50e. I'm just going to go back to the gimp.

---

### Post by Braunstonian on 2006-11-18
I had the same problem and after messing about this afternoon found that you will need to upgrade to Krita (Koffice) 1.6.

As I use Open Office I didn't want to install all of KOffice, but obviously wanted to use Krita. I did this by going to:

[http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.6.0/kubuntu/pool-dapper/koffice/](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.6.0/kubuntu/pool-dapper/koffice/)

Downloading the appropriate versions for my PC of

koffice-data
koffice-libs
krita-data
krita

Then in the terminal using dpkg -i <package name> to install them, in the order listed above.

NOTE: I already had Krita 1.5 installed (via Synaptic) and just installed the above over the top of this version. 

So far it works fine, and more importantly the clone brush tool works now.

Out of the other paint programs available for Kubuntu I started out using GIMP. Which is OK if a bit fiddly. But I wanted CMYK support, so searched for something else. Eventually I came up with Cinepaint and Krita. Having tried both of those I found Krita offered more functions and was easier to use than Cinepaint AND Gimp.

HTH

John.

---

### Post by Braunstonian on 2006-11-19
**CORRECTION OF MY ABOVE MESSAGE**

It seems doing the above causes Krita 1.6 to crash when using the filters.

So - I've now found that installing the following from the above URL sorts out the problem. DO NOT INSTALL THESE OVER THE TOP OF AN EXISTING KRITA 1.5 INSTALLATION - uninstall the original first then start from scratch.

Install the following using the dpkg -i <package name> command in the terminal.

From the lcms directory:

liblcms1_1.05-1_your machine type (in my case i386)
liblcms1_dev_1.15-1_your machine type
liblcms_utils_1.15-1_your machine type

From the main directory:

koffice_dbg_1.6.0-0ubuntu1~dapper1_your machine type
koshell_1.6.0-0ubuntu1~dapper1_your machine type
koffice_data_1.6.0-0ubuntu~dapper1_all
koffice_libs_1.6.0-0ubuntu~dapper1_your machine type
krita_data_1.6.0-0ubuntu~dapper1_all
krita_1.6.0-0ubuntu~dapper1_your machine type

This *should* sort out the problem. Apologies for the confusion, I'm a relative newbie on Linux and as for all: I'm learning new stuff all the time.

Of course - if you want to use ALL of Koffice then you have to install all the relavant files for your machine from the URL in my previous message. ](*,)

---

