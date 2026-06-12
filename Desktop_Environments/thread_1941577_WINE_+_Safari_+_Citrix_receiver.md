---
title: "WINE + Safari + Citrix receiver"
date: 2012-03-15
forum: Desktop Environments
---

### Post by le_jawa on 2012-03-15
I have no idea if anyone has tried this before or not, but here goes...

I've got a friend for whom I setup a Linux system a few years ago and she's been thrilled with it, but now her work has a new Citrix Access Gateway, and they say that it only works with IE.  However,  someone has said that it works with Safari also.  To see if we could make that work, I installed Safari (using WineTricks) then installed the Windows version of the Citrix Receiver (11.0 or 11.1).  Safari doesn't seem to recognize the plugin at all.  When I get to the point of actually running an app, I Safari says it doesn't recognize the ICA file.

Does anyone know what I need to do to get Safari working with the Citrix Receiver in this environment?

Thank you,

Jason

---

### Post by americanLoki on 2012-03-16
Have you tried using the native Linux Citrix Receiver? In my last job we used Citrix and although I was told "it only works in IE" I was able to use the native Citrix client with no issues in Firefox. Does the site not even load in Firefox? If so you may be able to spoof the browser ID string so it shows up as IE.

---

### Post by BHEJU on 2012-03-16
I run 64 bit ubuntu and run citrix apps which are built for WIN platform. 
I THINK that as long as you have citrix client running, it doesn't matter what os or borwser you run.
Now, last I checked, there was no 64 bit version of citrix client for linux. so I had to install some libraries for 32 bit and and install 32 bit citrix online plug-in. It worked.

So, I suggest you install the citrix client on ubuntu and try to access the app.

Cheers,

---

