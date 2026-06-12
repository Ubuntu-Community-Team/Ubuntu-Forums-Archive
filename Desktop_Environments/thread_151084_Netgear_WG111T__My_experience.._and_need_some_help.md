---
title: "Netgear WG111T : My experience.. and need some help.."
date: 2006-03-27
forum: Desktop Environments
---

### Post by Kennyt on 2006-03-27
First of all I must say I'm not really good in Linux.

Then I must say I did make a lot of search concerning this issue and they were not kind of helpful. (On my windows partition, got access to internet)

What I had to do in order to make Ubuntu start my WG111t:

1. Download and install gcc-3.4 (Because the new ndiswrapper needed that)
2. Install ndiswrapper1.10 -> and the .inf files 

Now I can see the wlan0 after typing iwconfig...

1 thing done... next thing... wpa...



Now this is giving me a really big headache...
I've downloaded the wpasupplicant (.deb)
Tired to install it and I tells me I'm missing openssl, so I go in the synaptic package thingy and install openssl, no go.

Go and download the newer version of openssl with the libssl etc (libssl0.9.8 i think) and got it installed.

Back to trying to make and install the wpasupplicant..

Now I get something else... says I need libreadline5.1 at least and 5.0 something is installed...

I go on the net and go download libreadline5.1, and now what do I get?

libpsock8 depends on libreadline4 >= 4.3-1.....
and to install libreadline5.1, version 4 have to be removed..

And here I am STUCK, at this point, trying to install that WPA_supplicant..

and this is really starting to P*** me off.


Could someone help me install wpasupplicant.

---

